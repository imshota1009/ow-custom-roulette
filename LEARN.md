# 📚 LEARN.md — What You Can Learn from This Project

This document explains the technologies used in OW Custom Roulette.

---

## 🔥 Firebase Realtime Database

### What is it?
A "real-time database" provided by Google. When someone writes data, it is **instantly reflected** on every connected user's screen.

### How it's used in this app
- **Room creation**: Saves room data (room ID, player list) to the database
- **Real-time sync**: When someone registers, everyone's player list updates automatically
- **Sharing results**: Writes roulette results to the database → reflected on everyone's screen

### Where in the code
Inside the `<script>` tag of `public/index.html`:
```javascript
// Write to the database
await roomRef.child('players/' + myPlayerId).set({ name, tank, dps, support });

// Watch for real-time changes
playersRef.on('value', (snap) => {
  const players = snap.val();
  updateMemberList(players); // Update the UI
});
```

---

## 🏠 Firebase Hosting

### What is it?
A service that lets you publish websites to the world. Just upload your HTML files and you get a URL anyone can access.

### How to use
```bash
firebase deploy --only hosting
```
That's all it takes to publish to `https://ow-custom-roulette.web.app`!

---

## 🎰 How the Roulette Animation Works

### Slot Machine
We use CSS `overflow: hidden` to create the slot "window", then use JavaScript to rapidly scroll the content inside.

```javascript
// Spinning (rapid movement with setInterval)
r._interval = setInterval(() => {
  pos -= speed;
  el.style.top = pos + 'px';
}, 30);

// Stopping (display final result)
clearInterval(r._interval);
el.innerHTML = `<div>${finalText}</div>`;
```

---

## 🔀 Team Assignment Algorithm

### Shuffle — Fisher-Yates Method
A well-known algorithm for randomly shuffling an array:

```javascript
function shuffle(arr) {
  const a = [...arr];
  for (let i = a.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [a[i], a[j]] = [a[j], a[i]]; // Swap
  }
  return a;
}
```

### Role Assignment
1. Shuffle all 10 players and split into two groups of 5
2. Shuffle the role array `['tank', 'dps', 'dps', 'support', 'support']`
3. Assign a random role to each player
4. Apply the hero that each player entered for their assigned role

---

## 🌐 Room Sharing via URL Parameters

We use the `?room=XXXXX` URL parameter to share rooms:

```javascript
// Get room ID from URL
const params = new URLSearchParams(window.location.search);
const roomFromUrl = params.get('room');
if (roomFromUrl) {
  joinRoom(roomFromUrl); // Automatically join the room
}
```

This allows players to automatically join a room just by clicking a URL.

---

## 📱 Responsive Design

We use CSS `@media` queries to ensure the layout looks great on both mobile and desktop:

```css
@media (max-width: 600px) {
  .app-header h1 { font-size: 1.5rem; }
  .member-list { grid-template-columns: 1fr 1fr; }
}
```
