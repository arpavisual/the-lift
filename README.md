# The Lift

Static site, no build step on Vercel.

**Deploy:** New Project → upload this folder (or push it to GitHub and import) → Framework preset **Other** → leave Build Command and Output Directory empty → Deploy.

| File | Size | What it is |
|---|---|---|
| `index.html` | 9 KB | Page, loading dial, captions |
| `app.js` | 655 KB | The 3D experience (three.js r170, minified) |
| `car.glb` | 3.9 MB | The car. Replace it to update the car (see `PARTS.md`) |
| `sky.hdr` | 0.5 MB | CC0 sunset sky for reflections (Poly Haven "Venice Sunset") |
| `vercel.json` | | Caching |

Vercel compresses these automatically, so a visitor downloads about 2.5 MB in total.
