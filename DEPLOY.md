# Deployment Runbook

This is the deployment record for **微光原 · Shimmer Meadow**. It is intentionally written for a future agent session.

## Current URLs

| Purpose | URL |
| --- | --- |
| Vercel production | https://quick-olive-qfob7lc.vercel.app/ |
| GitHub repository | https://github.com/YI260602/shimmer-meadow |
| GitHub Pages backup | https://yi260602.github.io/shimmer-meadow/ |
| Vercel Analytics | Project → Analytics |

Vercel team/scope: `vega-shade` (Hobby)
Vercel project: `quick-olive-qfob7lc`
Git branch used by both hosts: `main`

## Architecture

```
local shimmer-meadow/
        │ git push origin main
        ▼
GitHub repository ──────► Vercel (Git integration, production deploy)
        │
        └───────────────► GitHub Pages (backup, main / root)
```

- No build command is needed. The site is plain HTML + inline CSS/JS.
- Three.js loads from a CDN, so opening the HTML still needs a network connection.
- GitHub Pages must stay enabled from the `main` branch root; `.nojekyll` is committed.
- Vercel is connected to the GitHub repo. A push to `main` triggers a production deployment automatically.

## Normal update flow

```bash
cd "/Users/vega/Desktop/DeepSeek harness/shimmer-meadow"
# edit index.html
node --check /dev/null  # not applicable; validate the page in a browser
git add .
git commit -m "feat: describe change"
git push origin main
```

Then verify:

```bash
curl -s -o /dev/null -w "%{http_code}\n" https://quick-olive-qfob7lc.vercel.app/
curl -s -o /dev/null -w "%{http_code}\n" https://yi260602.github.io/shimmer-meadow/
```

## Analytics

- Provider: **Vercel Web Analytics**, enabled on the project.
- The head of `index.html` injects `/_vercel/insights/script.js` only on HTTP(S) hosts that are not `github.io` or localhost. This keeps GitHub Pages backup clean.
- The Vercel “Get Started” wizard may default to Next.js instructions. For this plain-HTML project those steps are not used; the HTML snippet above is the correct integration.
- The Analytics dashboard can take a short time to show the first visitor after the page is opened with JavaScript enabled.

## If deployment has to be set up again

1. Push the folder to a public GitHub repository.
2. In Vercel: **Add New → Project → Import Git Repository**, choose the repo, framework preset **Other**, no build command, root directory `/`.
3. Connect the Git repository in project settings if not already connected.
4. Add the HTML analytics snippet if enabling Web Analytics (see above).
5. Optionally enable GitHub Pages: Settings → Pages → Deploy from branch → `main` → `/`.

Do not use an anonymous temporary deployment unless the user explicitly accepts that it must be claimed within 60 minutes.

## Account/UI notes

- Vercel’s GitHub App is installed for this account; future imports should show the repository automatically.
- The Vercel deployment owner is `yi260602`, team `vega-shade`.
- Browser-only actions (2FA, GitHub authorization, claim links, DNS) require the user; ask for a screenshot rather than guessing.
- Never commit `.vercel/`, tokens, 2FA codes, or claim links.
