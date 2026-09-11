# Spice Timer

A fullscreen countdown timer. No dependencies. One HTML file.

## Usage

Open `bigtimer.html` in any browser, or serve it locally.

**URL parameters:**

| Parameter | Example | Effect |
|---|---|---|
| `minutes` | `?minutes=5` | Set starting time (default: 1) |
| `autostart` | `&autostart=true` | Start immediately on load |

Example: `bigtimer.html?minutes=15&autostart=true`

## Features

- Giant countdown display with green glow
- +/− controls for minutes (1m) and seconds (5s)
- Progress bar
- Tab title counts down live; flashes "Time / Up" on completion
- **Play Gong at End** — plays `time-is-up.mp3` at zero
- **Play Ticking While Waiting** — plays `clock-ticking.mp3` while running
- **Browser Notification** — optional, requests permission on toggle

## Audio files

Drop these alongside `bigtimer.html`:

- `time-is-up.mp3` — played at zero (falls back to Web Audio beeps if missing)
- `clock-ticking.mp3` — looped while timer runs

## License

MIT
