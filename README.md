# Keys to the City

A Singapore property match-3 game, inspired by Candy Crush, by Patrick Low ([patricklow.sg](https://patricklow.sg)).

Swap and match homes along an MRT-style line of 10 stations, from a first flat in Tampines to a penthouse at Marina Bay. It runs as a Progressive Web App (PWA): install it on your phone's home screen and it opens full screen and plays offline.

## What's in the game

- **Pieces:** keys, HDB flats, coins, condos, trees and shophouses on an 8×8 board.
- **Specials:** match 4 for a Line Blaster, an L or T shape for a Bomb, and 5 in a row for a Red Dot that clears one whole type. Swap two specials together for a combo.
- **Goals:** reach a target score, collect pieces, and build on construction lots (hazard-striped lots need two matches). Some boards have gaps.
- **Extras:** 1–3 stars per level, saved progress, hints, auto-reshuffle, Hammer / Shuffle / +3 Moves boosters, sound effects and vibration with a mute button.

## Files

| File | What it does |
| --- | --- |
| `index.html` | The whole game: markup, styles and script in one file |
| `manifest.webmanifest` | App name, colours, icons and full-screen display for installing |
| `sw.js` | Service worker that caches the game so it works offline |
| `icons/` | App icon: `icon.svg` master, PNGs for Android, iOS and the browser tab |
| `vercel.json` | Headers so the service worker and manifest are served correctly |

There is no build step and no dependencies.

## Run it locally

Service workers need a real web server (not a double-clicked file):

```bash
npx serve .
# or
python3 -m http.server 8080
```

Then open http://localhost:8080 (or the port shown).

## Deploy on Vercel

1. In Vercel, choose **Add New → Project** and import this GitHub repo.
2. Framework preset: **Other**. Leave the build command and output directory empty (the site is served from the repo root).
3. Deploy. Every push to `main` redeploys automatically.

Vercel serves the site over HTTPS, which is required for installing a PWA.

## Install on your phone

- **Android (Chrome):** open the site, then tap **Install app** on the start screen, or use the ⋮ menu → **Install app**.
- **iPhone / iPad (Safari):** open the site, tap the **Share** button, then **Add to Home Screen**.

## Updating the game

After changing `index.html` or the icons, bump `VERSION` in `sw.js` (for example `ktc-v2`) so installed copies fetch the new files.

Progress and boosters are stored in the browser on each device (localStorage), so they don't sync between phones.
