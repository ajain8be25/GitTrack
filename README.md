# 🃏 GitTrack

Type a GitHub username and get a collectible, trading-card style profile: top repos, main languages and recent activity.

Built with **HTML, CSS, JavaScript and React 18** in a single file. No build step, no install.

## Features

- **Profile card**: avatar, name, bio, repo/star/follower stats and a fun "builder class" title (e.g. *Veteran · Python Wrangler*).
- **Main languages**: stacked bar and legend. Languages are weighted by repo size plus stars, and forks are ignored.
- **Top repos**: your four most-starred original repos, linked to GitHub.
- **Recent activity**: last 8 public events (push, PR, issue, star, fork, release…) with relative timestamps.
- **Neo-brutalist UI**: paper texture, thick borders, hard shadows, and a 3D tilt effect on hover.
- **Friendly errors**: unknown user, rate limit and network problems each show a clear message.

## How to run

1. Download `builder-card.html`.
2. Double-click it to open in Chrome, Edge, Firefox or Safari.
3. Enter a GitHub username (with or without `@`) and press **Deal**.

> **Important:** open the file in your own browser, not inside a chat preview or sandbox. Those environments often block requests to `api.github.com`, so the card never loads.

An internet connection is required (for the GitHub API, React and fonts).

## How it works

| Piece | Source |
|---|---|
| Profile | `GET /users/{username}` |
| Repos and languages | `GET /users/{username}/repos?per_page=100&sort=pushed` |
| Activity | `GET /users/{username}/events/public?per_page=8` |

All three calls run in parallel using the public, unauthenticated GitHub REST API. React and Babel load from cdnjs, and JSX is compiled in the browser.

## Limits and notes

- Unauthenticated GitHub API requests are limited to about **60 per hour per IP**. If you hit the limit, wait and retry.
- Only the 100 most recently pushed repos are counted, and private repos or activity are never shown.
- GitHub's public events feed only covers roughly the last 90 days, so quiet accounts may show no activity.
- Language percentages are a weighted estimate, not exact lines of code.

## Customize

- **Colors**: edit the CSS variables at the top of the `<style>` block (`--hot`, `--sky`, `--lemon`, `--mint`).
- **Language colors**: edit the `LANG` map in the script.
- **Number of repos or events**: change `.slice(0,4)` for repos and `per_page=8` for events.
- **Higher rate limit**: add an `Authorization: Bearer <token>` header to the `fetch` call. Only do this in a local copy, and never publish a file containing your token.

## Troubleshooting

| Symptom | Fix |
|---|---|
| Nothing happens when searching | Open the file in your own browser, then check the console (F12) |
| "No builder named…" | Check the username spelling |
| "Rate limit" message | Wait a few minutes, or use a token |
| Blank page | The CDN scripts were blocked. Try another network or disable ad-block |

## Tech stack

HTML5 · CSS3 · JavaScript (ES2020) · React 18 (UMD) · Babel Standalone · GitHub REST API · Google Fonts (Space Mono, Bowlby One)
