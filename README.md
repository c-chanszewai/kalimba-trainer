# Kalimba Trainer

A single-page web app for practicing kalimba songs. Play songs back, slow them
down, loop tricky passages, drill chord shapes, and **tap in your own rhythm**.
Fully offline once installed — no server, no accounts, no data leaves your device.

## Features

- **Songs as tab** — numbers `1`–`7` are tine positions, `^` = octave up,
  `( )` = played together, a dash inside a group separates melody from an
  accompaniment chord (e.g. `(6^ -46 1^)`), line breaks = phrases.
- **Playback** with adjustable tempo (30–150 bpm), melody / chords / both.
- **Loop** any passage (click two notes, or a phrase's ⟲) with an optional rest
  between repeats.
- **Chord hints & chord drill** for practicing the hand shapes.
- **Tap rhythm** — turn on *Tap rhythm*, then press **Space** (or **Tap**) once
  per note to set the timing. Playback then uses your tapped rhythm and the
  tempo slider scales it faster/slower. Untapped notes play at 1 beat.
- **Everything is saved** — your edited songs and tapped rhythms persist in the
  browser (localStorage), so you only tap a song once.
- **Edit tab** to paste/write your own songs; **Restore built-in** to undo.

## Run it locally

Just open `index.html` in a browser. (Offline caching via the service worker
only activates over http/https — see hosting below — but the app itself works
fine opened directly.)

## Host it on GitHub Pages (for your iPad)

1. Create a repo and push (from this folder):

   ```bash
   git init
   git add -A
   git commit -m "Kalimba Trainer PWA"
   gh repo create kalimba-trainer --public --source=. --push
   ```

   (Or create an empty repo on github.com, then `git remote add origin <url>`
   and `git push -u origin main`.)

2. On github.com: **Settings → Pages → Build and deployment →** Source:
   *Deploy from a branch*, Branch: `main` / `/ (root)`, **Save**.

3. Wait ~1 minute, then open the URL it gives you
   (`https://<your-username>.github.io/kalimba-trainer/`).

## Install it on the iPad (offline app)

1. Open the GitHub Pages URL in **Safari** on the iPad.
2. Tap the **Share** button → **Add to Home Screen** → **Add**.
3. Launch it from the home-screen icon. It opens fullscreen and works with no
   internet connection. Your songs and tapped rhythms are remembered on the
   device.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The whole app (HTML + CSS + JS inline) |
| `manifest.webmanifest` | PWA metadata (name, icons, theme) |
| `sw.js` | Service worker — caches the app for offline use |
| `icon-192.png` / `icon-512.png` / `icon-180.png` | App icons |

> Updating the app: after changing `index.html` (or any cached file), bump the
> `CACHE` version in `sw.js` (e.g. `kalimba-v1` → `kalimba-v2`) so installed
> copies fetch the new version.
