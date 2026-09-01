# Endless Breaks Studio — website

A one-page site for Endless Breaks Studio (ocean-inspired resin art). Plain HTML/CSS/JS, no build step, no dependencies to install — it's ready to upload as-is.

**Live at:** https://endlessbreaksstudio-dotcom.github.io/Endless-Breaks-Studio/

## Files

- `index.html` — the whole site
- `logo.webp`, `hero_photo.webp`, `sunset_waves.webp`, `coastline_sealions.webp` — shared background/hero images
- `photos/` — gallery thumbnails
- `photos/detail/` — larger images shown in the lightbox
- `favicon-32.png`, `favicon-180.png` — the browser-tab icon and the icon used when someone saves the site to their phone's home screen
- `robots.txt`, `sitemap.xml` — tell search engines the site exists and it's OK to crawl it

`index.html`'s meta tags, `sitemap.xml`, and `robots.txt` are all already set to the live GitHub Pages URL above. If a custom domain gets pointed at this site later, those need updating to the new domain — ask Claude to rebuild the folder with the new URL, or edit the `LIVE_URL` line in `build_github.py` and re-run it.

## Getting found on Google

1. Go to **search.google.com/search-console** and sign in with the Google account tied to this site (this part has to happen in your own browser — it's your account).
2. Click **Add property**, choose the **URL prefix** option (not "Domain" — that one's only for custom domains you own via DNS), and paste in: `https://endlessbreaksstudio-dotcom.github.io/Endless-Breaks-Studio/`
3. Verify using the **HTML tag** method — `index.html` already has the verification meta tag baked in (`google-site-verification`), so once this file is uploaded you can just click **Verify** in Search Console right away.
4. After verifying, go to **Sitemaps** in the left sidebar, and submit `sitemap.xml`.
5. That's it — Google will start crawling. It typically takes anywhere from a few days to a couple weeks for pages to actually show up in search results, and you can check progress anytime under **Pages** in Search Console.

For local/maker-business discovery (often more useful than general search), also set up a **Google Business Profile** at business.google.com — free, and it's what shows up when someone nearby searches "resin art" or similar.

## Put it on GitHub Pages (free hosting) — step by step

1. **Create a GitHub account** at github.com if you don't already have one (free).
2. **Create a new repository**: click the **+** in the top-right corner → **New repository**. Name it something like `endless-breaks-studio`. Keep it **Public** (GitHub Pages on a free plan requires a public repo). Don't check any of the "initialize with" boxes. Click **Create repository**.
3. **Upload the files**: on the new repo's page, click **Add file → Upload files**. Drag in *everything inside this folder* (not the folder itself — its contents: `index.html`, the `.webp` files, `robots.txt`, `sitemap.xml`, the `photos` folder, etc.) so `index.html` ends up at the root of the repo. Scroll down and click **Commit changes**.
4. **Turn on Pages**: go to the repo's **Settings** tab → **Pages** in the left sidebar. Under "Build and deployment," set **Source** to "Deploy from a branch," branch `main`, folder `/ (root)`. Click **Save**.
5. **Wait a minute or two**, then refresh that same Settings → Pages screen. GitHub will show a banner like "Your site is live at `https://<your-username>.github.io/<repo-name>/`" — that's your real, public, working URL.

## Point a real domain at it (optional)

1. **Buy a domain** (e.g. `endlessbreaksstudio.com`) from a registrar — Cloudflare Registrar, Namecheap, and Squarespace Domains are common, usually $10-20/year.
2. In the repo's **Settings → Pages**, enter the domain under **Custom domain** and save — GitHub creates a `CNAME` file in the repo automatically.
3. At your registrar, add the DNS records GitHub's docs specify (search "GitHub Pages custom domain DNS," or the Pages settings page links directly to them): four `A` records for the bare domain, or one `CNAME` record for `www`. The Pages settings page shows a "DNS check" status once records are set correctly (a few minutes to 24 hours).
4. Once the DNS check passes, turn on **Enforce HTTPS** in the same settings screen.
5. Ask Claude to rebuild this folder with the new domain as `LIVE_URL`, then re-upload `index.html`, `robots.txt`, and `sitemap.xml` — and re-verify the new URL prefix in Search Console (step 2 above), since Google treats a domain change as a different property.

## Making future edits

Edit `index.html` directly (all CSS and JS are inline in the file), or ask Claude to make the change and re-export this folder. Re-upload through **Add file → Upload files** (it lets you overwrite existing files) — GitHub Pages redeploys automatically within a minute.
