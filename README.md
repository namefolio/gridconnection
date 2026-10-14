# GridConnection.co.uk sales lander

A single static page (`index.html`) with no build step, ready for Cloudflare Pages.

## Before you deploy

Replace the two placeholder purchase links in `index.html` (search for `data-buy`; each appears twice):

| Button | Current value | Replace with |
|---|---|---|
| Buy on Afternic | `https://www.afternic.com/domain/gridconnection.co.uk` (placeholder, the standard Afternic listing URL pattern) | Your live Afternic Buy Now link |
| Buy via Escrow.com | `https://www.escrow.com/` (placeholder) | Your Escrow.com "Buy It Now" link for this domain |

## Deploy to Cloudflare Pages

Recommended, Git-connected: Cloudflare dashboard > Workers & Pages > Create > Pages > Connect to Git > pick `namefolio/gridconnection`. Framework preset: None. Build command: leave empty. Build output directory: `/`. Every push to `main` then redeploys.


Option A, drag and drop: Cloudflare dashboard > Workers & Pages > Create > Pages > Upload assets, and upload this folder.

Option B, command line:

```
npx wrangler pages deploy . --project-name gridconnection
```

Then add the custom domain: Pages project > Custom domains > Set up a domain > `gridconnection.co.uk` (and `www.gridconnection.co.uk`). If the domain's DNS is already on Cloudflare the records are added for you; otherwise point a CNAME at `gridconnection.pages.dev`.

## Files

- `index.html` the page (Google Fonts is the only external request)
- `favicon.svg` tab icon
- `_headers` basic security headers for Cloudflare Pages
- `robots.txt` allows indexing
