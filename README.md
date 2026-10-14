# Deploying GridConnection.co.uk on Cloudflare Pages

The site is static: `index.html`, `favicon.svg`, `robots.txt` and `_headers`. No build step.

## Before you deploy

- **Afternic link:** the buttons point to `https://www.afternic.com/domain/gridconnection.co.uk`. Check it opens your listing (or swap in your exact listing URL). It appears twice in `index.html`.
- **Escrow.com link:** the buttons point to `https://www.escrow.com/`. Swap in your own pre-filled transaction or "Buy It Now" link if you have one. Also appears twice.

## Option A: connect this GitHub repo (auto-deploys on every push)

1. Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
2. Pick `namefolio/gridconnection`, production branch `main`.
3. Framework preset: **None**. Build command: leave empty. Build output directory: `/`.
4. **Save and Deploy**, then add the custom domain as below.

## Option B: direct upload (no tools)

1. Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** → **Upload assets**.
2. Name the project `gridconnection`, drag in the four files, click **Deploy**.
3. In the project → **Custom domains** → add `gridconnection.co.uk` (and `www.gridconnection.co.uk`). If the domain's DNS is on Cloudflare, records are added for you; otherwise add the CNAME it shows at your registrar.

## Option C: Wrangler CLI

```sh
npm install -g wrangler
wrangler login
wrangler pages project create gridconnection --production-branch main
wrangler pages deploy . --project-name gridconnection --branch main
```

Run the deploy from inside this folder, then add the custom domain as in step 3 above.

Note: if the domain is parked at Afternic with their nameservers, pointing it to Cloudflare replaces the Afternic "for sale" parking page with this lander. That's usually what you want; the buy buttons still route to Afternic.
