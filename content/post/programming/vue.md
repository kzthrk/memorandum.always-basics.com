---
title: "初めてのVue.js"
date: 2020-05-05T16:12:05+09:00
lastmod: 2020-05-05T16:12:05+09:00
Categories: ["Programming"]
Tags: ["JavaScript", "Vue.js"]
Description: "はじめてのVue.js。前提はJavaScriptがなんとなく分かる程度ですので、文字取り本当に一から取り組みます。3部構成になっており、2つ目まで実施すれば後は独学の道もよしです。"
imgs: []
readingTime: true  # show reading time after article date
toc: true
comments: false
justify: false  # text-align: justify;
single: false  # display as a single page, hide navigation on bottom, like as about page.
license: ""  # CC License
draft: false
---

# はじめに

初めてのVue.jsということで、本当にいちからはじめてみたいと思います。

前提となる基礎知識は、JavaScriptがなんとなく分かる程度です。

私自身はJavaScriptができるとは到底言えないレベルですが、なんとなく読めてなんとなくかけます。(仕事をする上で一番たちの悪いパターンですね) node.jsやnpmコマンドも使ったことがありますし、他のフレームワークの経験もあります。

そのため、以下のような開発スタイルをなんとか自力でとれるレベルです。

* node.jsを複数インストールし切り替え可能な環境を構築し、
* npmコマンドを使ってパッケージ管理をして
* フレームワークの標準に沿ったソースファイルを編集することでプログラミングをし
* webpackを使ってビルドをして
* node.jsでAPIを提供するアプリに組み込んで、

SPA(Single Page Application)と呼ばれるWebのシステムを1つ動かすことができます。

さて、出発点を挙げるとするならば、やはりオフィシャルサイトの以下です。
https://jp.vuejs.org/v2/guide/installation.html

誰も否定する人はいないと思いますが、如何せん分かりやすいとは言えません。

例えばインストール手順ですが、`HTML内でCDNを指せばいい`と言ったかと思えば、`npm install vue`などと言い放ったりします。

当然これらは同値ではありません。全然次元が違うじゃんと。

CDNは指せば動きますが、npmでインストールしてもそれだけではなにも動作しないわけです。CLIを使ったインストール方法も紹介されていますが、CLIでのインストールでは裏でこのnpmでインストールが実行されているのであって、はっきり言ってなんのこっちゃ？です。

そっちがその気ならこっちも言わせてもらいますと

「てめーが書きたいことを書いて満足してるんじゃねーぞ」

ってなもんです。

# コンテンツ

さて当サイトのコンテンツは、次のような構成となります。

1. [HTMLとJavaScriptの単純構成で初めのVue.js](/programming/vue1/)
2. [npmでパッケージ管理して、webpackでビルドする](/programming/vue2/)
3. [Vue.jsでアプリ開発](/programming/vue3/)

『1.HTMLとJavaScirptの単純構成で初めてのVue.js』では、index.htmlとindex.jsの2ファイルだけでVue.jsを体験します。実際の所、この2つだけで最後まで開発しきることは無理ではないと思います。したがって、とにかく試して試して試すだけという人は、このまま突き進んでも良いかと思います。

続いて『2.npmでパッケージ管理して、webpackでビルドする』では、『1.HTMLとJavaScirptの単純構成で初めてのVue.js』のindex.htmlとindex.jsをゴールに定めて、開発環境を整える手順を紹介します。

具体的には、

1. 複数バージョンを切り替え可能なようにNode.jsをインストール
2. npmでBabelとWebPackをインストール
3. WebPackを構成して、ビルド

の流れでご紹介します。

読者の前提をJavaScrptがなんとなく分かる程度という風に設定していますので、
Node.jsやnpmで寄り道し、BabelやWebPackについても取り上げます。

最後に『3.Vue.jsでアプリ開発』ですが、ここではVue.jsでアプリ開発する上で必要となる要素を一通り試していきたいと思います。もちろん『1.HTMLとJavaScirptの単純構成で初めてのVue.js』から直接ここへ来て試すだけ試すというのも可能です。

それでは早速ですが、[1. HTMLとJavaScriptの単純構成で初めのVue.js](/programming/vue1/)へどうぞ。
