# NIVÉRA AOYAMA — GitHub Pages 公開用パッケージ

架空ヘアサロン「NIVÉRA AOYAMA」のサンプルHP（1ページ・レスポンシブ）。
実在する店舗・人物・サービスとは関係ありません。予約・電話・LINE・問い合わせ・Instagram操作はすべてサンプル説明モーダルを表示します。

## 構成（このフォルダ＝公開ルート）
```
index.html        エントリーポイント（そのまま開けば動作）
support.js         レンダリングランタイム（index.htmlが相対参照）
assets/            画像・ロゴ（写真=JPEG最適化済 / logo-symbol.png=favicon兼用）
```
すべて**相対パス**参照。サブディレクトリ公開（`https://<user>.github.io/<repo>/`）でもパスは壊れません。ビルド工程なし。

## GitHub Pages 公開手順
1. このフォルダの中身（`index.html` / `support.js` / `assets/`）をリポジトリ直下に置いてコミット
2. GitHub → Settings → Pages → Source: `Deploy from a branch`、Branch: `main` / `(root)` を選択
3. 数十秒後に発行される `https://<user>.github.io/<repo>/` が公開URL

`/docs` 公開にする場合は3ファイルを `docs/` に入れ、Pagesのフォルダを `/docs` に設定してください。

## 公開前の推奨設定
- **検索エンジンに載せる場合**：`index.html` の `<meta name="robots" content="noindex, nofollow">` を削除
- **OGP画像の絶対URL化**：`<meta property="og:image" content="assets/hero-01-exterior.jpg">` を公開URL基準の絶対URL（`https://<user>.github.io/<repo>/assets/hero-01-exterior.jpg`）に変更するとSNSプレビューが安定します

## 予約導線を実URLへ切り替える場所
現在は予約/電話/LINE/Instagram/フォーム送信がすべてサンプルモーダル（`openModal`）を表示します。実運用化は `index.html` 内で：
- `onClick="{{ openModal }}"` を実URLの `<a href>` に、電話は `tel:`、LINEは `https://line.me/...` に置換
- フォームは `submitForm` の `preventDefault` を外し送信先を設定

## 店舗情報の編集
`index.html` 内 `<script data-dc-script>` のロジッククラス `this.D`（nav / heros / styles / recs / cats / staff / voices / steps / igs / faqs / hours）で一元管理。住所・電話等の固定表記は ACCESS / FOOTER のマークアップ内。

## 画像最適化について
写真は長辺1800px・JPEG(品質0.82)へ変換済み（元PNG合計約40MB → 約3MB）。差し替え時は同名・同拡張子で `assets/` に上書きしてください。オリジナルPNGはリポジトリ親側の `assets/` に保管しています。
