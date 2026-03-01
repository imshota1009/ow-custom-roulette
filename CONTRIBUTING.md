# 🤝 コントリビューティングガイド

OW カスタムルーレットへの貢献に興味を持っていただきありがとうございます！🐱

---

## 📝 貢献の方法

### 🐛 バグ報告
1. [Issues](https://github.com/imshota1009/ow-custom-roulette/issues) ページを開く
2. 「New Issue」をクリック
3. バグの詳細（何が起きたか、期待される動作、再現手順）を記入

### 💡 機能提案
1. [Issues](https://github.com/imshota1009/ow-custom-roulette/issues) ページを開く
2. 「New Issue」をクリック
3. 追加したい機能の説明を記入

### 🔧 コードの変更
1. このリポジトリをフォーク
2. 新しいブランチを作成: `git checkout -b feature/素敵な機能`
3. 変更を加える
4. コミット: `git commit -m '素敵な機能を追加'`
5. プッシュ: `git push origin feature/素敵な機能`
6. プルリクエストを作成

---

## 🏗️ 開発環境のセットアップ

```bash
# リポジトリをクローン
git clone https://github.com/imshota1009/ow-custom-roulette.git
cd ow-custom-roulette

# Firebase CLIをインストール（まだの場合）
npm install -g firebase-tools

# Firebaseにログイン
firebase login

# ローカルサーバーを起動
firebase serve
```

ブラウザで `http://localhost:5000` を開いて動作確認できます。

---

## 📋 コードスタイル

- インデントは **スペース2つ**
- 変数名・関数名は **キャメルケース** (例: `createRoom`, `myPlayerId`)
- コメントは **日本語OK**
- CSSカスタムプロパティ（変数）を活用する

---

## 🙏 行動規範

- お互いに敬意を持って接しましょう
- 建設的なフィードバックを心がけましょう
- 楽しくコーディングしましょう！🎮

---

ご不明な点があれば、お気軽にIssueでお問い合わせください！
