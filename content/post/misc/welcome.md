---
title: "Welcome"
date: 2020-02-05T13:57:04+09:00
Categories: ["Misc"]
Description: "当サイトへのお試し投稿です。markdownの記法が有効かどうかの確認を兼ねて、色々試しています。"
Tags: ["note"]
draft: false
---

# はじめに

この投稿はお試し投稿です。

# なにするサイト？

このサイトでは、プログラミング言語や電子工作など日頃行っている作業のメモを纏め公開していく予定です。
加えてそれに日々の雑多な疑問などTwitterに収まりきらないようなものもダラダラと投下します。

このカテゴリー(Misc)とタグ(note)はダラダラ系なので、programmingやelectric_kitあたりを中心に見て回っていただければと思います。

# お試し
それでは早速Markdown記法でいくつかお試しです。
Markdown記法、実際の表示の順に並べていきます。

## 見出し

```markdown
# 見出し1
## 見出し2
### 見出し3
#### 見出し4
##### 見出し5
###### 見出し6
```

# 見出し1
## 見出し2
### 見出し3
#### 見出し4
##### 見出し5
###### 見出し6


## 箇条書きリスト

### markdown
```markdown
- リスト1
    - ネスト リスト1_1
        - ネスト リスト1_1_1
        - ネスト リスト1_1_2
    - ネスト リスト1_2
- リスト2
- リスト3
```
### 実例
- リスト1
    - ネスト リスト1_1
        - ネスト リスト1_1_1
        - ネスト リスト1_1_2
    - ネスト リスト1_2
- リスト2
- リスト3

## 番号つきリスト

### markdown
```markdown
1. 番号付きリスト1
    1. 番号付きリスト1_1
    1. 番号付きリスト1_2
1. 番号付きリスト2
1. 番号付きリスト3
```
### 実例
1. 番号付きリスト1
    1. 番号付きリスト1_1
    1. 番号付きリスト1_2
1. 番号付きリスト2
1. 番号付きリスト3


## 引用
### markdown
```markdown
> お世話になります、xxxです。
> 
> ご連絡頂きありがとうございます。
```
### 実例
> お世話になります、xxxです。
> 
> ご連絡頂きありがとうございます。

## 二重引用

### markdown
~~~
> お世話になります、xxxです。
> 
> ご連絡頂きありがとうございます。
>> こんにちは、yyyです。
>> 
>> 明日の予定につきましてご連絡致します。
~~~

### 実例
> お世話になります、xxxです。
> 
> ご連絡頂きありがとうございます。
>> こんにちは、yyyです。
>> 
>> あの新機能バグってるっすね

## pre記法(スペース4 または タブ)

### markdown
```markdown
    class aaa
        def bbb
            print 'ccc'
        end
    end

```
### 実例
    class aaa
        def bbb
            print 'ccc'
        end
    end


## コード

### markdown
```markdown
お試しコードはこちらです: `cd; mkdir git; mkdir my_project; git init`
```
### 実例
お試しコードはこちらです: `cd; mkdir git; mkdir my_project; git init`



## 強調 em
### markdown
```markdown
normal *italic* normal
normal _italic_ normal
```

### 実例
normal *italic* normal
normal _italic_ normal


## 強調 strong
### markdown
```markdown
normal **bold** normal
normal __bold__ normal
```
### 実例
normal **bold** normal
normal __bold__ normal

## 水平線
### markdown
```markdown***
---
___
* * * 
```

### 実例
***
---
___
* * * 

## リンク
### markdown
```markdown
[Google](https://www.google.co.jp/)

```
### 実例
[Google](https://www.google.co.jp/)


## 取り消し線
### markdown
```markdown
~~取り消し線~~
```
### 実例
~~取り消し線~~


## pre記法のシンタックスハイライト
### markdown
~~~
```python
def make_sense():
    return "なるほどね！"

print(make_sense())
```
~~~
### 実例
```python
def make_sense():
    return "なるほどね！"

print(make_sense())
```
