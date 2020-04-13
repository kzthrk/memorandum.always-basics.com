---
title: "macOS 便利な使い方"
date: 2020-04-13T21:43:54+09:00
lastmod: 2020-04-13T21:43:54+09:00
Categories: ["Misc"]
Tags: ["Mac"]
Description: "Macの便利な使い方"
imgs: []
cover: ""  # image show on top
readingTime: true  # show reading time after article date
toc: true
comments: false
justify: false  # text-align: justify;
single: false  # display as a single page, hide navigation on bottom, like as about page.
license: ""  # CC License
draft: false
---

# はじめに

本稿では、Macでこんな設定こんな使い方すると便利だよ！というのを紹介していきます。
最初投稿では1つしかない状態で、都度追加していく方式です。

## お品書き

1. どこでも(フォルダ指定)で、VSCodeを開く



## どこでも(フォルダ指定で)VS Codeを開く

### 前書き
iTermを使われている方は、Finderを使っていてどこでもiTermが開けると思います。(設定次第だったかも知れませんが、とにかく可能です。)
VSCodeやAtomを使われている方は、ターミナル内でコマンドを実行することでそれぞれ起動可能なことと思います。

こんな感じでVSCodeを呼び出すことで、フォルダを開いた状態で起動します。

```
MacBookPro ~ $ code .
```
長らくこの方法で使っていたのですが、やはり都度ターミナルが増えちゃう(閉じなければならない。Command+w)というのは少しイケてません。

これをFinderのポップアップメニューから直接指定して起動できればどうでしょう。それを実現するモノです。

### 設定方法

私はこのやり方でVSCodeを開けるようにしていますが、他のアプリでもやり方は同じです。

まずは、automator.appを起動します。

![automator.app](../assets/2020-04-13-21-44-47.png)

**クイックアクション**をクリックし、**選択**ボタンをクリックします。
![](../assets/2020-04-13-21-59-18.png)

**ファイルとフォルダ**をクリック、**Finder項目を開く**を右側のペインへドラッグします。

![](../assets/2020-04-13-22-16-22.png)

アプリケーションを選択します。VSCodeの場合は、**その他**をクリックします。

![](../assets/2020-04-13-22-17-54.png)

**Visual Studio Code,app**を選択して、**選択**をクリックします。

![](../assets/2020-04-13-22-19-44.png)

あとはファイル→保存…で**名前**を付けて保存します。

![](../assets/2020-04-13-22-23-00.png)

automator.appは終了して構いません。

Finderを開いて、フォルダを右クリックして、付けた名前(ここではVSCodeで開く)をクリックしてください。

![](..//assets/2020-04-13-22-30-49.png)

無事に動作しましたでしょうか。

今回の場合、フォルダでもファイルでも開けます。
もっともファイルの場合には**このアプリケーションで開く**という機能がそもそもあるのでありがたみもありませんが。