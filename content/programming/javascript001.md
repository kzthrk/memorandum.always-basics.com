---
title: "JavaScriptでループの同期処理"
date: 2020-02-06T13:57:04+09:00
Categories: ["Programming"]
Description: "JavaScriptでループの同期処理"
Tags: ["JavaScript", "同期"]
draft: true
---

# はじめに

JavaScriptを使い慣れていないと、
非同期処理をループで回して、終わりを待ちたい



複数行で言うと
題材は何でも良いのですが、ここではデータベースのTable_A, Table_B, Table_Cのレコード数を取り出し、その和(10+20+30=60)を求めたいとします。

let sum = 0
for (const label in ["A", "B", "C"]) {

    sum += select count(*)してくれる関数("Table_" + label)

}
console.log(sum)
この例はおそらくsumが0として残念な結果になると思います。 で、この記事を読む動機を持った方は、大げさに言うと下のようなことになりたくないといった感じでしょうか。

count("Table_A").then(result => {
    sum += result
    count("Table_B").then(result => {
        sum += result
        count("Table_C").then(result => {
            sum += result
            console.log(sum)
        }
    }
}
ここまでひどくは無くても、then.then.then　と君の名は。状態は避けたいと。そして、ループで処理したいよねと。 それをここでは扱います。

なので
ここまででお分かりの方には「同期処理」や「同期実行」という話題は扱わないというのがお分かりかと思いますが 私含めて、この「やりたいこと」を考えているときには、自分の考えていることと検索キーワードの不一致に気がついて いなかったので、あえてこう書きました。

実食
使うのはPrpmise.all()です。

これまで「なにそれおいしいの？」と思っていた方、「なんだかよくわかんねーな」と思っていた方、意味分からなくてもこのひな形をコピペすれば、一応終了待ちは出来ますので是非。

意味分からなくてもスイッチ押せばエンジンはかかるんですよ。え、なに？お宅のはモーターだって？大丈夫、ちゃんとエンジンブレーキもききますって。ま、あとは、勉強するなり、実験するなり、意味が分からないまま使い続けるなり、お好きにすれば良いと思います。でもボタン押さないのはもったいない。

Promise.all()
ここでは、DBアクセスの代わりにsetTimeout()を使っています。

let sum = 0

const test = function(param) {
  return new Promise( function(resolve, reject) {
    setTimeout(function(){
      sum += param
      resolve(sum)
    }, param*1000)
  })
}

const promises = []
promises.push(test(3))
promises.push(test(5))

Promise.all(promises).then(function(result) {
  console.log("result: " + JSON.stringify(result))
  console.log("sum: " + sum)
}).catch(err => {
  console.log("err: " + JSON.stringify(err))
})
console.log("sum: " + sum)
これで無事に、合計値が得られます

sum: 0
result: [3,8]
sum: 8
やりたいことをsetTimeout()の箇所に記載すればいいわけです。

補足
Promise.all()は処理の合流
Promise.all()は同期的に実行しているわけではありません。あくまで終了待ち、処理を合流させるために使うものです。 そして、それは指定した処理だけの話です。次のコードを実行すればそれが分かります。

console.log("begin")
let sum = 0

const test = function(param) {
  console.log("2 " + param + "秒")
  return new Promise( function(resolve, reject) {
    console.log("3")
    setTimeout(function(){
      console.log("5 " + param + "秒待ち")
      sum += param
      resolve(sum)
    }, param*1000)
    console.log("4")
  })
}

console.log("1")
const promises = []
promises.push(test(3))
console.log("6.1: sum: " + sum)
promises.push(test(5))

setTimeout(function() {
  console.log("6.2: sum: " + sum)
}, 6000)

setTimeout(function() {

  console.log("7")
  Promise.all(promises).then(function(result) {
    console.log("8.1: result: " + JSON.stringify(result))
    console.log("8.1: sum: " + sum)
  }).catch(err => {
    console.log("8.2: err: " + JSON.stringify(err))
  })
}, 7000)

console.log("end")
結果

begin
1
2 3秒
3
4
6.1: sum: 0
2 5秒
3
4
end
5 3秒待ち
5 5秒待ち
6.2: sum: 8
7
8.1: result: [3,8]
8.1: sum: 8
考えてみれば当たり前ですが、二つの処理はpromisesにpush()された行で動き始めるので、5.x秒後には終わっているはずです。 なので、6秒後に結果を確認すると結果は出そろっています。このコードでは「合流して確認」という作業を7秒後に発動させているだけです。 Primise.all()を使うと、この5.x秒とかを意識せずに、すでに終わっていようが終わっていまいが、合流後の処理を記載できるということに過ぎません。 そして、このPromise.all()を囲っているsetTimeout()を外すと次の結果となり、Promise.all()自体も非同期処理としてその先に進んでしまっているので、ここで全体が待ってくれているわけではありません。

begin
1
2 3秒
3
4
6.1: sum: 0
2 5秒
3
4
7
end
5 3秒待ち
5 5秒待ち
8.1: result: [3,8]
8.1: sum: 8
6.2: sum: 8
JavaやC++の類いでもスレッドの扱いで面倒があったかと思いますが。ただ世界をひっくり返しただけなので別に楽も苦労もしていません。隣の芝、青かった？使用人の皆さん、よくおっしゃるんですよねー。

