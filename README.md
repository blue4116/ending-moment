# ひとひら — ending moments

日々の記録を残すためのWebアプリです。GitHub Pagesではブラウザー側の画面を公開し、記録は利用中の端末の `localStorage` に保存します。

## GitHub Pagesへの公開

1. このフォルダーの内容をGitHubリポジトリのルートに置き、`main` ブランチへ push します。
2. リポジトリの **Settings → Pages → Build and deployment** を開き、Sourceを **GitHub Actions** にします。
3. `main` へのpush後、**Actions** タブの「Deploy to GitHub Pages」が完了すると公開されます。

プロジェクト用リポジトリ（例: `owner/ending-moments`）では `/ending-moments/` のURLに対応する形で自動ビルドします。カスタムドメインやユーザーサイトでもルートパスでビルドします。

## GitHub Pagesで使える機能

- 日記やひとことなど、ブラウザー内に保存する記録
- 録音の端末内保存、ブラウザーが対応している場合の読み上げ
- 画面の表示、テーマ切り替え、印刷

## サーバーが必要な機能

このプロジェクトにはNode.js APIサーバーとデータベースも含まれますが、GitHub Pagesは静的サイトのホスティングです。Pagesだけではログイン、端末間同期、AIによる要約・返答・文字起こし、共有手紙の発行と閲覧は動作しません。これらを有効にするには、APIサーバーとデータベースを別のホスティング先へ配置し、OAuthやAIなどのサーバー環境変数を設定する必要があります。

GitHub Actionsの公開設定はフロントエンドのビルドとデプロイを行います。サーバーの秘密情報をGitHub Pagesのフロントエンドに設定しないでください。

## ローカル開発

Node.js 22とpnpm 10.4.1を用意してから:

```sh
pnpm install --frozen-lockfile
pnpm run build:pages
```

サーバーを含めた開発・本番実行には、`.env` の設定とデータベースが必要です。`pnpm dev` と `pnpm start` はAPIサーバーを起動します。
