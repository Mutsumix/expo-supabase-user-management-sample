# React Native + Supabase プロフィールアプリ

React Native と Supabase を使用した、ユーザー認証とプロフィール管理機能を備えたモバイルアプリケーションです。

## 機能概要

- 🔐 ユーザー認証（メールアドレス認証）
- 👤 プロフィール情報の管理
- 📸 プロフィール画像のアップロード
- 🌐 ウェブサイト URL の設定

## 技術構成

### フロントエンド

- [React Native](https://reactnative.dev/) - クロスプラットフォームモバイルアプリケーション開発フレームワーク
- [Expo](https://expo.dev/) - React Native の開発ツール
- [TypeScript](https://www.typescriptlang.org/) - 型安全な JavaScript
- [@rneui/themed](https://reactnativeelements.com/) - UI コンポーネントライブラリ
- [Expo Image Picker](https://docs.expo.dev/versions/latest/sdk/imagepicker/) - 画像選択機能
- [react-native-url-polyfill](https://github.com/charpeni/react-native-url-polyfill) - URL API のポリフィル

### バックエンド

- [Supabase](https://supabase.com/) - バックエンドサービス
  - 認証機能
  - データベース
  - ストレージ（画像保存用）

## 開発環境のセットアップ

### 前提条件

- Node.js (v16.0.0 以上)
- npm または yarn
- Expo CLI
- iOS/Android シミュレータ（オプション）

### インストール手順

1. 必要なパッケージのインストール

```bash
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

### アプリの起動

1. 開発サーバーの起動

```bash
npx expo start
```

2. 以下のオプションが利用可能：

- `i` - iOS シミュレータで起動
- `a` - Android エミュレータで起動
- `w` - Web ブラウザで起動
- QR コードをスキャン - 実機での動作確認（Expo Go アプリが必要）

## プロジェクト構成

```
├── components/
│   ├── Account.tsx    # プロフィール画面
│   ├── Auth.tsx       # 認証画面
│   ├── Avatar.tsx     # アバター画像コンポーネント
│   └── Header.tsx     # ヘッダーコンポーネント
├── lib/
│   └── supabase.ts    # Supabase クライアント設定
├── assets/            # アプリアイコンなどの静的ファイル
└── App.tsx            # アプリケーションのエントリーポイント
```

## Supabase の設定

1. Supabase でプロジェクトを作成
2. Storage bucket の作成
   - `avatars`という名前でバケットを作成
   - パブリックアクセスの設定を確認
3. プロフィールテーブルの作成：

```sql
create table profiles (
  id uuid references auth.users on delete cascade,
  username text,
  website text,
  avatar_url text,
  updated_at timestamp with time zone,
  primary key (id)
);
```

## トラブルシューティング

- Expo Go で接続できない場合：
  - 開発 PC とモバイル端末が同じ WiFi ネットワークに接続されているか確認
  - ファイアウォールの設定を確認
- 環境変数が読み込めない場合：
  - `.env`ファイルが正しい場所にあるか確認
  - アプリを再起動

## ライセンス

MIT
