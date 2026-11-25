# Publishing a new portfolio

A checklist for taking a new client from LinkedIn profile to a live domain.

## 1. Create the site folder

1. Copy `_starter/` to `sites/<first-last>/` (lowercase, hyphenated, e.g. `sites/jane-smith/`).
2. Build the page in `sites/<first-last>/index.html`. Keep it self-contained: CSS and JS inline, and images as data URIs or files in the same folder.
3. Replace the favicon set (`favicon.svg`, `favicon.ico`, `favicon-32.png`, `apple-touch-icon.png`, `icon-192.png`, `icon-512.png`) with the client's monogram. Sizes: 32, 180, 192 and 512 px squares; the `.ico` holds 16, 32 and 48.
4. Update `site.webmanifest` (name, short name, colours).
5. Add the project thumbnail as `previews/<first-last>.jpg` (1600×1000).
6. Add the client to `sites.json` and to the table in `README.md`.

## 2. Push

```bash
git add .
git commit -m "Add <Client Name> portfolio"
git push
```

The **Publish sites** action creates or updates the branch `deploy/<first-last>` containing only that site's files.

## 3. Connect the domain (one-time per client)

**Hostinger**

1. hPanel → **Websites → Add website** → use the client's domain.
2. Website → **Advanced → Git** → connect `fahimsahib19/client-portfolios`, branch `deploy/<first-last>`, install path `public_html`, and turn on **Auto deployment**.

**Domain registrar (e.g. Fasthosts)**

Keep the registrar's own nameservers and add two records:

| Type  | Host  | Value          |
|-------|-------|----------------|
| A     | `@`   | `31.97.238.16` |
| CNAME | `www` | `<domain>`     |

Remove any existing parking A/CNAME records for `@` and `www`. Do **not** change the nameservers as well. Use either the records or the nameservers, never both.

**SSL**

Once the domain loads (usually 1–4 hours), go to hPanel → **Security → SSL** and install the free certificate if it hasn't been issued automatically.

## 4. Check

- The site loads on `https://` with a padlock, and `www.` works.
- The favicon shows in the browser tab.
- It works on mobile.
- The footer shows "Website by Essential Studios".
