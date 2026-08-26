# VoltichQ site — deploy checklist

## 1. Push to a GitHub repo
Create a new repo (e.g. `voltichq-site`) and push everything in this folder to the `main` branch, including the `CNAME` file at the root.

## 2. Enable GitHub Pages
Repo → **Settings → Pages** → Source: `main` branch, `/ (root)` folder → Save.

## 3. Point voltichq.com at GitHub Pages
At your domain registrar, set these DNS records (apex domain, no `www` needed since `CNAME` is set to `voltichq.com`):

**A records** (apex `@`) → point to all four of GitHub's IPs:
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**Optional — if you also want `www.voltichq.com` to work:**
```
CNAME  www  ldananjaya.github.io.
```
(GitHub Pages will redirect www → apex automatically once both are verified.)

DNS can take up to a few hours to propagate. Once it resolves, go back to **Settings → Pages** and check "Enforce HTTPS" — GitHub issues the SSL certificate automatically after the domain is verified.

## 4. Verify domain ownership in Play Console
Play Console checks domain ownership the same way Search Console does. Under **Play Console → Setup → Developer account → Advanced settings** (or wherever the "Website" field prompts verification), you'll likely need to either:
- Add a Google Search Console verification meta tag or DNS TXT record for `voltichq.com`, or
- Confirm ownership via an existing Search Console property.

Do this **before** re-submitting the Store listing "Website" field — that was the root cause of the original "not registered to you" error.

## 5. Update each app's Play Console listing
- **Block Puzzle: Classic** — update Website to `https://voltichq.com` and Privacy Policy URL to `https://voltichq.com/privacy/block-puzzle.html`. Once confirmed working, the old `ldananjaya.github.io/block-puzzle-classic-legal/` page can be taken down (or left as a redirect if you want to be safe for a while).
- **Word Search Explorer** — review `/privacy/word-search-explorer.html` against the app's actual current build (it's drafted assuming fully offline, no accounts, no ads — update it if that's changed) before using it in the closed-testing setup.
- **Sprout, Fruit Blast Shooter, Jewel Match Blast** — placeholder policy pages exist so the URLs are live now; replace the content with the real policy once each app is ready for testing.

## File structure
```
index.html
CNAME
assets/css/styles.css
privacy/block-puzzle.html
privacy/word-search-explorer.html
privacy/sprout.html
privacy/fruit-blast-shooter.html
privacy/jewel-match-blast.html
```
