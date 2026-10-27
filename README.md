# Your own Mochi 🧠

A tiny pet with a real [Cadence](https://github.com/muellerberndt/cadence) brain that learns as you play, running entirely in the browser. This template lets you host **your own customised Mochi** on GitHub Pages for free, with no build step.

> Based on [Mochi](https://github.com/muellerberndt/mochi) by Bernhard Mueller (MIT). Community template, not affiliated with Bernhard Mueller or Pragma Research.

## 1. Make your copy
Click **Use this template → Create a new repository** at the top of this page (or **Fork**). Give it a name, e.g. `my-mochi`, and make it **Public**.

## 2. Design your Mochi
Easiest: open the builder at `https://<your-username>.github.io/<repo>/build/` (after step 3), or any Build-a-Mochi page, design it, and click **Export JSON**.

Then in your repo, open **`mochi.config.json`** → ✏️ edit → paste in (or edit by hand) → **Commit changes**. This is the only file you need to touch.

```json
{
  "v": 1,
  "name": "Mochi",                      // up to 14 characters
  "coat": {                             // hex colours "#rrggbb"
    "back": "#9945FF", "mid": "#5A8FE0", "brow": "#14F195",
    "earBack": "#4f9fd6", "earFront": "#22e0a0", "ear": "#c9ffe9",
    "line": "#0d0a1a", "eye": "#0b0714", "blush": "#dc1fff", "mouth": "#2a0f4a"
  },
  "temperament": {                      // each -2 … 2 (0 = original)
    "appetite": 0, "energy": 0, "playful": 0, "cuddly": 0, "pace": 0
  },
  "start": {
    "autoCare": true,                   // feeder fills the bowl at dawn
    "skipNight": true,                  // nights pass faster
    "daySeconds": 360,                  // 240, 360 or 600
    "pack": ""                          // "" = default brain, or an id from web/brains/index.json
  }
}
```
(Real JSON has no `//` comments — they're just explanations here.) Invalid values are ignored and fall back to the defaults.

## 3. Turn on GitHub Pages
Repo **Settings → Pages → Build and deployment → Source: Deploy from a branch**, Branch: **`main`**, folder **`/ (root)`** → **Save**. After a minute your Mochi is live at
`https://<your-username>.github.io/<repo>/` (it opens `web/`). The builder is at `/build/`.

## 4. (Optional) Custom domain
1. Settings → Pages → **Custom domain**: enter e.g. `mymochi.com` → Save (GitHub adds a `CNAME` file for you).
2. At your domain registrar add DNS records: four `A` records for `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`, and a `CNAME` for `www` → `<your-username>.github.io`.
3. When the certificate is ready (minutes to a few hours), tick **Enforce HTTPS**.

## How customisation works
- **Coat/name** only change the drawing — the brain never sees its own coat, so it behaves exactly as trained.
- **Temperament** gently scales how fast needs rise (hunger/thirst, sleepiness, boredom, loneliness) and movement speed, ×0.7 to ×1.4. The brains were raised on the middle setting, so extremes may look a bit clumsier at first; it keeps learning as you play.
- Room, toys and food colours aren't customisable: the brain recognises them by colour.
- Order of priority on a visitor's browser: a share link (`?mochi=…`) → a design they saved in the builder → your `mochi.config.json` → built-in defaults.
- Each visitor's pet life is saved in their own browser (IndexedDB).

## Run locally
```
python3 -m http.server 8000
# open http://localhost:8000/web/
```
The first load fetches Python (Pyodide) from a CDN, so you need internet.

## Licence
MIT — see `LICENSE` (original copyright Bernhard Mueller) and `NOTICE.md` for credits. Keep both when you share your copy.
