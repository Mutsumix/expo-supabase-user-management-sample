## 開発環境のセットアップ

1. 必要なパッケージのインストール

```
npm install
```

2. 環境変数の設定
   プロジェクトのルートで`.env.example`をコピーして`.env`ファイルを作成：

```bash
cp .env.example .env
```

`.env`ファイルを開き、Supabase プロジェクトの認証情報を設定：

```
EXPO_PUBLIC_SUPABASE_URL=your_supabase_project_url
EXPO_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
```
