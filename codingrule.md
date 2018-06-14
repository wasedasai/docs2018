---
title: 早稲田祭コーディング規約
author: Written by <a href="https://kuragem.github.io">Kazuki Matsumoto</a>
date: Last Updated on 2018-06-12
---

# 概要
この文書では、早稲田祭運営スタッフのWebサイト制作における、HTMLとCSSのコーディング規約を説明します。

Web広報チームでは複数人でWebサイトを制作することになるので、個人によるコーディングの差異をできるだけ無くし、可読性とメンテナンス性を高めることを目的としています。

# コーディング
本章では、HTML/CSSのコーディング全般における規約を説明します。

## エンコーディング
 - UTF-8
   - 現在、主流のエンコーディングのため。

## インデント
 - スペース2つ

```html
<!-- Good -->
<ul>
  <li><a href="example.html">Example</a></li>
  <li><a href="sitemap.html">Sitemap</a></li>
</ul>
```

```css
/* Good */
ul {
  list-style-type: square;
}
```

## 大文字・小文字
 - タグやID・クラス名、カラーコードの指定には小文字を用いる。キャメルケースの場合を除く。

```html
<!-- Good -->
<img src="example.png" alt="Example">

<!-- Bad -->
<IMG SRC="example.png" ALT="Example">

<!-- camelCase -->
<div class="camelCase"><p>lowerCamelCaseを利用して単語を繋げる。</p></div>
```

```css
/* Good */
.good {
  color: #1375ca;
}

/* Bad */
.bad {
  color: #1375CA;
}
```

## バリデーション
 - バリデータを利用してHTML/CSSの文法を確認する。
  - [HTML Validator: W3C](https://validator.w3.org/)
  - [CSS Validator: W3C](https://jigsaw.w3.org/css-validator/)

## ブラウザの対応

### デスクトップ
 - [日本でのシェア](http://gs.statcounter.com/browser-market-share/desktop/)と、早稲田祭公式サイトの利用者層を考慮して、以下のブラウザでの動作を確かめる。
   - Internet Explorer 11
   - Google Chrome 最新版
   - Microsoft Edge 最新版
   - Mozilla Firefox 最新版
   - Safari 最新版

### スマートフォン
 - スマートフォンについては、チームメンバーの実機で検証する。
   - iOS Safari
   - Android Chrome
   - LINE, Twitterのアプリ内ブラウザ

## ディレクトリ構成（例）
 - index.html
 - access.html
 - sitemap.html
 - example.html
 - assets/
   - images/
     - logo.png
     - top.jpg
   - stylesheets/
     - reset.css
     - design.css
   - scripts/
     - jquery.min.js
     - example.js
 - favicon.ico

# HTML
本章では、HTMLのコーディングにおける規約を説明します。

## HTMLのバージョン
 - HTML5を使用する。
   - HTML 5.1, HTML 5.2については、ブラウザの対応状況を考慮しながら必要に応じて採用する。

## ファイル命名規則
 - HTMLファイルの命名には、英語を用いる。
   - 「施設」についてのページであれば "facilities.html" とし、 "shisetsu.html" といったローマ字による命名は避ける。

## DOCTYPE宣言
 - DOCTYPE宣言は必ず行う。

```html
<!DOCTYPE html>
```

## HTMLの言語
 - ブラウザの翻訳機能の不必要な起動などを避けるため、ページの言語に応じて設定する。

```html
<!-- Good -->
<html lang="ja">
  <!-- Japanese content -->
</html>

<html lang="en">
  <!-- English content -->
</html>
```

## headタグ内の記述
 - まず文字コードを記述し、その後viewportを設定する。その後、titleとdescriptionを加え、Internet Explorerの互換モードを避ける。

```html
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Page title</title>
  <meta name="description" content="A brilliant website.">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
</head>
```

## コンテンツセクショニング要素の利用
 - シンプルな記述のため、可能な限り、[コンテンツセクショニング要素](https://developer.mozilla.org/ja/docs/Web/HTML/Element)を利用する。

```html
<!-- Good -->
<header>
  <h1>Title</h1>
</header>
<nav>
  <ul>
    <li><a href="index.html">Home</a></li>
    <li><a href="sitemap.html">Sitemap</a></li>
  </ul>
</nav>
<section>
  <h2>News</h2>
  <ul>
    <li>Good news.</li>
  </ul>
</section>

<!-- Bad -->
<div class="header">
  <h1>Title</h1>
</div>
<div class="nav">
  <ul>
    <li><a href="index.html">Home</a></li>
    <li><a href="sitemap.html">Sitemap</a></li>
  </ul>
</div>
<div class="content">
  <h2>News</h2>
  <ul>
    <li>Good news.</li>
  </ul>
</div>
```


## スタイルはスタイルシートに記述する
 - セマンティック・ウェブ
pandoc -f markdown_github+yaml_metadata_block+fenced_code_attributes+fenced_code_blocks index.md -s -c github.css -t html5 -o index.html --self-contained --highlight-style=haddock