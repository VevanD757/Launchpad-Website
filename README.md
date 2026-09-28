# Launchpad Website

Static mirror of https://launchpad.stan.store — every page, style, font, image, video and animation, served as plain files (no build step).

## Pages

| URL | File |
| --- | --- |
| `/` | `index.html` |
| `/who` | `who.html` |
| `/where` | `where.html` |
| `/agenda` | `agenda.html` |
| `/apply` | `apply.html` |
| `/stan` | `stan.html` |
| `/legal/terms`, `/legal/privacy`, `/legal/cookies` | `legal/*.html` |

`vercel.json` turns on `cleanUrls`, so `/who` serves `who.html`.

## Assets

- `_next/static/` — the site's compiled CSS, JavaScript and fonts
- `img/`, `img-dither/`, `trail/`, `trail-dither/`, `video/`, `brand/` — images, the dithered image sets, the hover-trail frames and the hero video

## Changes from the original

- Images load directly from `img/…` instead of through Next.js's `/_next/image` optimizer (which doesn't exist on static hosting).
- Stan's Meta (Facebook) tracking pixels are removed.
- The apply form still posts to `/api/apply`, which doesn't exist here, so submissions fail until a real endpoint is connected.
- Moving between pages does a normal full page load instead of Next.js's in-app navigation. Pages look the same, just without the instant client-side transition.

## Run locally

```sh
npx serve .
```
