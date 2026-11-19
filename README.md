# Greatij Bekoe — Portfolio

This repository contains Greatij Bekoe's static portfolio website and a small browser game. The site presents a CV-style profile, experience, projects, and contact links. The game is an endless runner based on waiting for a very long loading process.

## Contents

- **Portfolio:** [`Website/website-cv.html`](Website/website-cv.html)
- **Local run instructions page:** [`Website/run-website.html`](Website/run-website.html)
- **Game:** [`Game/index.html`](Game/index.html)
- **Root entry point:** [`index.html`](index.html), which redirects to the portfolio
- **CV source text:** [`Website/CV File`](Website/CV%20File)
- **Game notes:** [`Game/Game File`](Game/Game%20File)

## Run locally

No package installation, build tool, or framework is required. A modern browser is sufficient.

### Run the complete site

From the repository root, start a local HTTP server:

```bash
python3 -m http.server 8000
```

Open [http://localhost:8000/](http://localhost:8000/) in a browser. The root page redirects to the portfolio. The portfolio links to the game and to its own run instructions.

Stop the server with `Ctrl+C`.

If Python is unavailable, open [`Website/website-cv.html`](Website/website-cv.html) directly in a browser or use the VS Code Live Server extension. Serving the files over HTTP is recommended so every relative link behaves consistently.

### Run only the game

From the repository root:

```bash
python3 -m http.server 8001 --directory Game
```

Then open [http://localhost:8001/](http://localhost:8001/) and stop the server with `Ctrl+C` when finished.

## Game controls

- Select **Start running** to begin.
- Press **Space** or **Arrow Up** to jump.
- Tap or click the game canvas to jump on a touch device or with a mouse.
- Avoid the blocks for as long as possible.
- The current score and best score are shown below the game. The best score is stored in the browser's local storage.

## Project structure

```text
.
├── index.html
├── Game/
│   ├── index.html
│   └── Game File
├── Website/
│   ├── index.html
│   ├── website-cv.html
│   ├── run-website.html
│   └── CV File
└── .github/
    └── workflows/
        └── deploy-pages.yml
```

The project is intentionally dependency-free. The HTML files contain their own styles and scripts, so there is no `package.json`, compilation step, or generated output to maintain.

## Deployment

The workflow in [`.github/workflows/deploy-pages.yml`](.github/workflows/deploy-pages.yml) deploys the repository to GitHub Pages whenever changes are pushed to `main`. It can also be started manually from the repository's **Actions** tab.

The workflow uploads the repository root as the Pages artifact. GitHub Pages therefore serves [`index.html`](index.html), which redirects visitors to the portfolio in `Website/website-cv.html`. The final public URL is supplied by the GitHub Pages deployment; no fixed production URL is configured in this repository.

## Updating the site

1. Edit the relevant HTML file in `Website/` or `Game/`.
2. Open the appropriate local URL and test navigation, keyboard controls, touch/click controls, and responsive layout.
3. Keep links relative so the site works both locally and on GitHub Pages.
4. Push changes to `main` to trigger deployment.
