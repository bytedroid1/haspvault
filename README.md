# Hasp Vault — website

Static site for the app: landing page, privacy policy, terms, support.
No build step, no dependencies, no external requests — plain HTML and one CSS
file. Drop it on any static host.

The pages deliberately load nothing from a CDN and carry no analytics or
trackers. A privacy policy served from a page that calls out to three third
parties undermines its own point, and the app follows the same rule.

## Deploying on GitHub Pages

1. Create a repository, e.g. `hifazat-vault-site`.
2. Copy the contents of this folder into it (not the folder itself — `index.html`
   must sit at the repository root).
3. Push, then in the repo: **Settings → Pages → Source: Deploy from a branch →
   `main` / `(root)` → Save**.
4. After a minute the site is live at
   `https://<username>.github.io/<repo>/`.

The privacy policy URL for the Play Console listing is then:

```
https://<username>.github.io/<repo>/privacy.html
```

A `github.io` URL is perfectly acceptable to Google Play. A custom domain is a
presentation choice, not a requirement — you can add one later under
**Settings → Pages → Custom domain** without changing any of these files,
because every link here is relative.

## app-ads.txt — the one thing a project site cannot do

`app-ads.txt` authorises AdMob to sell your ad inventory, and crawlers only ever
look for it at the **root of a domain**:

```
https://example.com/app-ads.txt        ✅ found
https://user.github.io/repo/app-ads.txt ❌ not found — wrong level
```

So on a GitHub Pages *project* site it will not be picked up. Two ways round it:

- **User site** — name the repository `<username>.github.io`. The site is then
  served from the domain root and `https://<username>.github.io/app-ads.txt`
  works.
- **Custom domain** — once you own one, this file at its root works normally.

This is not urgent. Without `app-ads.txt` ads still serve; you simply lose the
advertisers who refuse unverified inventory, which costs revenue rather than
function. Set it up when the domain arrives.

## Before publishing

- Replace `alwinpatel3@gmail.com` throughout if you would rather use a dedicated
  support address than a personal one. It appears on the privacy, terms and
  support pages, and Play requires a working contact address.
- Re-read `privacy.html` against what the app actually does at release. It was
  written to match the app as of 31 July 2026 — in particular, it states that no
  analytics are collected and that the ads SDK only starts if the user taps the
  rewarded offer. If either changes, the policy must change with it.
- The date at the top of `privacy.html` and `terms.html` should be updated
  whenever their contents change.
