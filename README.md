# Wandering Qingdom

A minimal, no-tracking starter for personal blogs and weekly notes built with Astro 5 and Tailwind CSS 4.

## Features
- Markdown content via Astro Content Collections stored under `content/blog` and `content/weekly`.
- Tailwind 4 + `@tailwindcss/typography` and preloaded Inter/Anton/Lato fonts for crisp typography.
- Shared layout with sensible SEO meta, Shiki code highlighting (GitHub Dark), and external-link hardening (`noopener`, `noreferrer`, `nofollow`).
- Reusable `Social` component (GitHub, X, email, optional WeChat QR modal) and badge-style `Menu` with avatar + nav links.
- Date-sorted list views and clean post pages powered by a small helper in `src/utils/content.ts`.
- Automatic sitemap generation; static output suitable for any static host.

## Tech Stack
- Astro 5.11
- Tailwind CSS 4 (`@tailwindcss/vite`, `@tailwindcss/typography`)
- date-fns
- rehype-external-links

## Requirements
- Node.js 18+
- pnpm (recommended) or npm/yarn

## Quick Start
```bash
pnpm install
pnpm dev
# visit http://localhost:4321
```

## Scripts
- `pnpm dev` - start dev server
- `pnpm build` - production build to `dist/`
- `pnpm preview` - preview the build locally

## Project Structure
```
.
├─ public/                 # Static assets (favicons, manifest, robots, avatar)
├─ content/                # Your markdown posts
│  ├─ blog/
│  └─ weekly/
├─ src/
│  ├─ assets/              # SVG icons
│  ├─ components/          # Menu, Social, Footer, List
│  ├─ layouts/             # Shared page shell + meta
│  ├─ pages/               # /, /blog, /weekly, and post routes
│  ├─ styles/              # Tailwind setup + global tweaks
│  └─ utils/               # Content sorting helper
├─ src/content.config.ts   # Content collections + schema
├─ astro.config.mjs        # Astro + sitemap + rehype config
├─ package.json
└─ tsconfig.json
```

## Content Model
Defined in `src/content.config.ts` (collection key: `post`). Frontmatter for each markdown file:

```md
---
title: Example Post          # string, required
date: 2025-01-01             # date, required
description: Short summary.  # string, required
tags: [note, learning]       # string[], optional
---

Markdown body here.
```

Place files under:
- `content/blog/my-post.md`
- `content/weekly/issue-1.md`

Dates are timezone-shifted by 8 hours to display consistently.

## Customization Tips
- **Site URL**: set `site` in `astro.config.mjs` for correct sitemap/meta.
- **SEO defaults**: adjust title/description/keywords in `src/layouts/Layout.astro`.
- **Social links**: pass props in `src/components/Social.astro` (supports GitHub, X, email, `wechatQrSrc` for modal QR).
- **Menu badge & avatar**: update `title` prop and `public/avatar.png`.
- **Styling**: tweak fonts/themes in `src/styles/global.css`; Tailwind 4 is already configured.
- **Favicons & manifest**: replace assets in `public/` and update `manifest.json` if needed.

## Build & Deployment
```bash
pnpm build
pnpm preview
```
Outputs static files in `dist/`. Deploy to Vercel, Netlify, GitHub Pages, Cloudflare Pages, or any static host.

## License
MIT License. See `LICENSE`.
