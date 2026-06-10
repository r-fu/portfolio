# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A single-page personal portfolio site (Japanese language) built with plain HTML, CSS, and jQuery. There is no build system, package manager, linter, or test suite — files are edited directly and served as-is.

## Development

There are no build or test commands. To preview the site locally, serve the repo root with any static file server, e.g.:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`. Opening `index.html` directly in a browser also works.

## Structure

- `index.html` — the entire site: one page with four anchor-linked sections (`#Profile`, `#skill`, `#works`, `#contact`) plus the PhotoSwipe lightbox markup at the bottom of `<body>`.
- `css/style.css` — all custom styles, organized with section-divider comments. Responsive breakpoints are at `max-width: 767px` and `max-width: 540px`. `css/reset.css` is a CSS reset.
- `js/script.js` — custom behavior: smooth scrolling for anchor links, the fixed nav on scroll, and PhotoSwipe initialization.
- `css/photoswipe/` and `js/photoswipe/` — vendored PhotoSwipe lightbox library plus its setup script (`js/photoswipe/photoswipe_setup.js`). Treat the library files as third-party; only `photoswipe_setup.js` is meant to be customized.

## Key conventions

- External dependencies (jQuery 1.12.4, Bootstrap 4.1.3 CSS, Font Awesome 5.2, Google Fonts) are loaded from CDNs in `index.html` — there is no `node_modules` or local copy of these.
- Bootstrap is used for table styling (`table table-borderless`) in the SKILL section; layout otherwise uses custom classes (`card`, `card-wrapper`, `two-column-wrapper`, etc.) defined in `css/style.css`.
- Skill ratings are rendered with `rate rate1`–`rate rate5` classes inside `.rating` spans.
- WORKS entries are `<figure class="card">` blocks inside `.my-gallery`; the PhotoSwipe `<a>` wrappers are currently commented out, so thumbnails are not clickable lightbox items.
- Site content (profile text, skills, works) is written in Japanese; keep new user-facing content in Japanese to match.
- Commit messages in this repo are written in Japanese.
