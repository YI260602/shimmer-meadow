# Agent Notes (DeepSeek Harness)

This file is the durable project context for DeepSeek Harness sessions.

## Scope

- Project: **微光原 · Shimmer Meadow**
- Only this directory is in scope. Do not modify sibling project folders in the workspace.
- The deliverable is a standalone static scene: `index.html`.
- Keep it single-file where possible. Three.js is loaded from a CDN; do not add a build step.
- Read `README.md` for controls and `DEPLOY.md` for hosting/deployment.

## Current deployment

- GitHub: https://github.com/YI260602/shimmer-meadow
- Vercel: https://quick-olive-qfob7lc.vercel.app/
- GitHub Pages backup: https://yi260602.github.io/shimmer-meadow/
- Vercel Analytics is enabled. The HTML analytics snippet is inside `index.html`.

## Working rules

1. Do not commit `.vercel/` or any credentials/tokens.
2. Test `index.html` locally before pushing.
3. A normal update is: edit → commit → `git push origin main`. Vercel and GitHub Pages both redeploy from `main`.
4. After changes, check the Vercel URL still returns 200.
5. If a deployment or account action requires a browser login, 2FA, GitHub authorization, or Vercel claim, stop and ask the user instead of guessing.
6. Preserve the user’s scene requirements: no countdown, no HP, no enemies; walking, flying, candles, soft boundary, clouds, and the following child.

## New session prompt

If context is missing, ask the user to confirm they want work on `shimmer-meadow/`, then read `README.md` and `DEPLOY.md` before changing anything.
