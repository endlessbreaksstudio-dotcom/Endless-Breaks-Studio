# Endless Breaks Studio — website

A one-page site for Endless Breaks Studio (ocean-inspired resin art). Plain HTML/CSS/JS, no build step, no dependencies to install — it's ready to upload as-is.

**Live at:** https://endlessbreaksstudio-dotcom.github.io/Endless-Breaks-Studio/

## What broke, and why this version fixes it

The version uploaded earlier had images sorted into a `photos/` folder and a `photos/detail/` subfolder. GitHub's web **Add file → Upload files** drag-and-drop doesn't reliably recreate that folder structure — depending on the browser, files dragged from inside a subfolder can land flat at the repo root instead of inside their folder. On top of that, the thumbnail and detail version of each piece shared the same filename (e.g. both were called `surfboard.webp`, one meant for `photos/`, one for `photos/detail/`), so once flattened, one silently overwrote the other. The result: `index.html` was asking for `photos/surfboard.webp`, but no such path existed anymore — hence no images.

This version has **no subfolders at all** — every file sits at the repo root with a unique name (detail crops are named things like `surfboard-detail.webp` instead of reusing `surfboard.webp`). That makes the upload immune to this problem regardless of browser or how the files get dragged in.

## Fix it — step by step

1. Go to your repo on GitHub (`endlessbreaksstudio-dotcom` → `Endless-Breaks-Studio`).
2. **Delete what's there now**, so nothing stale is left behind: select all the files in the repo's file list (click the first file, then shift-click the last, or use the checkbox at the top of the file list if your view has one), and delete them. If GitHub doesn't offer bulk-select in your view, it's fine to skip this — the new upload will overwrite same-named files either way, and any leftover `photos` folder with broken contents just won't be linked from anywhere.
3. Click **Add file → Upload files**.
4. Open this zip's `github-repo` folder on your computer and drag in **every file inside it individually selected** (select all of them at once — Ctrl+A on Windows or Cmd+A on Mac inside the folder — then drag that whole selection in one motion). There should be no subfolders this time, so there's nothing that can get flattened wrong: `index.html`, all the `.webp` files, `favicon-32.png`, `favicon-180.png`, `robots.txt`, `sitemap.xml` — 19 files total, all landing directly at the repo root.
5. Scroll down and click **Commit changes**.
6. Give it a minute or two, then reload the live site and hard-refresh (Ctrl+Shift+R / Cmd+Shift+R) to bypass any cached broken version. Images should now appear everywhere: hero, story, gallery thumbnails, spotlight, banner, and contact sections, plus the lightbox when you click a gallery piece.

Nothing about the domain or Google Search Console setup needs to be redone — same URL, same verification tag, still intact in `index.html`.

## Files

- `index.html` — the whole site
- `logo.webp`, `hero_photo.webp`, `sunset_waves.webp`, `coastline_sealions.webp` — shared background/hero images
- `surfboard.webp`, `waveplatter.webp`, `deepblue.webp`, `cuttingboard.webp`, `canvas.webp` — gallery thumbnails
- `surfboard-detail.webp`, `waveplatter-detail.webp`, `deepblue-detail.webp`, `cuttingboard-detail.webp`, `canvas-detail.webp` — larger images shown in the lightbox
- `favicon-32.png`, `favicon-180.png` — browser-tab icon and the icon used when someone saves the site to their phone's home screen
- `robots.txt`, `sitemap.xml` — tell search engines the site exists and it's OK to crawl it

## Getting found on Google

Already done for this URL — see the notes from your earlier setup. If you ever move to a custom domain, that will need re-verifying in Search Console as a separate property; ask Claude to rebuild this folder with the new domain first.

## Point a real domain at it (optional)

1. **Buy a domain** (e.g. `endlessbreaksstudio.com`) from a registrar — Cloudflare Registrar, Namecheap, and Squarespace Domains are common, usually $10-20/year.
2. In the repo's **Settings → Pages**, enter the domain under **Custom domain** and save — GitHub creates a `CNAME` file in the repo automatically.
3. At your registrar, add the DNS records GitHub's docs specify: four `A` records for the bare domain, or one `CNAME` record for `www`. The Pages settings page shows a "DNS check" status once records are correct (a few minutes to 24 hours).
4. Once the DNS check passes, turn on **Enforce HTTPS**.
5. Ask Claude to rebuild this folder with the new domain as `LIVE_URL`, then re-upload `index.html`, `robots.txt`, and `sitemap.xml`, and re-verify the new URL prefix in Search Console.

## Making future edits

Edit `index.html` directly (all CSS and JS are inline in the file), or ask Claude to make the change and re-export this folder. Since everything's flat now, re-uploading is just: select all the files in the folder, drag them into **Add file → Upload files**, commit. GitHub Pages redeploys automatically within a minute.
