# ec-affiliate-site

[prototype] Amazon アソシエイト向けの商品紹介サイトの試作 — 静的 HTML を GitHub Pages で配信する。

- 正本（source of truth）: **このリポジトリ**（`obatatakafumi/ec-affiliate-site`・public）。配信先は `https://obatatakafumi.github.io/ec-affiliate-site/`（`_config.yml` の `url` + `baseurl`）。
- 位置づけ: EC 事業の検証用プロトタイプ。掲載している商品・価格・レビュー数・リンクは試作時点のサンプルで、実運用の商品選定・価格・在庫を反映していない。アソシエイト ID もプロトタイプ用の値。

## 構成

| パス | 内容 |
|---|---|
| `index.html` | トップページ（カテゴリと記事カードへの導線） |
| `articles/index.html` | 記事一覧 |
| `articles/*.html` | 商品紹介記事（介護・日用品・ペット・スキンケア・セール情報など 11 本）。各ページが CSS を内包する単体 HTML |
| `about.html` / `contact.html` / `privacy-policy.html` | サイト情報・連絡先・プライバシーポリシー（アソシエイト表示を含む） |
| `_config.yml` | GitHub Pages（Jekyll）の `title` / `description` / `url` / `baseurl` のみ。テーマやプラグインは使っていない |

ビルド工程は無い。HTML を直接編集して push すると GitHub Pages がそのまま配信する（Jekyll は `_config.yml` を読むだけで、`.html` は無加工で通る）。

## ローカルで確認する

```bash
cd ec-affiliate-site
python3 -m http.server 8000
# ブラウザで http://localhost:8000/ を開く（articles/ 以下も同じサーバーで見られる）
```

リンクは `baseurl` を前提にした相対パスなので、ローカルではルート直下で開く。

## ここに無いもの

- 本番の商品選定・価格の根拠・収益データ（EC 事業の分析は別リポジトリ `ec-research` と Obsidian 側）。
- ビルドツール・テンプレートエンジン・CMS（意図的に素の HTML）。
- 解析タグ・フォームのバックエンド（`contact.html` は静的な案内のみ）。
- 個人情報・認証情報（公開リポジトリなので置かない。pre-commit の gitleaks を迂回しない）。
