# Endless Breaks Studio — website

A one-page site for Endless Breaks Studio (ocean-inspired resin art). Plain HTML/CSS/JS, no build step, no dependencies to install — it's ready to upload as-is.

**Live at:** https://endlessbreaksstudio-dotcom.github.io/Endless-Breaks-Studio/

## Buying pieces — Square checkout

Each of the 5 gallery pieces (and the Indigo Swell spotlight) now has a **Buy now** button that opens a Square-hosted checkout page: item price + a flat $35 shipping fee, with the buyer's shipping address collected. These are Square **Payment Links**, created directly against the studio's Square account:

| Piece | Price | Checkout link |
|---|---|---|
| Low Tide | $135 | https://square.link/u/Mwdm30HM |
| Whitewash | $135 | https://square.link/u/8lQsh58W |
| Indigo Swell | $135 | https://square.link/u/doqm2ghw |
| Driftline | $85 | https://square.link/u/itPfhwXV |
| Horizon Break | $500 | https://square.link/u/xfVlZ9zK |

**When a piece sells**, since these are one-of-one and never repeated, ask Claude to pull that piece from the gallery (or mark it "Sold") so people can't buy something that's gone — the Square link itself doesn't know inventory status, so this has to be done on the site manually.

**To change a price or the shipping fee**, ask Claude — it can update the existing Square payment link (price and shipping are editable after creation) and refresh the displayed price on the site to match, without needing to regenerate the link. You can also see and manage these links directly in the Square Dashboard under Payments → Payment Links.

## What broke earlier, and why this version is upload-proof

An earlier version organized images into a `photos/` folder and a `photos/detail/` subfolder. GitHub's web **Add file → Upload files** drag-and-drop doesn't reliably recreate that folder structure — files from inside a subfolder can land flat at the repo root instead. On top of that, the thumbnail and detail version of each piece shared the same filename, so once flattened, one silently overwrote the other. This version has **no subfolders at all** — every file sits at the repo root with a unique name — so that failure mode can't happen again.

## Files

- `index.html` — the whole site
- `logo.webp`, `hero_photo.webp`, `sunset_waves.webp`, `coastline_sealions.webp` — shared background/hero images
- `surfboard.webp`, `waveplatter.webp`, `deepblue.webp`, `cuttingboard.webp`, `canvas.webp` — gallery thumbnails
- `surfboard-detail.webp`, `waveplatter-detail.webp`, `deepblue-detail.webp`, `cuttingboard-detail.webp`, `canvas-detail.webp` — larger images shown in the lightbox
- `favicon-32.png`, `favicon-180.png` — browser-tab icon and the icon used when someone saves the site to their phone's home screen
- `robots.txt`, `sitemap.xml` — tell search engines the site exists and it's OK to crawl it

## Uploading changes

Since everything's flat with no subfolders, updating the live site is always the same: open this folder, select every file inside it (Ctrl+A / Cmd+A), drag the whole selection into your GitHub repo via **Add file → Upload files**, and click **Commit changes**. GitHub Pages redeploys automatically within a minute. A hard refresh (Ctrl+Shift+R / Cmd+Shift+R) clears any cached old version in your own browser.

## Getting found on Google

Already set up for this URL — Search Console verification and the sitemap submission are done. If you ever move to a custom domain, that counts as a new property and needs re-verifying; ask Claude to rebuild this folder with the new domain first.

## Point a real domain at it (optional)

1. **Buy a domain** (e.g. `endlessbreaksstudio.com`) from a registrar — Cloudflare Registrar, Namecheap, and Squarespace Domains are common, usually $10-20/year.
2. In the repo's **Settings → Pages**, enter the domain under **Custom domain** and save — GitHub creates a `CNAME` file automatically.
3. At your registrar, add the DNS records GitHub's docs specify: four `A` records for the bare domain, or one `CNAME` record for `www`. The Pages settings page shows a "DNS check" status once records are correct.
4. Once the DNS check passes, turn on **Enforce HTTPS**.
5. Ask Claude to rebuild this folder with the new domain as `LIVE_URL`, then re-upload and re-verify the new URL prefix in Search Console. Also ask Claude to update the 5 Square payment links' redirect-after-payment URL to the new domain — that's a separate live update on Square's side, not something baked into these static files.

## Making future edits

Edit `index.html` directly (all CSS and JS are inline in the file), or ask Claude to make the change and re-export this folder, then upload per "Uploading changes" above.
