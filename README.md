## プロジェクトのセットアップ手順

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
