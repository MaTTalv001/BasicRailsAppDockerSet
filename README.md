# Docker Rails 開発環境の構築

### gitclone 後、初期ファイルの確認

1.  `Dockerfile` : バージョンの記述を必要に応じて修正
2.  `docker-compose.yml` : ポート番号など必要に応じて修正
3.  `Gemfile` : Rails のバージョンを必要に応じて修正

### rails アプリの作成

- オプションは必要に応じて変更
- コマンド実行後、確認画面が出た場合は y で可

```bash
docker compose run --rm web rails new . -d=postgresql -j=esbuild -c=bootstrap
```

### database.yml の編集

`config/database.yml`に、Docker で立ち上げた DB 用のコンテナに接続するための情報を記載する

```yml
host: db
username: postgres
password: password
```

# プロジェクトのセットアップ

### Docker を使った環境準備(イメージのビルド)

```
docker compose build
```

### rails サーバーの起動(バックグラウンドでのコンテナの立ち上げと rails サーバーの起動)

```
docker compose up
```

### コンテナ内に入る(rails・bundler・yarn 関係のコマンドはコンテナ内で実行)

```
docker compose exec web bash
```

### Gem のインストール

- 予め必要な追加 Gem がある場合は`Gemfile`に追記する
- それらは`add_to_gemfile.txt`にメモしておく

```bash
bundle install
```

### node_modules のインストール

```bash
yarn install
```

### データベースの作成(コンテナ内で実行)

```bash
bin/rails db:create
```

### CSS, JS 用のサーバー起動(コンテナ内で実行・)

```
bin/dev
```

### Docker コンテナの終了

```bash
docker compose down
```
