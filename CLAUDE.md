# Cielito Hayama — サイト管理ガイド

## プロジェクト概要
- **サイト名**: シエリート葉山 / Cielito Hayama
- **URL**: https://cielito-hayama.com（予定） / 現在: https://cielito-hayama.junko.tilgner.workers.dev
- **構成**: 静的HTML/CSSのみ（フレームワーク・CMSなし）
- **ファイル**: `index.html`（日本語）、`en.html`（英語）
- **ホスティング**: Cloudflare Pages（GitHubにpushすると自動デプロイ）
- **リポジトリ**: https://github.com/kaitivityai/cielito-hayama

## ファイル構成
```
site/
├── index.html          # 日本語版
├── en.html             # 英語版
├── assets/
│   ├── img/
│   │   ├── logo_white.png      # ヒーロー・フッター用ロゴ（白・透明背景）
│   │   ├── logo_cropped.jpg    # 元ロゴ（使用していない）
│   │   ├── 02-01.jpg〜06.jpg   # セクション1の写真
│   │   ├── 03-01.jpg〜06.jpg   # セクション2の写真
│   │   └── 04-01.jpg〜06.jpg   # セクション3の写真
│   └── video/
│       └── bg_web.mp4          # ヒーロー背景動画（1080p、約7MB）
```

## ⚠️ 変更前に必ずローカルで確認すること

**GitHubにpushすると即座に公開サイトに反映されます。**
必ずローカルで見た目を確認してからpushしてください。

### ローカルでプレビューする方法

ターミナルで以下を実行：

```bash
cd /path/to/cielito-hayama
python3 -m http.server 8000
```

ブラウザで http://localhost:8000 を開いて確認。
問題なければ `Ctrl+C` でサーバーを止めて、pushする。

### 変更 → 確認 → pushの流れ

```bash
# 1. ファイルを編集（index.html / en.html）

# 2. ローカルサーバーで確認
python3 -m http.server 8000
# ブラウザで http://localhost:8000 を確認
# スマホ表示も確認する（ブラウザの開発者ツール → モバイルビュー）

# 3. 問題なければcommit & push
git add index.html en.html
git commit -m "変更内容を簡潔に書く"
git push
# → Cloudflare Pagesが自動でデプロイ（1〜2分で反映）
```

## よく変更する箇所

### テキストを変える
`index.html`（日本語）または`en.html`（英語）を直接編集。

### 写真を差し替える
`assets/img/` に同じファイル名で上書きするだけでOK。
※ファイル名を変える場合はHTMLの`src`属性も変更すること。

### 予約リンクを変える
HTMLファイル内で `airbnb.jp/rooms/` を検索して該当箇所を変更。

### Instagramのアカウントを変える
HTMLファイル内で `cielito_hayama` を検索して変更。

## 注意事項
- `assets/video/bg.mp4`（元の4K動画）と`assets/video/bg_cropped.mp4`は`.gitignore`で除外済み。大きなファイルはGitHubにpushしないこと（100MB超はエラーになる）。
- ロゴは必ず`logo_white.png`（白・透明背景）を使うこと。`logo_cropped.jpg`は白背景があるため使用不可。
