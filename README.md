edge-tgp . ff-wndnrch-googleAuth . chrome - halx

# metrocebu.github.io

Metro Cebu community site built with [Astro](https://astro.build).

## Deployments

This repo serves two separate destinations:

| URL | Source | How |
| :-- | :----- | :-- |
| TBU | `src/` (Astro build) | Vercel auto-deploys on push to `main` |
| [metrocebu.github.io](https://metrocebu.github.io) | `gh-pages-src/` (static HTML) | GitHub Actions deploys to `gh-pages` branch on push to `main` |

They are independent — editing `gh-pages-src/` does not affect the Vercel deploy, and editing `src/` does not affect the GitHub Pages site.

## Project Structure

```
/
├── gh-pages-src/        # Static site for metrocebu.github.io
│   └── index.html
├── .github/
│   └── workflows/
│       └── deploy-gh-pages.yml
├── public/
│   └── favicon.svg
├── src/
│   ├── assets/
│   ├── components/
│   │   └── Welcome.astro
│   ├── layouts/
│   │   └── Layout.astro
│   └── pages/
│       └── index.astro
└── package.json
```

## Running Locally

**Requirements:** Node.js >= 22.12.0

```sh
# Install dependencies
npm install

# Start the Astro dev server (http://localhost:4321)
npm run dev

# Preview the gh-pages static site (http://localhost:3000)
npm run serve:gh
```

You can run both at the same time in two separate terminals to preview each site independently.

## GitHub Pages Setup (one-time)

After the first push that triggers the workflow:

1. Go to the repo **Settings → Pages**
2. Under **Build and deployment**, set Source to **Deploy from a branch**
3. Set Branch to **`gh-pages`** and folder to **`/ (root)`**
4. Save — `metrocebu.github.io` will now serve from `gh-pages-src/`

The workflow only re-runs when files inside `gh-pages-src/` change, so unrelated commits to `main` won't trigger it unnecessarily.

## Commands

| Command              | Action                                      |
| :------------------- | :------------------------------------------ |
| `npm install`        | Install dependencies                        |
| `npm run dev`        | Start Astro dev server at `localhost:4321`  |
| `npm run build`      | Build production site to `./dist/`          |
| `npm run preview`    | Preview the Astro production build locally  |
| `npm run serve:gh`   | Serve `gh-pages-src/` at `localhost:3000`  |
| `npm run astro ...`  | Run Astro CLI commands (e.g. `astro check`) |
