# magicMCP — website

Marketing site for **magicMCP**, a Model Context Protocol connector that helps AI
assistants find the right way to buy products at no extra cost to the user.

Live: https://magicmcp.xyz

## Stack

Plain static site — no build step.

- `index.html` — landing page
- `privacy.html` — privacy policy + affiliate disclosure
- `styles.css` — all styling (editorial-corporate: serif display + Inter body)
- `main.js` — copy-to-clipboard + current year
- `favicon.svg`, `*.png` — icons and Open Graph image
- `vercel.json` — clean URLs, cache + security headers

## Local preview

```bash
npx serve .       # or: python3 -m http.server 8000
```

## Deploy

Hosted on Vercel. Pushing to `main` triggers a production deploy automatically.

## Regenerating icons / OG image

Sources live in `favicon.svg` and `assets/og.svg`. On macOS (no extra tooling):

```bash
TMP=$(mktemp -d)
qlmanage -t -s 512  -o "$TMP" favicon.svg
sips -z 32 32   "$TMP/favicon.svg.png" --out favicon-32.png
sips -z 180 180 "$TMP/favicon.svg.png" --out apple-touch-icon.png
sips -z 192 192 "$TMP/favicon.svg.png" --out icon-192.png
sips -z 512 512 "$TMP/favicon.svg.png" --out icon-512.png
qlmanage -t -s 1200 -o "$TMP" assets/og.svg
sips -c 630 1200 "$TMP/og.svg.png" --out og.png
rm -rf "$TMP"
```
