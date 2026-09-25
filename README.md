# preston

Hero theme for XLiink creator profiles. One stylesheet, served from here, pulled
in by each profile's custom CSS field.

## Use

Two rules in the profile's custom CSS field. `@import` must be the first rule:

```css
@import url("https://moderatesoup.github.io/preston/shared/xliink-theme.css");

:root{
  --hero: url("<the profile photo's URL>");
}
```

Get the photo URL by uploading the photo in XLiink, then copying the image
address off the live profile. Nothing needs to be hosted here.

## Tuning

Override any of these in the `:root` block alongside `--hero`:

| Variable | Default | Effect |
|---|---|---|
| `--hero-ratio` | `4 / 5` | Hero shape. Taller: `3/4`, `2/3` |
| `--hero-max` | `520px` | Hero width cap |
| `--hero-focus` | `center 30%` | Crop focus. Higher %: shows lower |
| `--hero-fade` | gradient | Mask that melts the photo into the page |
| `--ink` | `#fff` | Text colour |
| `--page-bg` | `#000` | Page colour |

## Why it targets two DOM trees

XLiink renders the profile photo with two different components and picks one at
page load, not through CSS media queries — so a narrow load keeps the banner
tree even after the window widens.

- `.header-image-container > img.xliink-profile-image` — 16:9 banner
- `.justify-center.py-6 .relative > img` — rounded card

Both are styled unconditionally, so either load path renders the same. Only the
blurred backdrop is width-gated, since it is a desktop-only effect.

Verified against the live DOM 2026-09-19.

## Gemma Preston final site

This repo also serves the generated Gemma Preston landing page at the custom domain:

- https://gemmapreston.com/

Private source/generator files remain in `moderatesoup/preston-dev`; this public repo contains only deployable public assets.
