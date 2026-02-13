# Astro Blog

A minimalistic blog built with Astro featuring content collections, RSS feeds, and responsive design.

## Features

- ⚡ **Fast by default** - Astro's zero-JS architecture
- 📝 **Content Collections** - Type-safe Markdown & MDX support
- 🎨 **Minimal styling** - Clean, customizable design
- 📱 **Responsive** - Mobile-first approach
- 🔍 **SEO-friendly** - Canonical URLs, OpenGraph, sitemap
- 📡 **RSS Feed** - Auto-generated at `/rss.xml`
- ✅ **100/100 Lighthouse** - Performance optimized

## Quick Start

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build
```

## Project Structure

```
├── public/              # Static assets (fonts, images)
├── src/
│   ├── components/      # Reusable Astro components
│   ├── content/blog/    # Blog posts (Markdown/MDX)
│   ├── layouts/         # Page layouts
│   ├── pages/           # File-based routes
│   ├── styles/          # Global CSS
│   ├── assets/          # Images processed by Astro
│   └── consts.ts        # Site constants
├── astro.config.mjs     # Astro configuration
└── package.json         # Dependencies
```

## Commands

| Command               | Action                                       |
| :-------------------- | :------------------------------------------- |
| `npm run dev`         | Start dev server at `localhost:4321`         |
| `npm run build`       | Build production site to `./dist/`           |
| `npm run preview`     | Preview production build locally             |
| `npx astro add`       | Add integrations (tailwind, react, etc.)     |
| `npx astro check`     | Type-check the project                       |
| `npx astro sync`      | Generate content collection types            |

## Adding Content

Create new blog posts in `src/content/blog/`:

```markdown
---
title: 'My New Post'
description: 'A brief description'
pubDate: 2024-01-15
heroImage: '../../assets/blog-placeholder-1.jpg'
---

Your content here...
```

## Contributing

See [AGENTS.md](./AGENTS.md) for development guidelines and code style conventions for AI agents and contributors.

## Deployment

Update `site` URL in `astro.config.mjs`, then deploy to:

- **Vercel** - `vercel --prod`
- **Netlify** - Connect Git repo
- **Cloudflare Pages** - Import from Git
- **Static hosting** - Upload `./dist/` folder

## Tech Stack

- [Astro](https://astro.build/) - Web framework
- [TypeScript](https://www.typescriptlang.org/) - Type safety
- [Zod](https://zod.dev/) - Schema validation
- [Sharp](https://sharp.pixelplumbing.com/) - Image optimization

## License

MIT
