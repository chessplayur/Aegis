# Aegis Insight — AI Gameplay Intelligence Platform

> **Analyze your gameplay against professional players using AI pattern intelligence.**

---

## Overview

Aegis Insight is a single-file browser application that benchmarks player gameplay footage against professional esports players. Upload a clip, select a pro baseline, and receive a detailed performance report with charts, per-metric scores, and personalized coaching recommendations.

No backend required. Everything runs locally in the browser — no data is sent anywhere.

---

## Features

- **Video upload** — drag-and-drop or file picker; MP4, MOV, WEBM up to 500 MB. A demo session is available without any upload.
- **Professional baselines** — 14 real pro players across four titles, with links to their YouTube, Twitch, Liquipedia, and highlight pages.
- **AI analysis simulation** — seeded, deterministic metric generation across six dimensions so the same clip always produces the same result.
- **Ghost overlay** — blends a second copy of your footage over the player view for self-comparison.
- **Five charts** — skill radar, bar comparison, session timeline, overall donut, and horizontal improvement-targets bar.
- **Detailed comparison table** — per-metric delta vs. the pro baseline with mini progress bars.
- **Coaching report** — overall Pro Similarity score, tier badge (Developing → Elite), and four written coaching insights generated from the score.
- **Session history** — up to 15 sessions stored in `localStorage` with aggregate averages.
- **Export & share** — download the full report as JSON, copy a shareable URL, or print.
- **Keyboard shortcuts** — full keyboard control (see below).
- **Live telemetry sidebar** — animated frame-alignment, movement-smoothness, input-frequency, and reaction-stability meters.

---

## Supported Games & Pro Players

| Game | Players |
|---|---|
| **Valorant** | TenZ (Sentinels), Demon1 (EG), Aspas (Leviatán), yay (Cloud9) |
| **Counter-Strike 2** | s1mple (NAVI), ZywOo (Vitality), donk (Spirit), NiKo (G2) |
| **League of Legends** | Faker (T1), Chovy (GenG), Caps (G2) |
| **Apex Legends** | ImperialHal (TSM), Genburten (DZ), Zer0 (TSM) |

---

## Getting Started

Aegis Insight is a zero-dependency, single HTML file. No build step, no npm install.

```bash
# Clone or download
git clone https://github.com/your-org/aegis-insight.git
cd aegis-insight

# Open directly in your browser
open index.html
```

Or serve it locally to avoid any browser file-access restrictions:

```bash
npx serve .
# then open http://localhost:3000
```

The only external dependency is **Chart.js 4.4.1**, loaded from jsDelivr CDN, and Google Fonts — both require an internet connection on first load.

---

## Usage

1. **Upload** your gameplay clip (or click **Demo Session** to use sample footage).
2. **Select** your game and a professional baseline from the dropdowns.
3. Click **⚡ Launch** to open the analysis workspace.
4. Use **Sync** to start synchronized playback; toggle **Ghost** for overlay mode.
5. Click **📊 Analyze** to run the full analysis (~3 seconds).
6. Review the charts, metric cards, comparison table, and coaching report.
7. **Export** the report as JSON, copy a share link, or print.

---

## Keyboard Shortcuts

| Key | Action |
|---|---|
| `U` | Open file picker |
| `D` | Load demo session |
| `Space` | Play / Pause |
| `G` | Toggle ghost overlay |
| `A` | Run analysis |
| `C` | Toggle comparison table |
| `E` | Export JSON report |
| `N` | Focus session notes |

---

## Project Structure

```
index.html          # Entire application — styles, markup, and script in one file
README.md           # This file
```

The application is intentionally self-contained in a single HTML file for easy sharing and deployment on any static host (GitHub Pages, Netlify, Vercel, S3, etc.).

---

## Analysis Metrics

| Metric | Description |
|---|---|
| **Crosshair Accuracy** | Pre-aim efficiency, target acquisition, and precision consistency |
| **Movement Efficiency** | Pathing smoothness, strafing, and movement-while-firing penalties |
| **Reaction Timing** | Average decision-to-action latency in combat situations (ms) |
| **Positioning IQ** | Spacing, angle control, and map position vs. pro standards |
| **Game Sense** | Information usage, rotation timing, and macro decision quality |
| **Util Usage** | Ability/utility deployment efficiency and timing |

Scores are seeded from the filename and selected pro, so the same inputs always produce the same output — useful for A/B comparisons across sessions.

---

## Local Storage

Session history is stored in `localStorage` under the key `aegis-sessions-v3`. Up to 15 sessions are retained. Use **Clear history** in the footer to wipe all stored data.

---

## Deployment

Any static file host works:

```bash
# GitHub Pages — push to main, enable Pages in repo settings

# Netlify
netlify deploy --dir .

# Vercel
vercel --prod
```

---

## Tech Stack

- Vanilla HTML / CSS / JavaScript (ES2020, no framework)
- [Chart.js 4.4.1](https://www.chartjs.org/) — all five chart types
- [Google Fonts](https://fonts.google.com/) — Syne, JetBrains Mono, DM Sans
- Browser `localStorage` for session persistence
- Browser `URL.createObjectURL` for local video playback

