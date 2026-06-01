# Hazel's Rescue Climb — PWA

A gentle 3-world climbing game. Installable on phones/tablets, plays offline, works with keyboard (desktop) and touch (mobile, landscape).

## Files
- `index.html` — the game (this is the entry point Vercel serves)
- `manifest.webmanifest` — PWA manifest (landscape-locked, fullscreen)
- `sw.js` — service worker (offline + installability)
- `icon-180.png`, `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` — app icons
- `vercel.json` — correct headers for the service worker + manifest

## Deploy to Vercel
Easiest (no build step needed — it's a static site):

1. Put all these files in one folder (the repo root).
2. Option A — drag & drop: go to vercel.com, "Add New… → Project", and drag the folder in.
   Option B — CLI: `npm i -g vercel` then run `vercel` in this folder and follow the prompts.
   Option C — Git: push the folder to a GitHub repo and "Import Project" on Vercel.
3. No framework, no build command, no output directory needed. Vercel serves `index.html` automatically.
4. Vercel gives you an `https://…vercel.app` URL. PWAs require HTTPS — Vercel provides it automatically.

## Install on iPhone / iPad (no App Store needed)
1. Open the Vercel URL in **Safari**.
2. Tap the **Share** button → **Add to Home Screen** → **Add**.
3. Launch it from the home-screen icon. It opens fullscreen with no Safari bars, and works offline.
4. Hold the device **sideways (landscape)** to play — a friendly "turn sideways" hint shows if held upright.

## Install on Android / Chrome
Open the URL → Chrome shows an "Install app" prompt (or use the ⋮ menu → "Install app").

## Difficulty
The start screen has a difficulty picker (remembered between visits):
- **🌸 Toddler** (default) — extra-bouncy jumps and a fast dash, so little ones can reach the top easily.
- **⭐ Kid** — a moderate boost.
- **🚀 Grown-up** — the original precision climb, unassisted.

Letter-game rewards still stack on top of whichever level you pick.

## Controls
- **Desktop:** arrows/A-D move, Space/↑/W jump (again for double jump), L/Shift dash. Bonus round: press the letter key (or click a tile).
- **Touch:** on-screen left/right + JUMP + DASH buttons (bottom corners). Bonus round: tap the matching letter tile.

## Notes
- Progress (which worlds are unlocked, earned skills) currently resets each session. If you want it to persist between launches, that needs a storage layer added — ask and it can be wired in.
- To update the game after deploying, bump the cache name in `sw.js` (e.g. `hazel-climb-v1` → `v2`) so devices fetch the new version.
