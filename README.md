# 🎱 Game Stats

A real-time pool/billiards match tracker for office colleagues. Track wins, losses, head-to-head stats, and language team rivalries — all shared live across any device.

**[▶ Open the App](https://varignana.github.io/gamestats)**

---

## Features

- 📊 Live leaderboard ranked by win percentage
- 🏆 Head-to-head stats between any two players
- 🌍 Language team filtering (English, Italian, French, German, Portuguese)
- ⏳ Match confirmation system — both players must agree on results
- 👤 Individual player login with password protection
- 🔒 Admin panel for managing players and approving matches
- 📈 General stats — longest win streak, biggest rivalry, most active player
- 📤 Export and import data as JSON
- 🔄 Real-time sync via Firebase — any device, any browser

---

## How to Use

### As a player
1. Open the app link
2. Tap **Login** at the top and select your name
3. Enter your password (given to you by the admin)
4. Go to **Log** tab to record a match — select if you won or lost and pick your opponent
5. The match appears as pending until your opponent confirms it
6. Go to **History** tab to confirm or reject matches logged against you
7. You can change your password in the **Players** tab under My Account

### As admin
1. Go to the **Players** tab and tap **Admin Login**
2. You can add players, set their initial passwords, and manage all data
3. Admin matches are confirmed instantly without needing approval
4. You can confirm or reject any pending match in the **History** tab

---

## Tech Stack

- **HTML, CSS, JavaScript** — single file app, no frameworks
- **Firebase Firestore** — real-time cloud database
- **GitHub Pages** — free hosting
- **flagcdn.com** — flag images

---

## Setup (for developers)

If you want to run your own copy:

1. Clone this repository
2. Create a free Firebase project at [firebase.google.com](https://firebase.google.com)
3. Create a Firestore database
4. Replace the Firebase config values in `index.html`
5. In Firestore create a collection called `admin` with a document called `credentials` containing `username` and `password` fields
6. Host on GitHub Pages or any static hosting

---

## Firebase Structure
```
gamestats/
  data        → players array and matches array
  settings    → leaderboard settings

admin/
  credentials     → admin username and password
  playerPasswords → each player's password
```

---

## Commit Convention

This project follows [Conventional Commits](https://www.conventionalcommits.org/):

- `feat:` new feature
- `fix:` bug fix
- `refactor:` code improvement
- `style:` visual changes

---

*Built with 🎱 and a lot of pool matches*
