---
title: "Hugoで作成したサイトを追加構成"
date: 2020-02-10T23:11:57+09:00
Categories: ["Web"]
Tags: ["Hugo", "静的サイトジェネレータ", "config"]
Description: "Hugoで作成したサイトの追加構成"
draft: false
---

# はじめに

前回は[静的サイトジェネレータ Hugoをインストール](/web/hugo001/)で、静的サイトジェネレータのひとつであるHugoをインストールしました。
今回はそのサイトに記事を増やす方向の充実ではなく、**機能や構成**を充実させていく方向でのメモをです。

この記事は、順次追記されて充実していきます。(つまり、最初は1つ、2つしかトピックがありません)

# Hugoで作成したサイトに追加の構成を行う

<!-- ==================================================================================================== -->
## sitemap.xml
Googleさんをはじめ各種サーチエンジンに正しく認識してもらうためにも、sitemap.xmlがあった方がいいですね。
Hugoは自動的にsitemap.xmlが生成されています。

ただ、カテゴリーやタグのページはページ自体をコンテンツとして見たときに纏まっているわけではなく、あくまで集合体、リンク集に過ぎません。
そのため、すべてをsitemap.xmlに載せたくない。そんなときに、sitemap.xmlは自動生成させるも、いいさじ加減にするための方法がこちらです。

これがGoogle先生に気に入られるという話ではありません。こうやったら出来るんですよ。この作りを覚えておきましょうねというものです。

### 設定方法

layoutsディレクトリ配下に以下のsitemap.xmlファイルを配置するだけです。

```xml
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
{{ range .Data.Pages }}
    {{ if .IsPage }}
        <url>
        <loc>{{ .Permalink }}</loc>
        {{ if not .Lastmod.IsZero }}
            <lastmod>{{ safeHTML ( .Lastmod.Format "2006-01-02T15:04:05-07:00" ) }}</lastmod>
        {{ end }}
        </url>
    {{ end }}
{{ end }}
</urlset>
```

雑でも説明はあった方が良いかと思いますので致しますと、ページある分だけループを回してそのページがコンテンツのページだったら
sitemap.xmlに載るようにし、最終更新日時がとれなかったらそれは出さないようになっています。

ま、このサイトではGoは知らぬ存ぜぬの立場で書いていますので、この要件で良ければこのままコピペで良いと思います。

### 確認
[http://localhost:1313/sitemap.xml](http://localhost:1313/sitemap.xml)にアクセスして下さい。

もちろんこれは、[前回](/web/hugo001/)も記載しましたが`hugo server -w`を実行している前提です。

![sitemap.xmlの確認](/assets/2020-02-11-00-00-56.png)


<!-- ==================================================================================================== -->
## GoogleAnalytics

GoogleAnalyticsとの連携は、拍子抜けするほど簡単です。

### 設定方法
config.tomlに以下を設定するだけです。

```toml
# Google Analytics
googleAnalytics = "UA-xxxxx-xx"
```

### 確認
これに関しては、確認を割愛します。 


<!-- ==================================================================================================== -->
## Favicon.ico

**Favicon.ico**ってなんだ？って方がもしもいらっしゃった場合に、その話をスルーしてしまうと悲しいことになってしまうので、
念のためにいたしますと、ブラウザを開くとタブの左端に着いているアイコン、それからブックマークしたときなどにも使われているアイコンです。

![faviconサンプル](/assets/2020-02-10-23-24-23.png)

これはなにも設定していないときの例ですね。


### 設定方法
Hugoで作成したサイトで、favicon.icoを配置したいとおもったら、やることは単純です。
**static**ディレクトリの直下にfavicon.icoをおくだけで設定できます。

### 確認
HugoにFaviconを設定した後の確認です。
![favicon設定確認](/assets/2020-02-10-23-35-12.png)

適当に写真を切り取って使いましたが、やはりアイコンとしてデザインしたモノを用意した方が良いですね。

<!-- ==================================================================================================== -->
## テーマを変更

単なる思いつきですが、このタイミングでテーマを変更してみたいと思います。

選んだのはこちら。
[Techlog Simple](https://themes.gohugo.io/hugo-theme-techlog-simple/)

### 設定方法

ガイドされている方法に逆らってしまいますが、submodueとして加えます。


まずはインストールから。
```cmd
git submodule add https://github.com/mazgi/hugo-theme-techlog-simple.git themes/hugo-theme-techlog-simple
```

続いてテーマを有効にしておきます。
```cmd
hugo -t hugo-theme-techlog-simple
```

たぶん、何個か怒られると思います。
たぶん、次のconfig.tomlファイルの修正で治ると思います。

今ある**conig.toml**ファイルをバックアップして、代わりに[こちら](https://github.com/mazgi/hugo-theme-techlog-simple/blob/master/exampleSite/config.toml)で置き換えます。
その例がこちらです。

```toml

baseURL = "http://memorandum.always-basics.com/"
languageCode = "en-us"
title = "Memorandum - Danger past, got forgotten"
theme = "hugo-theme-techlog-simple"
defaultContentLanguage = "ja"
hasCJKLanguage = true
enableEmoji = true
pygmentsCodeFences = true
pygmentsStyle = "friendly"
enableGitInfo = false
enableRobotsTXT = true

copyright = "©2020 Always Basics."

# Google Analytics
googleAnalytics = "UA-75025058-6"


[params]
description = "継続する秘訣は、途切れたと思った時にもう一度繰り返すこと"

[params.sns]
github = "mazgi"
twitter = "mazgi"
instagram = "mazgi"
# facebook = ""

[taxonomies]
category = "categories"
tag = "tags"
author = "authors"

# [languages]
# [languages.en]
# weight = 1
# languageName = "English"

# [languages.ja]
# weight = 10
# languageName = "日本語"


logo = "/images/logo.jpg"

# disqus
disqusShortname = "kzthrk"  # your short name

```

### 確認
確認といっても単に表示するだけです。
[http://localhost:1313/](http://localhost:1313/)にアクセスして下さい。

![テーマ変更確認](/assets/2020-02-12-01-46-33.png)

無事に変更できていました。


<!-- ==================================================================================================== -->

## TOPページに記事がリストされない

なんだかTOPページに追加したはずの記事がリストされません。ですが、カテゴリーとかタグから辿ると確かに存在します。
どうも、見えているのはWebカテゴリーに投稿した記事のみのようです。

ということで、どんなことになっているのか見てみます。
まずは**themas/hugo-notepadium/layouts/index.html**ですね。

```
{{- define "main" -}}
{{- partial "homepage-body.html" . -}}
{{- $paginator := .Paginate (where site.RegularPages "Type" "in" site.Params.mainSections) -}}
{{- partial "note-list.html" $paginator -}}
{{- partial "pagination.html" $paginator -}}
{{- end -}}
```

えっ!？これ**HTML**なの？状態ですが、気にしません。

```
{{- partial "note-list.html" $paginator -}}
```
をみるとnote-list.htmlとか$paginatorあたりが気になりますが、note-list.htmlを見て見ます。
パスは`themes/hugo-notepadium/layouts/partials/note-list.html`です。

```
・・・
<ul class="note list">
    {{- range $paginator.Pages -}}
    <li class="item"><a class="note" href="{{- .RelPermalink -}}">
・・・
```

抜粋ですが、どうやらここみたいな雰囲気ですね。
つまりは、$paginatorに入っていればループが回って表示されるんじゃないかという推測です。

ふと元のindex.htmlを見ると、

```
{{- $paginator := .Paginate (where site.RegularPages "Type" "in" site.Params.mainSections) -}}
```
という行があります。**site.Params.mainSections**なんてステキなキーワードが見つかりました。

Google先生にお尋ねして探してみると、こんなページがあります。
[https://gohugo.io/functions/where/#mainsections](https://gohugo.io/functions/where/#mainsections)

![スクリーンショット](/assets/2020-02-12-22-08-57.png)

まさにキタコレ。

### 設定

というわけで、config.tomlに**mainSections**を追加してみます。

```toml
[params]
mainSections = ["electronic_kit", "misc", "programming", "web"]

```

### 確認

![メインセクション追加確認](/assets/2020-02-12-22-11-29.png)

無事に出てくるようになりました！

<!-- ==================================================================================================== -->

<!-- ==================================================================================================== -->




以上

