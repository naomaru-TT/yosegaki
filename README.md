# 🎊 2025年 振り返り寄せ書きアプリ

会場にいるメンバーがQRコードをスキャンして、その場でメッセージを書き込める Web 寄せ書きアプリです。  
Firebase Realtime Database によりリアルタイムで共有され、全員のメッセージがカラフルな付箋としてボードに表示されます。

**公開URL:** https://naomaru-tt.github.io/yosegaki/

---

## 📋 概要・目的

- 会場でQRコードを提示するだけで、参加者全員がスマホからメッセージを投稿できる
- 1年の振り返りや感謝の気持ちをリアルタイムで共有する
- インストール不要・ログイン不要で誰でもすぐに使える

---

## 🚀 使い方

### 1. メッセージを書く（✏️ 書くタブ）

1. ニックネームまたはイニシャルを入力（例：いわちゃん / T.N.）
2. メッセージを入力（最大120文字）
3. 付箋の色を選ぶ（8色から選択）
4. 「送信する」ボタンをタップ

> ⚠️ セキュリティのため、フルネームではなくニックネームまたはイニシャルで入力してください。

### 2. 寄せ書きボードを見る（🗒️ ボードタブ）

- 投稿されたメッセージが付箋スタイルで一覧表示される
- 「↺ 更新」ボタンで最新のメッセージを再読み込みできる
- 自分が投稿したメッセージには「編集」「削除」ボタンが表示される

### 3. QRコードを共有する（📱 QRタブ）

1. このアプリのURL（`https://naomaru-tt.github.io/yosegaki/`）を入力
2. 「生成」ボタンを押してQRコードを表示
3. 会場のスクリーンに映すか印刷して参加者に配布する

---

## ✨ 機能一覧

| 機能 | 説明 |
|------|------|
| メッセージ投稿 | ニックネーム・メッセージ・付箋色を選んで送信 |
| ボード表示 | 全員のメッセージを付箋スタイルで表示 |
| 自分のメッセージを編集 | メッセージ内容と付箋の色を変更できる |
| 自分のメッセージを削除 | 確認ダイアログ付きで削除 |
| QRコード生成 | URLを入力してQRコードを作成・表示 |
| リアルタイム共有 | Firebase により全端末でリアルタイム反映 |

> 「自分のメッセージ」の識別はブラウザの localStorage で管理しています。  
> 同じ端末・同じブラウザからのみ編集・削除が可能です。

---

## 🛠 使用技術・構成

```
yosegaki/
└── index.html   # アプリ本体（HTML / CSS / JavaScript 単一ファイル）
```

### フロントエンド

- **HTML / CSS / JavaScript**（フレームワークなし・単一ファイル構成）
- フォント：[Zen Maru Gothic](https://fonts.google.com/specimen/Zen+Maru+Gothic)（Google Fonts）

### バックエンド・インフラ

| サービス | 用途 |
|----------|------|
| [Firebase Realtime Database](https://firebase.google.com/products/realtime-database) | メッセージのリアルタイム保存・共有 |
| [GitHub Pages](https://pages.github.com/) | 静的ファイルのホスティング |
| [Firebase JavaScript SDK v10](https://www.gstatic.com/firebasejs/10.12.2/) | Firebase 接続（CDN経由） |
| [QR Server API](https://goqr.me/api/) | QRコード画像の生成 |

### Firebase 設定

| 項目 | 値 |
|------|----|
| プロジェクトID | `yosegaki-2f7e6` |
| Database URL | `https://yosegaki-2f7e6-default-rtdb.firebaseio.com` |
| プラン | Spark（無料） |
| セキュリティルール | テストモード（読み書き自由） |

> ⚠️ 現在はテストモードで運用しています。本番利用する場合はセキュリティルールの見直しを推奨します。

---

## 📦 デプロイ手順

### Firebase セットアップ

1. [Firebase Console](https://console.firebase.google.com/) でプロジェクトを作成
2. **Realtime Database** を有効化 → テストモードで開始
3. プロジェクト設定 → ウェブアプリを登録 → `firebaseConfig` の値を取得
4. `index.html` 内の `FIREBASE_CONFIG` に値を記載

### GitHub Pages へのデプロイ

1. GitHubでリポジトリを作成（Public）
2. `index.html` と `README.md` をアップロード
3. Settings → Pages → Branch: `main` → Save
4. `https://<ユーザー名>.github.io/<リポジトリ名>/` でアクセス可能

---

## 📝 注意事項

- メッセージはFirebase Realtime Databaseに保存されます（無料枠：1GB / 同時接続100件）
- テストモードのセキュリティルールは **30日後に期限切れ** になります
- 編集・削除権限はlocalStorageで管理するため、ブラウザのデータを消去すると失われます
