# Quiniela Mundial 2026 — Blueprint 1

React app for a family World Cup 2026 prediction pool (quiniela). Supports up to 50 participants.

## Features

- **Group stage predictions** — enter scores for all 72 group matches across 12 groups
- **Knockout bracket** — predict winners for R32, R16, QF, SF, and Final
- **Live standings** — group tables update in real time as scores are entered
- **Leaderboard** — ranked by points with medal display
- **Player dashboard** — detailed points breakdown per participant
- **Admin panel** (password: `admin2026`)
  - Approve / reject / reset submissions
  - Enter official match results (group + knockout)
  - View participants still in progress (draft) with progress bar
  - Export all predictions to CSV
- **Auto-save drafts** — progress saved automatically as players fill in predictions
- **Late entry support** — configurable penalty points for late submissions
- **Persistent storage** — uses `window.storage` shared key-value API

## Scoring

| Category | Points |
|---|---|
| Exact score | +3 pts |
| Group qualifier (top 2) | +3 pts each |
| Best 3rd place | +3 pts each |
| Round of 32 | +5 pts |
| Round of 16 | +8 pts |
| Quarter-finals | +10 pts |
| Semi-finals | +12 pts |
| Champion | +18 pts |

Tiebreaker: earliest submission wins.

## Deadlines (hardcoded)

- Edit deadline: June 11, 2026 10am CT
- Late submission deadline: June 14, 2026 11pm CT

## Setup

This is a single-file React artifact built for the Claude.ai artifact runner.

### To run locally

```bash
npm create vite@latest worldcup-pool -- --template react
cd worldcup-pool
# Replace src/App.jsx with App.jsx from this repo
npm install
npm run dev
```

> **Note:** Replace `window.storage` calls with `localStorage` when running outside Claude.ai:
>
> ```js
> // storeGet
> const val = localStorage.getItem(k);
> return Promise.resolve(val ? JSON.parse(val) : null);
>
> // storeSet
> localStorage.setItem(k, JSON.stringify(v));
> return Promise.resolve();
> ```

## Storage Keys

| Key | Contents |
|---|---|
| `wc2026:v7p` | Participants array |
| `wc2026:v7r` | Official results |
| `wc2026:v7s` | Settings (penalty, etc.) |

## Admin Password

Default: `admin2026` — change the `ADMIN_PW` constant in `App.jsx` before deploying.

## Blueprint

This is **Blueprint 1** — the reference build for the World Cup 2026 family pool app.
