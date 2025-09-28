# Wandering Qingdom

A clean, minimal personal blog template built with Astro 5 and Tailwind CSS 4.

It ships with a simple content model, accessible typography, and zero personal data. Use it as a starting point for your own blog or weekly notes site.

## Features

- Minimal Astro setup with Tailwind 4 and `@tailwindcss/typography`
- Markdown content via Astro Content Collections (`content/blog`, `content/weekly`)
- Automatic sitemap generation (`@astrojs/sitemap`)
- Sensible SEO defaults in a shared layout
- Reusable `Social` component with optional links (GitHub, X, Email, WeChat QR)
- Clean list pages and post pages with date formatting
- No third-party analytics by default

## Tech Stack

- Astro 5
- Tailwind CSS 4
- date-fns

## Project Structure

```
.
├─ public/                # Static assets (served at site root)
├─ content/               # Markdown content (blog, weekly)
│  ├─ blog/
│  └─ weekly/
├─ src/
│  ├─ assets/            # SVG icons used by components
│  ├─ components/        # UI components (Menu, Social, Footer, List)
│  ├─ layouts/           # Shared page layout
│  ├─ pages/             # Astro pages (/, /blog, /weekly)
│  ├─ styles/            # Tailwind + global styles
│  └─ utils/             # Helpers (content list sorting)
├─ src/content.config.ts  # Content collections & schema
├─ astro.config.mjs       # Astro configuration
├─ package.json
└─ tsconfig.json
```

## Content Model

Content is defined in `src/content.config.ts` and loaded from the `content/` directory.

Frontmatter schema for posts:

```md
---
title: My First Post           # string (required)
date: 2025-01-01               # date (required)
description: A short summary.  # string (required)
tags: [note, learning]         # string[] (optional)
---

Markdown body goes here.
```

Add files into:

- `content/blog/your-post.md`
- `content/weekly/issue-1.md`

## Configuration

- `astro.config.mjs`: set your site URL
  ```js
  export default defineConfig({
    site: 'https://your-domain.com',
    // ...
  });
  ```
- `src/layouts/Layout.astro`: default `<title>`, description, and keywords
- `src/components/Social.astro`: pass only the links you want to show
  ```astro
  ---
  import Social from "../components/Social.astro";
  ---
  <Social
    github="https://github.com/yourname"
    x="https://x.com/yourname"
    email="you@example.com"
    wechatQrSrc="/static/wechat_qr.png"
  />
  ```
- `src/components/Menu.astro`: the circular badge uses the `title` prop (defaults to `WQ`)
  ```astro
  <Menu title="WQ" />
  ```

## Development

Prerequisites:

- Node.js 18+
- pnpm (recommended) or npm/yarn

Install dependencies and start the dev server:

```bash
pnpm install
pnpm dev
```

Open `http://localhost:4321` in your browser.

## Build & Preview

```bash
pnpm build
pnpm preview
```

The site is a static build by default and can be deployed to any static host.

## Deployment

- Vercel: import the repo, framework = Astro
- Netlify: use `pnpm build` and publish `dist/`
- GitHub Pages: build in CI, deploy `dist/` to `gh-pages`

## Repository

- Repo: `git@github.com:coachpo/wandering-qingdom.git`
- Default branch: `main`

## Customization Checklist

- Update `astro.config.mjs` with your domain
- Replace favicon at `public/favicon.ico`
- Set your social links via `Social` props
- Adjust the text badge in `Menu` (`title` prop)
- Tweak fonts in `src/layouts/Layout.astro` if desired

## Notes

- This template intentionally ships without personal content or analytics
- Add your own posts under `content/` when you’re ready


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
