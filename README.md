# Endless Breaks Studio — website

A one-page site for Endless Breaks Studio (ocean-inspired resin art). Plain HTML/CSS/JS, no build step, no dependencies to install — it's ready to upload as-is.

## Files

- `index.html` — the whole site
- `logo.webp`, `hero_photo.webp`, `sunset_waves.webp`, `coastline_sealions.webp` — shared background/hero images
- `photos/` — gallery thumbnails
- `photos/detail/` — larger images shown in the lightbox
- `favicon-32.png`, `favicon-180.png` — the browser-tab icon and the icon used when someone saves the site to their phone's home screen
- `robots.txt`, `sitemap.xml` — tell search engines the site exists and it's OK to crawl it

## Before you upload: set your real domain

`index.html`, `sitemap.xml`, and `robots.txt` all contain the placeholder `YOUR-DOMAIN-HERE` (6 spots total, all inside `index.html`'s `<head>`, plus one each in the other two files). Once you've picked and bought a real domain (see below), do a find-and-replace for `YOUR-DOMAIN-HERE` → your actual domain, e.g. `endlessbreaksstudio.com`, in all three files. This isn't required for the site to work — it just makes link previews (texting the link, sharing on Instagram) and search engines show the right URL. You can skip this step for now and come back to it once you own a domain.

## Put it on GitHub Pages (free hosting) — step by step

1. **Create a GitHub account** at github.com if you don't already have one (free).
2. **Create a new repository**: click the **+** in the top-right corner → **New repository**. Name it something like `endless-breaks-studio`. Keep it **Public** (GitHub Pages on a free plan requires a public repo). Don't check any of the "initialize with" boxes. Click **Create repository**.
3. **Upload the files**: on the new repo's page, click **Add file → Upload files**. Drag in *everything inside this folder* (not the folder itself — its contents: `index.html`, the `.webp` files, `robots.txt`, `sitemap.xml`, the `photos` folder, etc.) so `index.html` ends up at the root of the repo. Scroll down and click **Commit changes**.
4. **Turn on Pages**: go to the repo's **Settings** tab → **Pages** in the left sidebar. Under "Build and deployment," set **Source** to "Deploy from a branch," branch `main`, folder `/ (root)`. Click **Save**.
5. **Wait a minute or two**, then refresh that same Settings → Pages screen. GitHub will show a banner like "Your site is live at `https://<your-username>.github.io/endless-breaks-studio/`" — that's your real, public, working URL. Open it to confirm.

At this point anyone with that link can visit the site. It's not yet showing up in Google search results — see "Getting found in search" below for that.

## Point a real domain at it (optional but recommended)

1. **Buy a domain** (e.g. `endlessbreaksstudio.com`) from a registrar — Cloudflare Registrar, Namecheap, and Squarespace Domains are common, usually $10-20/year.
2. In the repo's **Settings → Pages**, enter the domain under **Custom domain** and save — GitHub creates a `CNAME` file in the repo automatically.
3. At your registrar, add the DNS records GitHub's docs specify (search "GitHub Pages custom domain DNS" or check the Pages settings page, which links directly to them): four `A` records if you're using the bare domain (`endlessbreaksstudio.com`), or one `CNAME` record if you're using `www.endlessbreaksstudio.com`. The Pages settings page shows a "DNS check" status once the records are set correctly (can take anywhere from a few minutes to 24 hours).
4. Once the DNS check passes, turn on **Enforce HTTPS** in the same settings screen (the certificate usually issues within an hour).
5. Come back and do the `YOUR-DOMAIN-HERE` find-and-replace mentioned above, then re-upload `index.html`, `robots.txt`, and `sitemap.xml`.

## Getting found in search

Having a URL doesn't put you in Google's results by itself — a couple extra (free) steps help:

1. **Google Search Console** (search.google.com/search-console) — add your site (the GitHub Pages URL or your custom domain), verify ownership (it walks you through this), and submit `sitemap.xml`. Google will start crawling and indexing the site, usually showing up in search within a few days to a couple weeks.
2. **Google Business Profile** (business.google.com) — for a maker/studio business this usually matters more than general SEO. It's what gets you found when someone nearby searches "resin art" or "custom ocean art," and it's free to set up.
3. **Link the site everywhere you already have a presence** — Instagram/TikTok/Pinterest bios, your email signature. Search engines treat those inbound links as a signal the site is real and worth ranking.

## Making future edits

Edit `index.html` directly (all CSS and JS are inline in the file), or ask Claude to make the change and re-export this same folder. Commit and push (or re-upload through **Add file → Upload files**, which lets you overwrite existing files) — GitHub Pages redeploys automatically within a minute of any push to the branch you configured.
