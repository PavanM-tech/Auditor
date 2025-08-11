# Run and deploy your AI Studio app

This contains everything you need to run your app locally.

## Run Locally

**Prerequisites:**  Node.js


1. Install dependencies:
   `npm install`
2. Set the `GEMINI_API_KEY` in [.env.local](.env.local) to your Gemini API key
3. Run the app:
   `npm run dev`

---

## Deploy to GitHub Pages

This project is configured to deploy as a static site to **GitHub Pages**.

### One-time repo setup
1. Push this project to a GitHub repo (default branch: `main`).
2. In **Settings → Pages**, set **Source** to "GitHub Actions".
3. In **Settings → Secrets and variables → Actions → New repository secret**, add:
   - `GEMINI_API_KEY` — your Gemini API key. **Important:** Client-side keys are visible in the JS bundle. Restrict this key by HTTP referrer and rotate if leaked.

### Deploy
Every push to `main` will build with Vite and publish the `dist` folder to Pages via the provided workflow:
- `.github/workflows/gh-pages.yml`

### Local build for Pages
```
npm run build:pages
npx serve dist
```

### SPA routing
A `404.html` copy of `index.html` is included to handle client-side routing refreshes on GitHub Pages. A `.nojekyll` file bypasses Jekyll.

