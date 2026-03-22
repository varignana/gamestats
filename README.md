# 🎱 Game Stats

A real-time pool/billiards match tracker for office colleagues. Track wins, losses, ELO ratings, head-to-head stats, match odds and language team rivalries — all shared live across any device.

**[▶ Open the App](https://varignana.github.io/gamestats)**

---

## Features

### 🏆 Leaderboard
- ELO rating system — the same used in chess and football
- Ranked by ELO, showing win/loss record and win percentage
- Expandable player cards with head-to-head stats against every opponent
- Language team filter (English, Italian, French, German, Portuguese)
- Minimum matches threshold to prevent new players jumping to the top

### 🎯 Odds
- See win probability for any player against all opponents
- Ranked from hardest to easiest matchup
- Shows ELO points gained or lost for each possible result
- Colour coded — 🔴 tough, 🟡 even, 🟢 favourable
- Head-to-head history shown for each matchup
- Auto-selects logged-in player or strongest player by default

### ➕ Log Match
- Players must be logged in to log a match
- Select if you won or lost, then pick your opponent
- Matches go pending until the opponent confirms
- Admin can log any match instantly as confirmed
- Duplicate match detection — max 3 pending matches per pair per day

### 📋 History
- Full match history with ELO points won/lost per match
- Pending matches shown with confirm/reject buttons
- Players can edit or delete their own matches
- Admin can edit, delete, confirm or reject any match

### 👥 Players
- Admin protected panel for managing players
- Add players with language team and initial password
- Edit name, language and password
- ELO rating shown per player
- Players can change their own password in My Account

### 📊 General Stats
- Most active player
- Biggest rivalry (tappable to open head-to-head)
- Longest win streak
- Language team ELO rankings with average ELO per team

### 🔒 Security
- Admin login stored securely in Firebase
- Player passwords stored in Firebase
- API key restricted to GitHub Pages domain only
- Match confirmation system prevents false results

---

## How to Use

### As a visitor (not logged in)
- View the leaderboard and all stats
- Explore match odds for any player
- Browse match history

### As a player
1. Tap **Login** at the top and select your name
2. Enter your password (given by admin on first use)
3. Go to **Log** tab to record a match
4. Select if you won or lost and pick your opponent
5. The match appears as ⏳ pending until your opponent confirms
6. Go to **History** tab to confirm or reject matches logged against you
7. Change your password in the **Players** tab under My Account

### As admin
1. Go to **Players** tab and tap **Admin Login**
2. Add players, set passwords, manage all data
3. Admin matches are confirmed instantly
4. Confirm or reject any pending match in History
5. Export data as JSON backup anytime

---

## ELO Rating System

Everyone starts at **1000 ELO**. The rating updates after every confirmed match using the standard ELO formula:
```
Expected score = 1 / (1 + 10^((opponent ELO - your ELO) / 400))
New ELO = current ELO + 32 × (result - expected score)
```

Where result is 1 for a win and 0 for a loss. The K-factor of 32 means ratings move quickly, which is ideal for a casual office setting.

---

## Tech Stack

- **HTML, CSS, JavaScript** — single file app, no frameworks
- **Firebase Firestore** — real-time cloud database
- **Firebase Analytics (GA4)** — user behaviour tracking
- **GitHub Pages** — free hosting
- **flagcdn.com** — flag images
- **ELO rating system** — K-factor 32, base 1000

---

## Analytics Events Tracked

| Event | Description |
|---|---|
| `app_open` | User opens the app |
| `tab_view` | User switches tab (includes tab_name) |
| `player_login` | Player logs in (includes player_name) |
| `player_login_failed` | Failed login attempt |
| `player_logout` | Player logs out |
| `admin_login` | Admin logs in |
| `admin_logout` | Admin logs out |
| `match_logged` | Match is logged (includes status and logged_by) |
| `match_confirmed` | Match is confirmed by opponent |
| `match_rejected` | Match is rejected by opponent |
| `h2h_viewed` | Head-to-head screen opened |
| `language_filter` | Language team filter applied |
| `elo_info_toggled` | ELO info box opened or closed |
| `data_exported` | Data exported as JSON |
| `data_imported` | Data imported from JSON |
| `player_added` | New player added by admin |

---

## Firebase Structure
```
gamestats/
  data        → players array and matches array
  settings    → leaderboard settings (min matches threshold)

admin/
  credentials       → admin username and password
  playerPasswords   → each player's login password
```

---

## Setup (for developers)

If you want to run your own copy:

1. Clone this repository
2. Create a free Firebase project at [firebase.google.com](https://firebase.google.com)
3. Enable Firestore database in test mode
4. Enable Google Analytics when setting up the project
5. Register a web app and copy the config values
6. Replace the Firebase config placeholders in `index.html`
7. In Firestore create collection `admin` → document `credentials` with fields `username` and `password`
8. Restrict your API key to your domain in Google Cloud Console
9. Host on GitHub Pages or any static hosting

---

## Commit Convention

This project follows [Conventional Commits](https://www.conventionalcommits.org/):

- `feat:` new feature
- `fix:` bug fix
- `refactor:` code improvement
- `style:` visual changes
- `docs:` documentation
- `security:` security improvements

---

## Roadmap

- [ ] Firebase Authentication for proper user management
- [ ] Push notifications for pending match confirmations
- [ ] Monthly/weekly stat snapshots
- [ ] Tournament bracket mode

---

*Built with 🎱 Claude AI and a lot of pool matches*
