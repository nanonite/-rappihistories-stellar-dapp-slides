# Rappihistories — Slide Deck

A [Slidev](https://sli.dev) deck covering the architectural merits of the
Rappihistories / MediChain MVP. Aimed at a non-technical audience.

## Local development

```sh
pnpm install
pnpm dev
```

Then open the URL Slidev prints (usually `http://localhost:3030`).

## Build a static site

```sh
pnpm build
```

The static output lands in `dist/`. The GitHub Actions workflow at
`.github/workflows/deploy-slides.yml` runs this on every push to `master`
that touches this folder, and publishes the result to GitHub Pages.

## Enabling GitHub Pages (one-time)

After the first time the workflow runs, enable Pages in the repo:

1. Push this folder to GitHub.
2. In the repo, open **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **GitHub Actions**.
4. Re-run the `Deploy slides to GitHub Pages` workflow from the Actions tab.
5. The deck will be live at `https://<your-account>.github.io/<repo-name>/`.

## Room-brightness toggle

A persistent button at the top-right of every slide flips the deck between
a light scheme (for bright rooms) and a dark scheme (for dim rooms). The
toggle reads as the room type to switch into; click it whenever the room
changes.

## Editing the deck

All content lives in `slides.md`. Slidev hot-reloads in dev mode.

- `style.css` — overall theme overrides (fonts, colors, Mermaid styling).
- `global-top.vue` — global UI overlay (currently holds the brightness toggle).
- `components/BrightnessToggle.vue` — the toggle itself.
