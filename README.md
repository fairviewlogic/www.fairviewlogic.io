# www.fairviewlogic.io

Fairview Logic company site.

Built with [Hugo](https://gohugo.io/) on the [Hugoplate](https://github.com/zeon-studio/hugoplate) starter template (Hugo + Tailwind CSS v4).

## Prerequisites

- Hugo Extended >= 0.158
- Node >= 22
- Go >= 1.24 (used by Hugo Modules internally)

## Develop

```sh
npm install     # one-time, installs Tailwind toolchain
npm run dev     # local server on http://localhost:1313
```

## Build

```sh
npm run build   # produces ./public/
```

## Maintenance mode (current state)

The site is currently a placeholder — only the homepage and a matching 404 page render. Ingredients:

- `hugo.toml` sets `disableKinds = ["page", "section", "taxonomy", "term", "RSS", "sitemap"]` — Hugo skips every kind except `home` and `404`.
- `layouts/index.html` is a self-contained maintenance page (inline SVG logo, inline CSS, no theme chrome).
- `layouts/404.html` serves the same content — anyone hitting a subpage during maintenance mode gets the placeholder instead of a stark 404.

Result: 7-page build instead of Hugoplate's default ~90.

### To relaunch the real site

Reverse the three ingredients above:

1. Delete the `disableKinds = [...]` line from `hugo.toml`.
2. Delete `layouts/index.html`.
3. Delete `layouts/404.html`.

Hugoplate's default homepage + subpages come back automatically.

### On the double `<title>` in the maintenance page source

`view-source:` on the homepage shows two `<title>` elements: the HTML page title (`Fairview Logic`) and a second one *inside* the inline SVG (`logo`). The SVG's `<title>` is the accessible name for the graphic — screen readers announce it when describing the image. Browsers ignore it for the page title. Both are correct and intentional.
