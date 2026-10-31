# Hasp Vault — website

Live at **https://haspvault.com** (GitHub Pages, repo `bytedroid1/haspvault`,
custom domain set by `CNAME`; the old `https://bytedroid1.github.io/haspvault/`
address forwards there).

## Pictures (`shots/`)

| File | What it is |
|---|---|
| `home.png` | The app screen inside the phone on the home page (the app's home screen, as an iPhone shows it). |
| `og.png` | The picture shown when someone shares a link to the site (1200 x 630). |
| `favicon.png` | The browser-tab icon: the app icon with rounded corners. |
| `apple-touch-icon.png` | The icon an iPhone uses when the site is added to the home screen; also the logo search engines see. |

They are drawn from the real app, the same way as the store pictures. From
`aurora_vault/`: `tool/store/render.sh web` (layouts in `store/src/web-hero.html`,
`og.html`, `web-icon.html`; see `aurora_vault/store/README.md`). The pages ask
for `favicon.png`, `og.png`, `apple-touch-icon.png`, the hero `home.png` and
`style.css` with `?v=1.5` (31 Oct 2026): raise the number when they change, so
browsers and link previews fetch the new ones. The pictures
they replaced are in `_archive/2026-10-15/website-old-pictures/`.

Static site for the app: landing page and blog. **The privacy policy, terms and
support page live on the studio site** (`/Users/st/bytedroid website`,
https://bytedroidstudio.com/apps/hasp-vault/privacy/, /terms/, /support/ — the
addresses both stores and the app link to). Since 31 Oct 2026 `privacy.html`,
`terms.html` and `support.html` here only forward there, and every link on the
site points straight at them: two copies had drifted (this site's policy still
said 3 Sep while the studio one was current). The last full copies are in
`_archive/2026-10-31-website-before-1.3.2/`.
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
https://bytedroid1.github.io/haspvault/app-ads.txt ❌ not found — wrong level
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

- The contact address on every page is `info@bytedroidstudio.com`. Play requires a
  working one.
- Re-read `privacy.html` against what the app actually does at each release. It
  was last brought up to date on 15 October 2026 for 1.3.0: optional Sync to the
  user's own iCloud or Google Drive, and what Google sign-in shares. The app has
  no ads any more (the ads SDK was removed), so the `app-ads.txt` notes above no
  longer matter; the file is harmless to keep.
- The date at the top of `privacy.html` and `terms.html` should be updated
  whenever their contents change.
