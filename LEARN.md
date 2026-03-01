# 📚 LEARN.md — このプロジェクトから学べること

このドキュメントでは、OW カスタムルーレットで使われている技術を解説します。

---

## 🔥 Firebase Realtime Database

### これは何？
Googleが提供する「リアルタイム データベース」です。誰かがデータを書き込むと、接続中の全員の画面に**一瞬で反映**されます。

### このアプリでの使い方
- **部屋の作成**: 部屋のデータ（ルームID、参加者リスト）をデータベースに保存
- **リアルタイム同期**: 誰かが登録すると、全員の画面の参加者リストが自動更新
- **結果の共有**: ルーレット結果をデータベースに書き込み → 全員の画面に反映

### コードの場所
`public/index.html` の `<script>` タグ内:
```javascript
// データベースに書き込み
await roomRef.child('players/' + myPlayerId).set({ name, tank, dps, support });

// リアルタイムで変更を監視
playersRef.on('value', (snap) => {
  const players = snap.val();
  updateMemberList(players); // 画面を更新
});
```

---

## 🏠 Firebase Hosting

### これは何？
Webサイトを世界中に公開できるサービスです。HTMLファイルをアップロードするだけで、誰でもアクセスできるURLが発行されます。

### 使い方
```bash
firebase deploy --only hosting
```
これだけで `https://ow-custom-roulette.web.app` に公開されます！

---

## 🎰 ルーレット演出の仕組み

### スロットマシン
CSSの `overflow: hidden` でスロットの「窓」を作り、JavaScriptで中身を高速スクロールさせています。

```javascript
// 回転（setIntervalで高速移動）
r._interval = setInterval(() => {
  pos -= speed;
  el.style.top = pos + 'px';
}, 30);

// 停止（最終結果を表示）
clearInterval(r._interval);
el.innerHTML = `<div>${finalText}</div>`;
```

---

## 🔀 チーム振り分けアルゴリズム

### シャッフル — Fisher-Yates法
配列をランダムに並べ替える有名なアルゴリズムです：

```javascript
function shuffle(arr) {
  const a = [...arr];
  for (let i = a.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [a[i], a[j]] = [a[j], a[i]]; // 入れ替え
  }
  return a;
}
```

### ロール割り当て
1. 10人をシャッフルして5人ずつに分割
2. ロール配列 `['tank', 'dps', 'dps', 'support', 'support']` もシャッフル
3. 各プレイヤーにランダムなロールを割り当て
4. 割り当てられたロールに対応する、そのプレイヤー自身が入力したキャラを適用

---

## 🌐 URLパラメータでの部屋共有

URLの `?room=XXXXX` パラメータを使って部屋を共有しています：

```javascript
// URLからルームIDを取得
const params = new URLSearchParams(window.location.search);
const roomFromUrl = params.get('room');
if (roomFromUrl) {
  joinRoom(roomFromUrl); // 自動的に部屋に入る
}
```

これにより、URLをクリックするだけで自動的に部屋に入れます。

---

## 📱 レスポンシブデザイン

CSS の `@media` クエリを使って、スマホでもPCでも見やすいレイアウトにしています：

```css
@media (max-width: 600px) {
  .app-header h1 { font-size: 1.5rem; }
  .member-list { grid-template-columns: 1fr 1fr; }
}
```
