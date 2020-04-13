---
title: "Theia | Gitpodの環境設定"
date: 2020-04-12T09:24:50+09:00
lastmod: 2020-04-12T09:24:50+09:00
Categories: ['Theia']
Tags: ['IDE', 'Development']
Description: "Docker settings of Gitpod"
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

# Gitpodの環境設定

## はじめに

本稿は、[Theia | Theiaを始めてみよう](http://localhost:1313/theia/theia/)の中でGitpodおよびその中で使用されるDockerの設定について切り出したものです。

## Github権限設定

作業に入る前にGithubでのGitpodの権限を変更します。すでに行われている場合は不要ですが、当サイトの流れでここまできた場合には行われていないはずです。

右上のアイコンをクリックしてメニューを表示して、**Open Access Control**をクリックします。

![](../assets/2020-04-13-14-22-40.png)

**write public repos**にチェックを入れて、**Update**をクリックします。

![](../assets/2020-04-13-14-23-28.png)

これで、設定作業の中で行うブランチの作成やコミット作業が可能になります。

## 環境設定

設定がまだ済んでいない場合、右下にGitpodの設定が出来るますよと小さなウインドウが出ているかと思います。
もちろん出ていなくても、この記事にあるように2つのファイルを作成することで設定することは可能です。
本稿では、敷かれたレールの上を走る形で設定したいと思います。

![設定用メニュー呼び出し](../assets/2020-04-13-00-47-24.png)

赤枠で囲ったところが、表示されました。ついでに右側のバーにも1つアイコンが増えています。
設定が終わると消えてしまうようですが、それまでは表示されているようですので、もし何らかの操作によって閉じてしまった場合には、ここから再度呼び出してください。

まずは、一番上の**Create .gitpod.yml**をクリックします。

![設定メニュー](../assets/2020-04-13-01-07-51.png)

**Create .gitpod.yml**ボタンをクリックします。

![](../assets/2020-04-13-01-01-51.png)

**update .gitpod.Dockerfile**ボタンをクリックします。

![](../assets/2020-04-13-01-05-29.png)

ベースとするイメージを選択します。

![](../assets/2020-04-13-01-13-41.png)

.gitpod.Dockerfile を作ります。

![](../assets/2020-04-13-01-22-10.png)

.gitpod.yml には、Dockefileの項目が追加されていると思います。
編集するのは、.gitpod.Dockerfileの方です。

![](../assets/2020-04-13-01-37-46.png)

上記は、xclipをインストールしてみた時の例です。

**Test Drive Configuration**をクリックして、**Push to Branch & Start Workspace**をクリックします。

![](../assets/2020-04-13-01-41-27.png)


直接保管した上で再起動しても問題無いのですが、間違っていたとき、想定している結果が得られなかったときに少し面倒です。
そのため、マニュアルにも記載がありますが現時点では別ブランチでコミットしておいては、Github側から新しいインスタンスを使い捨てで起動してテストすることが勧められています。

上手く動作することが分かった場合には、そのブランチをマージするようにします。

**Create a pull request**をクリックし、**Open Pull Request View**をクリックします。

![](../assets/2020-04-13-02-02-06.png)

**Publish Changes**をクリックします。

![](../assets/2020-04-13-02-03-07.png)

ブランチをmasterから先ほど作成した**xxxxx/gitpod-setup**を選択します。

![](../assets/2020-04-13-02-03-38.png)


![](../assets/2020-04-13-02-04-06.png)


設定ファイルをコミットします。左のバーでGitのペインを呼び出します。変更対象のファイルをステージングし、コメントを入力してコミットします。

![](../assets/2020-04-13-02-22-30.png)


**push**をクリックしてください。

![](../assets/2020-04-13-02-04-21.png)


Githubにアクセスして、ブランチを先ほどpushしたブランチに切り替えてからGitpodボタンをクリックします。

![](../assets/2020-04-13-02-05-28.png)


Theiaが起動しますが、その時Dockerが初期化されているのが確認できます。

![](../assets/2020-04-13-02-05-43.png)


環境したら環境がセットアップされているはずです。変更を加えた内容に応じて確認してください。

問題が無ければ、これを元のブランチにマージすることでDockerの設定作業は完了です。

その他、**.gitpod.yml**を編集することで、起動した際の動作(例えばサーバーを毎回起動するなども)可能です。
その場合には、以下echo部分を変更してください。

![](../assets/2020-04-13-02-28-55.png)

以上で、Gitpodの環境設定は終了です。