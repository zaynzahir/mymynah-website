## Cursor Cloud specific instructions

This is a static marketing website for "My Mynah" (an AI speech coach iOS app). There is no build step, no backend, no database, no tests, and no linter configured.

### Running the dev server

```
npm run preview
```

This starts `npx serve . -l 3000` which serves the static files on `http://localhost:3000`. All three pages are plain HTML:

- `/` — main landing page (`index.html`)
- `/privacy/` — privacy policy (`privacy/index.html`)
- `/terms/` — terms of service (`terms/index.html`)

### Notes

- Tailwind CSS and Google Fonts are loaded from CDNs; no local CSS build is needed.
- There are no automated tests, linting, or CI configured in this repo.
- `DEPLOY.md` documents the GitHub Pages + Squarespace DNS deployment process.
- The `CNAME` file pins the custom domain `mymynah.com` for GitHub Pages.
