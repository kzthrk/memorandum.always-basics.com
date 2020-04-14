---
title: "はじめてのVue.js"
date: 2020-04-14T20:43:19+09:00
lastmod: 2020-04-14T20:43:19+09:00
Categories: ["Programming"]
Description: "はじめてのVue"
Tags: ["JavaScript", "Vue.js"]
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

# 初めてのVue.js

初めてのVue.jsということで、本当にいちからはじめてみたいと思います。

## はじめに

前提となる基礎知識は、JavaScriptがなんとなくという程度です。

私自身はJavaScriptができるとは言い切れず、なんとなく読めてなんとなく書けます。(仕事をする上で一番たちの悪いパターンですね) 
Node.jsやnpmコマンドも使ったことがありますし、他のフレームワークの経験もあります。

そのため、以下のような開発スタイル(環境構築を含む)を自力でなんとかとれるレベルです。
	- node.jsを複数インストールし切り替え可能な環境を構築し、
	- npmコマンドを使ってパッケージ管理をして
	- フレームワークの標準に沿ったソースファイルを編集することでプログラミングをし
	- webpackを使ってビルドをして
	- Node.jsでAPIを提供するアプリに組み込んで、
SPA(Single Page Application)と呼ばれるWebのシステムを開発、運用することができます。

さて、まず正規の出発点なら以下です。
[https://jp.vuejs.org/v2/guide/installation.html](https://jp.vuejs.org/v2/guide/installation.html)

誰も否定する人はいないと思いますが、如何せん分かりやすいとは言えません。(個人的な意見)

例えばインストールですが、CDNをHTML内で指せばいいと言ったかと思えば、
`npm install vue`などと言い放ったりします。

全然次元が違うじゃんと。

『npm install vue』と釣り合う作業は、『CDNのサイトにファイルをアップロードしてWebサーバーで公開する』ですよ!

つまりCDNは指せば動きますが、npmでインストールしてもそれだけではなにも動作しないわけです。
もっと言えば別の方法としてCLIでのインストールも提示されていますが、それって裏で`npm install vue`が実行されてますよね?

そっちがその気ならこっちも言わせてもらいますと **「書きたいことを書いて満足してるんじゃねーぞ」**ってなもんです。

## コンテンツ

さて文句ばっかり言っていても仕方ないので、先人の知恵を借りつつ、自分なりに解釈して進めていくわけですが、、、

当サイトのコンテンツは、次のような構成となります。

1. [HTMLとJavaScriptの単純構成ではじめてのVue.js](/programming/vue01/)
2. [npmでパッケージ管理して、webpackでビルドする](/programming/vue02/)
3. [Vue.jsでアプリ開発](/programming/vue03/)

『1.HTMLとJavaScirptの単純構成ではじめてのVue.js』では、index.htmlとindex.jsの2ファイルだけでVue.jsを体験します。

実際の所、この2つだけで最後まで開発しきることは無理ではないとですが、まだ始めたばかりの人間から見ても、多分ですがずいぶん奇特な人だと思います。
とにかく試して試して試すだけという人は、このまま2つのファイルのままで突き進んでも良いかと思います。

続いて『2.npmでパッケージ管理して、webpackでビルドする』では、開発するアプリは『1.HTMLとJavaScirptの単純構成ではじめてのVue.js』と同じです。

複数のファイルに分割してコーディングし、コマンドを実行するとアプリができあがるという開発環境を整える手順を紹介します。

具体的には、

1. 複数バージョンを切り替え可能なようにNode.jsをインストール
2. npmでBabelとWebPackをインストール
3. WebPackを構成して、ビルド

の流れでご紹介します。

読者の前提をJavaScrptがなんとなく分かる程度という風に設定していますので、Node.jsやnpmで寄り道し、BabelやWebPackについても取り上げます。

最後に『3.Vue.jsでアプリ開発』です。ここではVue.jsでアプリ開発する上で必要となる要素を一通り試していきたいと思います。
もちろん『1.HTMLとJavaScirptの単純構成ではじめてのVue.js』から直接ここへ来て試すだけ試すというのも可能です。

それでは、[1.HTMLとJavaScirptの単純構成で初めてのVue.js](/programming/vue01/)からお付き合いください。

