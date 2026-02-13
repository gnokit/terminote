# Terminote

A terminal-themed blog template for developers, built with Astro.

![Terminote Preview](https://gnokit.github.io/terminote/preview.png)

## Features

- 🖥️ **Terminal UI** - Authentic macOS terminal aesthetic with traffic lights
- 🎨 **4 Ghostty Themes** - Catppuccin Mocha, Dracula, Catppuccin Latte, and Solarized Light
- ✨ **Animated Effects** - Blinking cursor, subtle scanlines, smooth transitions
- 🔍 **SEO-friendly** - Canonical URLs, OpenGraph, sitemap, RSS feeds
- 📱 **Responsive** - Optimized for 2K displays with 150% scaling
- ⚡ **Fast** - Astro's zero-JS architecture, 100/100 Lighthouse score
- 📝 **Content Collections** - Type-safe Markdown & MDX support

## Terminal Themes

Switch between 4 popular Ghostty terminal color schemes:

| Theme | Type | Background | Primary Text | Accent | Description |
|-------|------|------------|--------------|--------|-------------|
| **Catppuccin Mocha** | Dark | `#1E1E2E` | `#CDD6F4` | `#CBA6F7` | Soothing pastel dark theme by Catppuccin |
| **Dracula** | Dark | `#282A36` | `#F8F8F2` | `#BD93F9` | Classic vivid dark theme by Zeno Rocha |
| **Catppuccin Latte** | Light | `#EFF1F5` | `#4C4F69` | `#8839EF` | Warm muted light theme by Catppuccin |
| **Solarized Light** | Light | `#FDF6E3` | `#657B83` | `#268BD2` | Precision-engineered theme by Ethan Schoonover |

## Quick Start

```bash
# Clone the repository
git clone https://github.com/gnokit/terminote.git
cd terminote

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
│   ├── styles/          # Global CSS + Terminal themes
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

## Customization

### Site Configuration

Edit `src/consts.ts`:

```typescript
export const SITE_TITLE = 'Your Blog Name';
export const SITE_DESCRIPTION = 'Your blog description';
export const AUTHOR_NAME = 'Your Name';
```

### Adding Blog Posts

Create new posts in `src/content/blog/`:

```markdown
---
title: 'My New Post'
description: 'A brief description'
pubDate: 2024-01-15
heroImage: '../../assets/blog-placeholder-1.jpg'
---

Your content here...
```

### Creating Custom Themes

Add new theme files in `src/styles/themes/` following the existing pattern:

```css
[data-theme="mytheme"] {
  --terminal-bg: #1e1e1e;
  --terminal-text: #f0f0f0;
  /* ... more variables */
}
```

## Deployment

### GitHub Pages

1. Update `site` in `astro.config.mjs`:
   ```javascript
   site: 'https://yourusername.github.io/terminote',
   ```

2. Enable GitHub Pages in repository settings
3. Push to `main` branch

### Other Platforms

- **Vercel** - `vercel --prod`
- **Netlify** - Connect Git repo
- **Cloudflare Pages** - Import from Git

## Contributing

See [AGENTS.md](./AGENTS.md) for development guidelines and code style conventions.

## Author

Created by [Paul Chan](https://github.com/gnokit)

## Tech Stack

- [Astro](https://astro.build/) - Web framework
- [TypeScript](https://www.typescriptlang.org/) - Type safety
- [Zod](https://zod.dev/) - Schema validation
- [Sharp](https://sharp.pixelplumbing.com/) - Image optimization

## License

MIT

---

**[Live Demo](https://gnokit.github.io/terminote)** | **[GitHub Repo](https://github.com/gnokit/terminote)**
