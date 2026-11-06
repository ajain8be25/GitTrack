# 🃏 Builder Card

A GitHub toolkit in a single HTML file. Make a collectible card for any GitHub user, discover cool repos and people by interest, and use a set of tools built for open source contributors.

Built with **HTML, CSS, JavaScript and React 18**. No build step, no install, no backend.

## Quick start

1. Download `index.html`.
2. Double-click it to open in Chrome, Edge, Firefox or Safari.
3. Type a GitHub username and press **Deal**.

> **Open it in your own browser, not inside a chat preview.** Previews usually block requests to `api.github.com`, so nothing loads.

You need an internet connection (GitHub API, React from cdnjs, Google Fonts).

## Features

### Card
- Profile card with avatar, bio, repos, stars and followers.
- Main languages bar (weighted by repo size and stars, forks ignored).
- Top repos and recent activity (last 8 public events).
- **Interest DNA:** topics inferred from the user's repos. Click a chip to find people with the same interest.
- **Rarity:** Common, Rare, Epic or Legendary by total stars, with a holo border for Epic and above.
- Save a builder, copy a share link (`index.html#u=username`), or jump to **Find similar**.

### Repo Radar
- Search any topic. Modes: **Top starred**, **Hidden gems** (5 to 300 stars, active in the last 30 days) and **Hot this fortnight**.
- Optional language filter.
- ALIVE / SLOW / DEAD badge from each repo's last push.
- Save repos for later.

### Find People
- Enter interests like `ai, rust` to find builders who own repos on those topics, ranked by how many interests they match.
- **Builders like @user:** uses someone's Interest DNA to find people with overlapping interests.

### Contribute (tools for open source contributors)
| Tool | What it does |
|---|---|
| **Issue Finder** | Open issues labeled good first issue, help wanted or docs. Only issues updated in the last 90 days with no assignee. Optional language filter and "0 comments" filter. |
| **Repo Score** | A 0 to 100 contributor-friendliness score from the contributing guide, code of conduct, issue templates, license, recent activity, PR merge rate, median time to merge and bus factor. |
| **PR Checklist** | Reads a repo's `CONTRIBUTING.md` and builds a tickable checklist (tests, lint, branch naming, sign-off, CLA, changelog). Copy it as markdown. |
| **My PRs** | Paste PR links to track open, merged or closed status. Refresh any time. |
| **Watchlist** | For up to 6 saved repos, shows the latest release and the number of open good first issues. |
| **Contributor Card** | A user's merged PRs in other people's repos, their top repos, and a level from Newcomer to Core contributor. |

### Saved
Saved repos and builders are listed in the **Saved** tab.

## Data and privacy

- All data comes from the public GitHub REST API.
- Saved repos, saved builders, tracked PRs and your optional token are stored only in your browser (`localStorage`). Nothing is sent anywhere else.
- Only public data is shown.

## Rate limits (important)

GitHub allows about **60 requests per hour** without a token, and search is limited to **10 requests per minute**. Results are cached in memory during a session to help.

If you see "rate limit hit":
1. Wait a minute and try again, or
2. Click **add token** in the footer and paste a GitHub personal access token (no scopes needed for public data). It is stored only in your browser. Only do this on your own machine.

## Limits and notes

- Interest DNA relies on repo topics, so users who never add topics may show no chips.
- Repo Score samples the last 30 closed PRs and top 10 contributors, so it is an estimate, not an audit.
- Maintainer response time is approximated by time to merge, not time to first reply.
- Contributor Card shows the total exactly, but the repo breakdown uses the 100 most recent merged PRs.
- GitHub's public events feed covers about the last 90 days.

## Customize

- **Colors:** edit the CSS variables at the top of the `<style>` block (`--hot`, `--sky`, `--lemon`, `--mint`).
- **Language colors:** edit the `LANG` map in the script.
- **Rarity thresholds:** edit the `rarity` function.
- **Score weights:** edit the `checks` array in `RepoScore`.

## Troubleshooting

| Symptom | Fix |
|---|---|
| Nothing loads | Open the file in your own browser and check the console (F12) |
| "No builder named…" | Check the username spelling |
| "Rate limit hit" | Wait a minute or add a token |
| Blank page | CDN scripts were blocked. Try another network or disable ad-block |
| Find similar says no topics | That user's repos have no topics. Try a topic search instead |

## Tech stack

HTML5 · CSS3 · JavaScript (ES2020) · React 18 (UMD, `React.createElement`, no JSX) · GitHub REST API · Google Fonts (Space Mono, Bowlby One)

## Ideas for next

Card Battle, Collab Match, PNG export of the card, dark mode, and a small backend for accounts and weekly digests.
