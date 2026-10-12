# DekaPulls Studio website

Buildless, responsive English one-page website for GitHub Pages.

## Current status

- Website source is prepared. Publication and domain registration are separate steps.
- Contact email is not created yet; the page deliberately says “Company email coming soon.”
- Suggested future address: `hello@dekapulls.com` (not provisioned or verified).
- No external fonts, JavaScript dependencies, analytics, or build step.

## Publish on GitHub Pages

1. Sign in as `BlackHumbleCow` and create a public repository named `dekapulls-site` (or use another dedicated repository).
2. Upload this folder's CONTENTS into the repository root: `index.html`, `styles.css`, `favicon.svg`, `CNAME`, `.nojekyll`, and this README. Do not upload the parent Project MRG folder.
3. Open repository **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, branch **main**, folder **/(root)**, then **Save**.
5. Set **Custom domain** to `dekapulls.com` and save BEFORE pointing DNS at GitHub Pages. The included `CNAME` file contains this domain for branch deployment.
6. Add the DNS records below through the provider managing `dekapulls.com`.
7. After the DNS check and certificate provisioning finish, enable **Enforce HTTPS**. This can take up to 24 hours.

Domain registration must be completed separately if you do not already own `dekapulls.com`. GitHub Pages does not register this domain.

## DNS records

Recommended TTL: Auto or 3600 seconds. `@` means the root domain `dekapulls.com`.

| Type | Host | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | blackhumblecow.github.io |

Optional IPv6 records:

| Type | Host | Value |
| --- | --- | --- |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |

The `www` CNAME target has no `https://` and no repository path. With `dekapulls.com` configured as the custom domain, GitHub redirects `www.dekapulls.com` to it.
Replace conflicting web-hosting records for `@` and `www`; preserve unrelated DNS records, especially email MX/TXT records. Do not add a wildcard record.

GitHub recommends verifying domain ownership in account **Settings → Pages**. Add the exact TXT name and token GitHub supplies; do not guess the verification token.

## Company email

GitHub Pages provides web hosting, not an email inbox. A custom-domain mail provider or forwarding service must be configured separately.

1. Register/own `dekapulls.com`.
2. Choose a full email provider for sending and receiving, or a forwarding service for receiving into an existing inbox. Forwarding alone does not necessarily allow sending as the company address.
3. Add the MX/TXT/DKIM records supplied by that provider. These are separate from the website A/CNAME records above.
4. Create and test the chosen address.
5. In `index.html`, replace the `email-pending` paragraph in the contact section with, for example:

```html
<a class="email-link" href="mailto:hello@dekapulls.com">hello@dekapulls.com <span aria-hidden="true">↗</span></a>
```

Use the actual confirmed address, not the example, if different.

## Local preview

Open `index.html` directly, or run `python -m http.server 4173 --bind 127.0.0.1` from this directory and visit `http://127.0.0.1:4173`.

## Sources

- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages

DNS values checked on October 13, 2026.
