---
title: "Theia | Theiaを始めてみよう"
date: 2020-04-10T23:25:55+09:00
lastmod: 2020-04-10T23:25:55+09:00
Categories: ['Theia']
Tags: ['IDE', 'Development']
Description: "Cloud & Desktop IDE Platform"
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
## Theiaとは
まずは読み方ですが『[テイア](https://ja.wikipedia.org/wiki/%E3%83%86%E3%82%A4%E3%82%A2_(%E4%BB%AE%E8%AA%AC%E4%B8%8A%E3%81%AE%E5%A4%A9%E4%BD%93))』と読むようです。

Theiaとは[公式ページ](https://theia-ide.org/)の説明を借りれば

> Eclipse Theia is an extensible platform to develop multi-language Cloud & Desktop IDEs with state-of-the-art web technologies.


Eclipse Theiaは、最先端のWebテクノロジーを使用して多言語のクラウドおよびデスクトップIDEを開発するための拡張可能なプラットフォームです。

### だからなに？

我々一般ユーザーにとって見れば、このスクリーンショットのような開発環境が提供されるってことです。

![ScreenShot](../assets/2020-04-10-23-54-22.png)

### つまりは？

こちらの記事で紹介されていますが、デスクトップ版とブラウザ版が想定されていて、どちらでも同じソースコードで開発環境が提供されることになります。

[Visual Studio Codeの代替を狙う統合開発環境「Eclipse Theia 1.0」リリース。VS Codeの拡張機能を利用可能、デスクトップ版とWebブラウザ版に両対応](
https://www.publickey1.jp/blog/20/visual_studio_codeeclipse_theia_10vs_codeweb.html
)

> Eclipse Theiaは、「真のオープンソースによるVisual Studio Codeの代替」（a true open source alternative to Microsoft’s popular Visual Studio Code (VS Code) software）だとEclipse Foundationは紹介しており、デスクトップアプリケーションだけでなくWebブラウザからも同一機能が利用できるWebアプリケーション版も提供されています。


### Theiaとは？

仕切り直しますね。**Theia** とはVS Code(Vidual Studio Code)そっくりなんですが、それがブラウザの中で(も)動きます。先に書いた通りデスクトップ版もありますが、デスクトップ版というのはElectronでパッケージングしたものになるので、それってそのまんまVS Codeじゃんってことですね。

*脱線: ElectronとはNode.jsのアプリ(サーバーサイド)とChromium(ブラウザ)を一塊にすることでデスクトップ・アプリケーションにするフレームワークです。*

この投稿を読んでいる方がVS Codeを聞いたことがないとは思えないですが、念のため簡単に触れておくと、Microsoftが開発しているElectronベースのソースコードエディタです。
ソースコードエディタって微妙な表現ですが、MicrosoftはVisual Studioという統合開発環境をもっていてそのエディタ部分だけを切り出したというイメージなので、VS Code自身はソースコードエディタという説明に。
ただご承知の通り、だれもソースコードエディタとしての使用にとどまっている人はおらず、豊富な拡張機能を **拡張機能(プラグイン)** をガシガシインストールして統合開発環境として使用している訳です。

一方で、TheiaはEclipseが開発しているので別物ではあります。ですが、TheiaはVS Codeそっくりなだけでなく **VS Codeの拡張機能(プラグイン)** が使えます。いよいよヤバイ感じですね。
はっきり言って、第一印象は丸パクリ状態です。



## Theiaを使ってみる

### マニュアル

Theiaについてのドキュメントは[こちら](https://theia-ide.org/docs/)ですが、このあと使う**Gitpod**については[こちら](https://www.gitpod.io/docs/)を参照してください。

ひとまず読むのは後者の方が多かった印象です。

### Gitpodで使ってみる

まず真っ先に試してみるべきは、ブラウザで動作するこちらです。
[公式ページ](https://theia-ide.org/)の**Try in Gitpod**を利用します。

![Try in Gitpod](../assets/2020-04-11-00-22-21.png)

Gitpodへ移動すると、 **Login with Github & Launch Workspace** をクリックします。

![Gitpod](../assets/2020-04-11-00-49-55.png)

Githubのアカウントで認証します。

![Sign in to Github](../assets/2020-04-11-00-51-39.png)

拡張機能のインストールの案内が出てくるはずです。 **Get Chrome Extension** をクリックします。

![拡張機能](../assets/2020-04-11-00-58-05.png)

すでにインストールしてしまった状態で画面をキャプチャしたので、ボタンが削除になっているのは許してください。

![機能拡張のインストール](../assets/2020-04-11-00-59-47.png)

そして、いよいよ...いよいよ...　ええ、Dockerですのでしばらくお待ちください。
こんな状態になっていると思います。

![theia](../assets/2020-04-11-01-10-33.png)

これが、GitpodによるTheiaです。
Theia自身の開発をしたい人はこのままで良いかと思いますが、多分そんな人はほとんどいないと思いますので一旦閉じます。

右上のアイコンをクリックするとメニューが表示されるので、 **Stop Workspace** をクリックします。

![Menu](../assets/2020-04-11-01-22-20.png)

**Workspaces** をクリックします。

![Dialog](../assets/2020-04-11-01-23-35.png)

ワークスペースのリストが表示されていることと思います。

![WorkspaceList](../assets/2020-04-11-01-34-07.png)

この画面は何度か訪れることになりますが、今は自分の環境を手に入れることが目的なので、一旦放置します。
Githubの自分のリポジトリにブラウザでアクセスします。

**Gitpod** ボタンがあるはずなのでクリックしてください。

![Github](../assets/2020-04-11-01-38-44.png)

これで自分自身は、 **拡張機能** を導入していないですが、VS Codeでプロジェクトを開いた相当の環境が手に入りました。

![Theia](../assets/2020-04-11-01-51-04.png)

### 拡張機能をインストールしてみる

さて、先ほどから何度となくVS Codeの拡張が使えると言ってきました。
いくつかの拡張がすでにインストールされているようですが、やはり自分のお好みのものをインストールしたいと思うでしょう。

ですが、拡張機能をインストールしようとしてみても、検索なんて出来ません。

![拡張機能](../assets/2020-04-11-02-01-26.png)

これは、VS Codeの拡張機能には制限があるためです。正確には拡張自身ではなくてそのカタログ表示の部分です。

Microsoftは、Visual Studio Marketplaceを他のソフトウェアによって直接使用することを禁止しているのです。
拡張機能事態はそのほとんどがオープンソースで、Microsoftが開発したり保守したりしていませんが、[マーケットプレイス](https://marketplace.visualstudio.com/vscode)へのアクセスは制限されています。

ということで、[マーケットプレイス](https://marketplace.visualstudio.com/vscode)にアクセスして、直接ファイルを手に入れてTheiaにインストールするという流れを取ります。
また多くの拡張がGithubを利用しているのでそちらで手に入れても構いません。

早速ですが[vscode-icons](https://marketplace.visualstudio.com/items?itemName=vscode-icons-team.vscode-icons)を例にインストールしてみたいと思います。

vsixファイルをダウンロードするためのリンクが用意されていますので、それをクリックします。

![DownloadExtension](../assets/2020-04-11-02-41-49.png)

手元にダウンロードしたファイルを、TheiaにDrag & Dropするとインストールできます。
(っていうか、リンク教えたらそっちで勝手にやってよって感じですが・・・)

![Install](../assets/2020-04-11-02-43-08.png)

右下にダイアログが表示されるので、有効化をクリックします。

![有効化](../assets/2020-04-11-02-41-15.png)

この例だとインストール前とそれほど変わってませんが、一応有効になったようです。

![icon](../assets/2020-04-11-02-45-45.png)

ただ、色々試してみて分かったのですが、全部が全部手放しで喜べるほど甘くはなさそうです。

たとえばこの記事は、Markdownで書き殴っているのですが、スクリーンショットは[Paste Image](https://marketplace.visualstudio.com/items?itemName=mushan.vscode-paste-image)を使ってベタペタ貼り付けています。

ですが、これをTheiaにインストールしてみたらxclipコマンドが必要だと言われました。
Dockerfileを作ってインストールしてみたら、今度は「There is not a image in clipboard.」と言われました。
そうですね、そっちからだと思います。

ということで、課題のありそうなもの、動かないモノなどがありそうです。

### Gitpod環境のセットアップ

Docker含め環境の設定方法は[こちら](/theia/docker_settings/)に纏めました


### 今更ですが、無料なのか？

今更ですが、これタダなの？と。

[Gitpod](https://www.gitpod.io/pricing/)にお値段表があります。
ここまでの手順で来た方は、50時間までは無料という形でFreeアカウントになっているはずです。

個人でお金払ってまでブラウザ越しに開発したいかというと微妙な気がしますが、とにかくそういうことです。

日頃忙しく働いている傍ら、隙間時間を使って開発を進めている人とかであれば、日々の隙間時間や移動中、出張中とかで個人用のPCがなくても、ブラウザさえ手に入れば開発が継続できるというのはありがたいのかも知れません。

ひとつ注意事項としては、止めるの忘れて放置しても適当なところでタイムアウトはしてくれるのですが、それでも50時間の1割、2割は浪費する構図になりますので、ご利用は計画的にということで。

## Theiaを使ってみる その2

Electron版つまりは、デスクトップ版はについては、また改めて記載したいと思います。
