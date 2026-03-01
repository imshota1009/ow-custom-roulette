# 🎮 OW カスタムルーレット 🐱

オーバーウォッチのカスタムゲーム（10人）で、チームとロールをルーレットで決めるWebアプリ！

🌐 **アプリURL**: [https://ow-custom-roulette.web.app](https://ow-custom-roulette.web.app)

---

## ✨ 特徴

- 🏠 **ルーム機能** — 部屋を作ってURLを共有するだけ！各自のスマホ・PCから参加できる
- 🎰 **ルーレット演出** — スロットマシン風の演出で盛り上がる！
- 🐱 **ねこが発表** — かわいいねこキャラが1人ずつロールとキャラを発表
- ⚔️ **5vs5 自動編成** — タンク1 / DPS2 / サポート2 の正しい編成で自動振り分け
- 🎯 **自分のキャラを使う** — 各ロールで自分が1番使っているキャラが割り当てられる

---

## 📖 使い方

### 1️⃣ 部屋をつくる
ホスト役の人が「🏠 部屋をつくる」をタップ

### 2️⃣ URLを共有
表示されたURLを友達にLINEなどで共有（📋コピーボタンあり）

### 3️⃣ キャラを入力
全員がURLを開いて、自分の **名前・タンク・DPS・サポート** の得意キャラを入力して「登録する！」

### 4️⃣ ルーレット開始！
10人全員揃ったら、ホストが「🎰 ルーレット開始！」ボタンをタップ

### 5️⃣ 結果発表！
ねこが1人ずつ発表 → チームA vs チームB の編成一覧が表示！

---

## 🛠️ 技術スタック

| 技術 | 用途 |
|------|------|
| HTML / CSS / JavaScript | フロントエンド |
| Firebase Realtime Database | リアルタイムデータ同期 |
| Firebase Hosting | Webホスティング |

---

## 📸 スクリーンショット

### ロビー画面
<img src="docs/lobby.png" alt="ロビー画面" width="600">

### 部屋画面（キャラ入力）
<img src="docs/room.png" alt="部屋画面" width="600">

---

## 🚀 セットアップ（開発者向け）

```bash
# クローン
git clone https://github.com/imshota1009/ow-custom-roulette.git
cd ow-custom-roulette

# Firebase CLIをインストール
npm install -g firebase-tools

# Firebaseにログイン
firebase login

# ローカルでテスト
firebase serve

# デプロイ
firebase deploy
```

---

## 📄 ライセンス

このプロジェクトは [MIT License](LICENSE) の下で公開されています。

## 🤝 コントリビュート

貢献方法については [CONTRIBUTING.md](CONTRIBUTING.md) をご覧ください。

## 📚 学習

このプロジェクトの技術的な詳細は [LEARN.md](LEARN.md) をご覧ください。
