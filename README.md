# PS38 PTA donate page

A static page for donate.ps38pta.org. It has no build step and no server. Donations go through Stripe Payment Links.

## Files

- `index.html`: the page, with all CSS inline
- `logo.png`, `favicon.png`, `apple-touch-icon.png`: the logo, the browser-tab icon and the phone home-screen icon
- `CNAME`: only used by GitHub Pages

## Payment links

All five Stripe Payment Links are in `index.html`: one-time any amount, plus $10, $20, $50 and $100 a month. To change one, search the file for `donate.stripe.com`.

## Hosting (GitHub Pages)

The site lives at https://github.com/38ptabrooklyn/donate-static and is served by GitHub Pages.

1. In the repo, go to **Settings → Pages → Build and deployment → Deploy from a branch**, then choose `main` and `/ (root)`.
2. Under **Custom domain**, enter `donate.ps38pta.org`. The `CNAME` file in the repo already sets it.
3. In Namecheap, go to **Domain List → ps38pta.org → Advanced DNS** and add a record: Type `CNAME`, Host `donate`, Value `38ptabrooklyn.github.io`, TTL Automatic.
4. Once GitHub's DNS check passes and the certificate is issued, tick **Enforce HTTPS**.

To update the site, edit the files, then commit and push to `main`. Pages redeploys within a minute or two.

### Optional: send ps38pta.org to the donate page

In Namecheap Advanced DNS, add a **URL Redirect Record**: Host `@`, Value `https://donate.ps38pta.org`, Permanent (301). Add the same record for Host `www`.

## Stripe settings checklist (per Payment Link)

- **Payment methods:** turn on US bank account (ACH) along with cards and wallets.
- **Confirmation page:** show a thank-you message, or redirect back to `https://donate.ps38pta.org/?thanks`.
- **Receipt text:** add "Parent Teacher Association of PS 38 is a 501(c)(3) nonprofit, EIN 11-3596441. No goods or services were provided in exchange for this contribution."
- **Custom field (optional):** add "Child's class" or "In honor of".
- **Customer portal:** enable it under Settings → Billing → Customer portal so monthly donors can manage their own gifts. If you want, add the portal login link to the footer of `index.html`.
- **Nonprofit rate:** contact Stripe support to request discounted 501(c)(3) processing.
