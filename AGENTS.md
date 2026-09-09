## Project Overview

タイピングと英会話を同時に学習できるWebアプリケーション。
バックエンドおよびサーバーサイドレンダリングにはDjangoを使用する。

## Tech Stack

- Python
- Django
- SQLite（開発環境）
- PostgreSQL（本番環境を採用する場合は事前に確認する）

## Project Structure

- Djangoの設定はプロジェクト設定用パッケージに配置する
- 機能ごとにDjangoアプリを分割する
- テンプレート、静的ファイル、テストは各アプリの責務に沿って配置する
- ビジネスロジックをビューやテンプレートへ集中させない

## Setup

仮想環境を有効化したうえで、依存パッケージをインストールする。

```bash
python -m pip install -r requirements.txt
python manage.py migrate
```

## Development Commands

```bash
python manage.py runserver
python manage.py check
python manage.py test
```

モデル変更時：

```bash
python manage.py makemigrations
python manage.py migrate
```

## Working Agreements

- 変更後は `python manage.py check` と関連テストを実行する
- テストが成功したことを確認してからコミットする
- 依存パッケージを追加・更新する前に確認を求める
- 新しいDjangoアプリの追加や主要なモデル設計は、実装前に確認を求める
- モデル変更時はマイグレーションファイルを作成し、コードと一緒に管理する
- 不具合修正では、可能な限り再現テストを追加する
- Django標準機能を優先し、不要な独自実装を避ける
- 既存の命名規則とコード構成を維持する

## Database and Migrations

- 過去に適用されたマイグレーションファイルを安易に書き換えない
- データ削除や後方互換性のないスキーマ変更は、実施前に確認を求める
- データマイグレーションはロールバックの可能性を考慮して作成する

## Security

- Djangoのセキュリティ機能を無効化しない
- CSRF保護、認証、認可を迂回しない
- ユーザー入力は必ず検証する
- シークレットや認証情報をコードへ直接記述しない

## Boundaries

- `.env*` ファイルを変更・コミットしない
- 本番環境の設定やデータを変更しない
- データベースの破壊的操作を許可なく実行しない
- `SECRET_KEY`、APIキー、パスワードを表示・記録・コミットしない
