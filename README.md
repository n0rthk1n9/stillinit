# Hyyyypeee. WHO wins the Club World Cup 😜

# Still In It ⚽

**Which clubs still have skin in the game at the 2026 World Cup?**

A single-file, mobile-first web app that traces eight clubs — player by player — through the nations left standing at the FIFA World Cup 2026. It counts both **current squad members** and **former first-teamers**, ranks the clubs, and updates itself automatically as each round knocks teams out.

Born from a simple question: *how many ex-Dortmund players are left in the World Cup?* — and the realization that the answer changes every few days.

## What it does

- **Live club ranking** — every tracked player is tied to a national team. When a nation is eliminated, its players fade out, the counts recompute, and the table re-sorts on the spot.
- **Shirt tally** — each club's row is a run of little shirts in club colors: solid for current players, hollow for former ones, faded for the eliminated.
- **Combined / Current / Former modes** — flip the lens and watch the ranking change (Arsenal tops current, Dortmund tops former).
- **The La Masia rule** — a toggle for the one genuine judgment call: whether Barcelona academy graduates who never made the first team (Cucurella, Grimaldo, Riad, Muñoz) count as "former" players. Strict = 12, loose = 16.
- **Auto-generated fixtures** — "Next up" and "Latest results" are built from the live feed, listing the tracked players in each match, with an automatic *"one side of BVB exits here"* flag whenever a club has players on both sides.
- **Graceful fallback** — if the feed is unreachable, the app falls back to a verified snapshot (July 9, 2026 — quarter-final stage) instead of a blank page, and says so.

## Data

- **Live results:** [TheSportsDB](https://www.thesportsdb.com/) free API (no key required). Fetched on load, every 10 minutes, and whenever the tab regains focus.
- **Squad and career data:** compiled and verified manually against official 26-man squad lists (July 9, 2026).

### Methodology

- **"Former"** means a genuine first-team spell — loans included, marginal spells marked with °.
- Players count for **every club where they earned it**, so club totals overlap by design (De Bruyne is ex-City *and* ex-Chelsea; Courtois appears three times).
- Rankings count only players whose nations are still alive; eliminated players stay visible but dimmed.
- Penalty shootouts are the weak spot of free feeds (a draw on the scoreboard hides the winner) — the app resolves them by checking who appears in the next round, and flags the result as unclear until then.

## The eight clubs

Manchester City · Atlético Madrid · Paris Saint-Germain · Barcelona · Chelsea · Arsenal · Real Madrid · Borussia Dortmund

## Running it

It's one HTML file with zero dependencies and no build step.

- **Locally:** open `index.html` in any browser.
- **Deployed:** hosted on Netlify, auto-deploys on every commit to `main`.
- **On iPhone:** open the site in Safari → Share → **Add to Home Screen** for a fullscreen, app-like experience.

## Tech

- Vanilla HTML/CSS/JS — no framework, no build, no tracking, no cookies.
- FLIP animations for live re-ranking, `prefers-reduced-motion` respected.
- Barlow / Barlow Condensed via Google Fonts; everything else is hand-rolled.

## Updating the squads

All data lives in two structures at the top of the `<script>` block in `index.html`:

- `CLUBS` — each club's current / former (and Barcelona's `academy`) player lists.
- `TEAM` — the tracked nations and their feed names.

Edit, commit, and Netlify redeploys in seconds. The next World Cup is a copy-paste away.

---

*Squad data verified July 9, 2026. Not affiliated with FIFA or any club — just a fan tracing shirts.*
