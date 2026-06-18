# Gullak · Envelope Opening Animation

A tap-to-open envelope reveal with a **dynamic postcard**: the recipient,
message, and sender are filled in, the envelope opens, the postcard rises,
enlarges and tilts, the envelope settles behind it, and sparkles shimmer in.

Open `index.html` in any browser — no build step.

## Demo flow

1. A compose modal asks for **To**, **Message** (≤150 chars), **From**.
2. Hit **Preview animation** → tap the envelope → watch the reveal.

The modal is **demo-only**. In production the message comes from earlier
screens — just call `renderPostcard({ to, message, from })` and run `playReveal()`.

## How the dynamic text works

- Text is drawn over `empty.png` in **Playpen Sans** with a blue gradient ink.
- Sizes use container units (`cqw`) so text scales with the postcard.
- The message font auto-sizes by length via `messageTier()`:
  | Tier | Chars | Size |
  |------|-------|------|
  | Large | 0–60 | `5.4cqw` |
  | Medium | 61–110 | `4.4cqw` |
  | Small | 111–150 | `3.5cqw` |
- Ruled lines are generated in CSS (one per wrapped line) so they always fit.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The whole demo (HTML + CSS + JS) |
| `empty.png` | Blank postcard base (text drawn on top) |
| `Back.svg`, `Middle.svg`, `Bottom.svg` | Envelope body layers |
| `Top-Close.svg`, `Top-Open.svg` | Closed / open flap faces |
| `.nojekyll` | Serve all files as-is on GitHub Pages |
| `server.js` | Optional local server (`node server.js`) — not needed for Pages |

## Deploy to GitHub Pages

```bash
# from inside this folder
git add .
git commit -m "Update demo"
git branch -M main
git remote add origin https://github.com/<you>/<repo>.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Deploy from a branch → `main` / `(root)`**.
Live at `https://<you>.github.io/<repo>/`.

> GitHub Pages is case-sensitive — keep asset filenames exactly as referenced
> in `index.html` (e.g. `Top-Close.svg`).
