# Spice Timer — implementation plan

## Goal

Publish Spice Timer as a static experiment at
`https://lab.digitalspice.net/spice-timer/` and add it to the Lab tool cache.

Selecting the Lab tile must open a separate browser tab at:

```text
https://lab.digitalspice.net/spice-timer/?minutes=5
```

The timer should therefore load with five minutes selected, but it must not
start automatically.

## Implementation

1. Complete the desired edits to `spicetimer.html` in this repository.
2. Copy the finalized timer and its referenced local assets into the website
   repository at `apps/lab/spice-timer/`:
   - `index.html` (from `spicetimer.html`)
   - `favico.png`
   - `clock-ticking.mp3`
   - `time-is-up.mp3`
   - any additional asset introduced by the final HTML
3. Preserve the current relative asset references (for example,
   `./favico.png`); they will resolve correctly from that directory.
4. Add a fifth card in `apps/lab/index.html` for **SPICE TIMER**. Its anchor
   should use `/spice-timer/?minutes=5`, `target="_blank"`, and
   `rel="noopener"`.
5. Use the existing Lab styling and give the card the next sequential index.

## URL parameters supported by the current timer

| Parameter | Accepted value | Effect |
| --- | --- | --- |
| `minutes` | Integer `0`–`99` | Sets the initial minutes; default is `1`. |
| `autostart` | Exactly `true` | Starts the timer immediately. |

The Lab tile intentionally passes only `minutes=5`; it does not set
`autostart`.

## Deployment and verification

No infrastructure changes are expected: `lab.digitalspice.net` already
publishes `apps/lab/` through its existing S3/CloudFront deployment. A merge
to `main` that changes `apps/lab/**` triggers `deploy-lab`.

Before merging, verify:

- the new tile opens a separate tab;
- the destination URL is exactly `/spice-timer/?minutes=5`;
- the timer displays `05:00` and remains paused on load;
- the icon and audio files load from the new directory;
- direct navigation to `/spice-timer/` succeeds.

After merging, confirm the `deploy-lab` workflow completes and repeat those
checks on `https://lab.digitalspice.net`.
