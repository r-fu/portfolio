# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 概要

素の HTML・CSS・jQuery で作られたシングルページの個人ポートフォリオサイト（日本語）です。ビルドシステム、パッケージマネージャー、リンター、テストスイートはありません。ファイルを直接編集し、そのまま配信します。

## 開発

ビルドやテストのコマンドはありません。ローカルでプレビューするには、リポジトリのルートを任意の静的ファイルサーバーで配信します。例:

```bash
python3 -m http.server 8000
```

その後 `http://localhost:8000` を開きます。`index.html` をブラウザで直接開いても動作します。

## 構成

- `index.html` — サイト全体。アンカーリンクされた4つのセクション（`#Profile`、`#skill`、`#works`、`#contact`）を持つ1ページと、`<body>` 末尾の PhotoSwipe ライトボックス用マークアップで構成されます。
- `css/style.css` — カスタムスタイルすべて。セクション区切りコメントで整理されています。レスポンシブのブレークポイントは `max-width: 767px` と `max-width: 540px` です。`css/reset.css` は CSS リセットです。
- `js/script.js` — カスタムの挙動: アンカーリンクのスムーススクロール、スクロール時のナビ固定、PhotoSwipe の初期化。
- `css/photoswipe/` と `js/photoswipe/` — 同梱（vendored）の PhotoSwipe ライトボックスライブラリと、そのセットアップスクリプト（`js/photoswipe/photoswipe_setup.js`）。ライブラリ本体はサードパーティとして扱い、カスタマイズしてよいのは `photoswipe_setup.js` のみです。

## 主な規約

- 外部依存（jQuery 1.12.4、Bootstrap 4.1.3 CSS、Font Awesome 5.2、Google Fonts）は `index.html` で CDN から読み込みます。`node_modules` やローカルコピーはありません。
- Bootstrap は SKILL セクションのテーブルスタイル（`table table-borderless`）にのみ使用しています。レイアウトはそれ以外、`css/style.css` で定義されたカスタムクラス（`card`、`card-wrapper`、`two-column-wrapper` など）を使います。
- スキル評価は `.rating` スパン内の `rate rate1`〜`rate rate5` クラスで描画します。
- WORKS の各エントリは `.my-gallery` 内の `<figure class="card">` ブロックです。PhotoSwipe 用の `<a>` ラッパーは現在コメントアウトされているため、サムネイルはライトボックスとしてクリックできません。
- サイトのコンテンツ（プロフィール文、スキル、制作物）は日本語で書かれています。新しいユーザー向けコンテンツも日本語で統一してください。
- このリポジトリのコミットメッセージは日本語で書きます。
