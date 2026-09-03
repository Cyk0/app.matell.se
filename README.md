# app.matell.se

Static hosting for small web apps, served by GitHub Pages at <https://app.matell.se>.

## How it's wired

| Piece | What it does |
| --- | --- |
| `index.html` | Landing page. Reads `apps.json` and lists every app. |
| `apps.json` | The index of apps. One entry per app. |
| `<slug>/index.html` | One folder per app. Becomes `https://app.matell.se/<slug>/`. |
| `CNAME` | Tells GitHub Pages the custom domain is `app.matell.se`. **Don't delete this.** |
| `.nojekyll` | Skips GitHub's Jekyll build step, so files publish exactly as committed. |
| `404.html` | Shown for unknown URLs. |

## Adding an app

1. Create a folder named after the URL you want, e.g. `roi-calculator/`.
2. Put an `index.html` in it (plus any CSS/JS/images it needs — relative paths only).
3. Add an entry to `apps.json`:

```json
{
  "slug": "roi-calculator",
  "name": "ROI Calculator",
  "description": "Works out payback period for a test programme.",
  "added": "2026-09-10"
}
```

4. Commit to `main`. GitHub Pages redeploys in under a minute.

## Rules of the road

- **Static only.** No server, no database, no build step. HTML, CSS and browser JavaScript.
- **No secrets.** Anything in this repo is readable by anyone who visits the site. Never commit an API key, token or password — even in a private repo, the published files are public.
- **Relative paths.** Inside an app, link to `style.css`, not `/style.css`, so the app also works if you move the folder.
- **Third-party libraries** can be loaded from a CDN (`https://cdnjs.cloudflare.com/...`) or committed into the app's folder.
