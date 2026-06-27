# Live Scores Dashboard — Product Requirements Document

## Overview

A personal live sports score dashboard that surfaces real-time game scores across NBA, WNBA, and FIFA World Cup in a single, always-up-to-date view. The primary use case is quickly checking scores without navigating to multiple apps or sites.

---

## Goals

- See live and final scores for today's games across multiple sports at a glance
- Know immediately when a game is in progress vs. scheduled vs. finished
- Have scores refresh automatically without manual intervention
- Open instantly with no login, no account, and no friction

---

## Non-Goals

- Historical stats, standings, or player data
- Notifications or push alerts
- Social features (comments, sharing)
- Mobile app (web only)
- Sports beyond the initial three (NBA, WNBA, FIFA World Cup)

---

## Users

Single user (personal tool). No authentication or multi-user support required.

---

## Features

### Sports Coverage

| Sport | Status |
|---|---|
| NBA | Supported |
| WNBA | Supported |
| FIFA World Cup | Supported |

### Score Cards

Each game is displayed as a card showing:
- Away team: logo, abbreviation, score
- Home team: logo, abbreviation, score
- Game status: current quarter/period and clock, or scheduled start time, or "Final"

### Live Game Indicators

- Cards for in-progress games have a green border
- A pulsing "LIVE" badge appears on active games
- Each sport tab shows a green bubble with the count of live games

### Game Sorting

Within each sport tab, games are ordered:
1. In-progress (live)
2. Upcoming (not started)
3. Final

### Auto-Refresh

- Scores refresh every 30 seconds automatically
- A countdown ring in the bottom left shows time until next refresh
- A manual "Refresh" button in the header allows an immediate reload

### Empty & Error States

- If no games are scheduled for a sport today, a friendly "No games today" message is shown
- If the data fetch fails (e.g., no internet), an error message is shown with context

---

## Technical Decisions

| Decision | Choice | Reason |
|---|---|---|
| Data source | ESPN unofficial scoreboard API | Free, no API key required, covers all three sports |
| Frontend | Vanilla HTML/CSS/JS (single file) | No Node.js available on the machine; single file opens directly in any browser |
| Refresh strategy | Client-side polling every 30s | Simple and sufficient for sports score granularity |
| Deployment | Local file (`index.html`) | Personal tool, no hosting needed |

### API Endpoints

```
NBA:            https://site.api.espn.com/apis/site/v2/sports/basketball/nba/scoreboard
WNBA:           https://site.api.espn.com/apis/site/v2/sports/basketball/wnba/scoreboard
FIFA World Cup: https://site.api.espn.com/apis/site/v2/sports/soccer/fifa.world/scoreboard
```

---

## File Structure

```
maddy playground/
├── readme.md                     ← this file
└── scores-dashboard/
    └── index.html                ← the entire app (open in browser)
```

---

## How to Run

Open `scores-dashboard/index.html` in any browser. No server, build step, or installation required.

---

## Future Ideas (Not Scoped)

- Add more sports: NFL, MLB, NHL, Premier League
- Date picker to view past or upcoming game schedules
- Browser notification when a followed team's game goes live
- Responsive mobile layout
- Dark/light theme toggle
