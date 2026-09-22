# Jeffrey Huang — Portfolio

Personal portfolio built with Astro and published at https://jehfoori.github.io.

## Development

Use Node.js 24 and pnpm 10.

```sh
pnpm install --frozen-lockfile
pnpm dev
```

## Publishing

Push changes to `main`. The GitHub Actions workflow builds the static site and deploys it to GitHub Pages. Run `pnpm build` locally to check changes before publishing.

Page content lives in `src/pages/`, shared layouts in `src/layouts/`, and styles in `src/styles/global.css`. Public reports, images, and the résumé are in `public/`.
