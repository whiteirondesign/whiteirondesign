# White Iron Design — website

Custom furniture & steel fabrication, Boise, Idaho. Static site + a visual admin
panel for managing the gallery. Deploys to **whiteirondesign.com**.

## What's here

| Path | What it is |
|------|-----------|
| `index.html` | The whole website (HTML, CSS, and JS in one file) |
| `pieces.json` | The gallery contents — one entry per piece. Managed by the admin panel. |
| `images/` | Photos. `images/gallery/` holds admin-uploaded photos. |
| `admin/` | The private editor (Sveltia CMS) at `/admin` |
| `netlify.toml` | Hosting config (no build step) |
| `robots.txt`, `sitemap.xml`, `404.html` | Standard production files |
| `real-photos/` | Local scratch folder for raw photos (not published) |

## How the gallery works

The gallery on the site is built from `pieces.json`. You never edit that file by
hand — the admin panel does it for you.

## Adding a piece (the everyday workflow)

1. Go to **https://whiteirondesign.com/admin**
2. Log in
3. Open **Gallery → Gallery pieces**, click **Add Piece**
4. Upload a photo, type the name, pick a category, add details/description
5. Click **Publish** — it's live in about a minute

## Deploy checklist (one-time setup)

1. **GitHub** — create a free account, then create a repository and push this folder to it.
2. **Netlify** — create a free account, "Add new site → Import from GitHub", pick the repo. It publishes automatically.
3. In `admin/config.yml`, set `repo:` to `your-github-username/your-repo-name`.
4. Set up the admin login (GitHub OAuth) — see notes below.
5. **Domain** — in Netlify, add the custom domain `whiteirondesign.com`, then point the domain's DNS at Netlify (at your registrar).

### Admin login note
The `/admin` panel authenticates against GitHub so only you can edit. This uses a
GitHub OAuth app (a free, one-time setup). Walk through this step during deploy.

## Local preview

From this folder:

```
python3 -m http.server 8137
```

Then open http://localhost:8137
