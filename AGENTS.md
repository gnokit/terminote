# AGENTS.md - Terminote Development Guide

This guide is for AI agents working on the Terminote terminal-themed blog codebase.

## Available Commands

```bash
# Development
npm run dev          # Start dev server at localhost:4321
npm run build        # Build for production (outputs to ./dist/)
npm run preview      # Preview production build locally

# Astro CLI
npx astro add <name> # Add integrations (react, tailwind, etc.)
npx astro check      # Type-check the project
npx astro sync       # Generate content collection types
```

**Note:** No testing or linting tools are currently configured.

## Terminal Theme System

Terminote features 4 built-in terminal color schemes:

- **Pro** (default) - macOS Terminal dark theme
- **Homebrew** - Matrix green terminal style
- **Nocturnal** - Cyberpunk purple/blue theme
- **Retro** - Vintage amber monitor aesthetic

### Theme CSS Variables

Each theme defines these CSS custom properties:

```css
[data-theme="pro"] {
    --terminal-bg: #1e1e1e;
    --terminal-bg-secondary: #2d2d2d;
    --terminal-text: #f0f0f0;
    --terminal-text-muted: #6c6c6c;
    --terminal-accent: #0a84ff;
    --terminal-success: #32d74b;
    --terminal-warning: #ff9f0a;
    --terminal-error: #ff453a;
    --terminal-cyan: #64d2ff;
    --terminal-magenta: #ff375f;
}
```

### Creating New Themes

1. Create `src/styles/themes/your-theme.css`
2. Define `[data-theme="your-theme"]` selector with variables
3. Import in `src/styles/global.css`
4. Add theme button in `ThemeToggle.astro`

## Code Style Guidelines

### Astro Component Structure

Components follow this pattern:
```astro
---
// 1. Imports (TypeScript)
import type { CollectionEntry } from 'astro:content';

// 2. Props interface
interface Props {
    title: string;
    href?: string;
}

// 3. Destructure props
const { title, href = '#' } = Astro.props;
---

<!-- 4. Template -->
<a href={href} class="card">
    <h2>{title}</h2>
    <slot />
</a>

<!-- 5. Scoped styles -->
<style>
    .card {
        padding: 1rem;
    }
</style>
```

### File Naming Conventions

- **Components**: PascalCase (`Header.astro`, `FormattedDate.astro`)
- **Utilities/Config**: camelCase (`consts.ts`, `content.config.ts`)
- **Blog Content**: kebab-case (`welcome-to-terminote.md`, `terminal-themes-guide.md`)
- **Dynamic Routes**: Bracket notation (`[...slug].astro`)
- **Layouts**: Descriptive (`BlogPost.astro`)
- **Themes**: lowercase (`pro.css`, `homebrew.css`)

### TypeScript Guidelines

- Use strict TypeScript (configured in `tsconfig.json`)
- Define Props interfaces in component frontmatter
- Use `type` imports when importing only types:
  ```typescript
  import type { CollectionEntry } from 'astro:content';
  ```
- Leverage Astro's built-in types: `HTMLAttributes`, `ImageMetadata`
- Enable `strictNullChecks` (already configured)

### Import Patterns

```typescript
// Astro built-ins
import { Image } from 'astro:assets';
import { getCollection } from 'astro:content';

// Relative imports
import Header from '../components/Header.astro';
import '../styles/global.css';

// Global constants
import { SITE_TITLE, AUTHOR_NAME } from '../consts';

// Terminal components
import TerminalWindow from '../components/TerminalWindow.astro';
import ThemeToggle from '../components/ThemeToggle.astro';
```

### Styling Conventions

**Terminal CSS Variables** (defined in theme files):
```css
:root {
    --terminal-bg: #1e1e1e;
    --terminal-text: #f0f0f0;
    --terminal-accent: #0a84ff;
    --traffic-close: #ff5f56;
    --traffic-minimize: #ffbd2e;
    --traffic-maximize: #27c93f;
}
```

**Component-scoped styles** preferred over global styles. Use CSS custom properties for theming.

**Responsive breakpoints** (scaled 150% for 2K):
```css
@media (max-width: 1080px) {
    /* Tablet styles */
}

@media (max-width: 720px) {
    /* Mobile styles */
}
```

**Design at 150% scale** - All measurements are scaled for 2K resolution visibility:
- Base font-size: 24px (was 16px)
- Container width: 1350px (was 900px)
- Traffic lights: 18px (was 12px)

### Content Collections

Define schemas in `src/content.config.ts` using Zod:

```typescript
import { defineCollection, z } from 'astro:content';
import { glob } from 'astro/loaders';

const blog = defineCollection({
    loader: glob({ base: './src/content/blog', pattern: '**/*.{md,mdx}' }),
    schema: ({ image }) =>
        z.object({
            title: z.string(),
            description: z.string(),
            pubDate: z.coerce.date(),
            updatedDate: z.coerce.date().optional(),
            heroImage: image().optional(),
        }),
});

export const collections = { blog };
```

Query content in pages:
```typescript
const posts = await getCollection('blog');
```

### Error Handling

Astro uses file-based routing. Handle dynamic route errors with `Astro.params` validation:

```typescript
const { slug } = Astro.params;
const post = posts.find((p) => p.slug === slug);
if (!post) return Astro.redirect('/404');
```

### Accessibility

- Use semantic HTML elements
- Include `aria-label` or `aria-hidden` on icons
- Use the `.sr-only` class for screen-reader-only text
- Ensure color contrast meets WCAG standards
- Support `prefers-reduced-motion` for animations

### Constants

Store global data in `src/consts.ts`:
```typescript
export const SITE_TITLE = 'Terminote';
export const SITE_DESCRIPTION = 'A terminal-themed blog template powered by Astro';
export const AUTHOR_NAME = 'Paul Chan';
```

Update the `site` URL in `astro.config.mjs` before deploying.

## Project Structure

```
src/
├── components/       # Reusable UI components (.astro)
│   ├── ThemeToggle.astro      # Theme switcher
│   ├── TerminalWindow.astro   # macOS window wrapper
│   ├── BlinkingCursor.astro   # Animated cursor
│   └── Header.astro           # Terminal header
├── content/blog/     # Blog posts (.md, .mdx)
├── layouts/          # Page layouts (.astro)
├── pages/            # File-based routes (.astro)
├── styles/           # Global CSS + Themes
│   ├── themes/       # Theme files (pro, homebrew, etc.)
│   ├── terminal.css  # Terminal base styles
│   └── animations.css # Cursor blink, scanlines
├── assets/           # Images (processed by Astro)
└── consts.ts         # Global constants
public/               # Static files (fonts, favicon)
```

## Best Practices

1. **Zero JS by default** - Astro ships zero JavaScript; use `client:*` directives only when needed
2. **Content-driven** - Use content collections for type-safe data
3. **Image optimization** - Use `<Image />` component from `astro:assets`
4. **SEO** - Use `BaseHead.astro` component for meta tags
5. **RSS** - Update `src/pages/rss.xml.js` when adding content types
6. **Theme consistency** - Use CSS variables for colors, don't hardcode
7. **150% scale** - Maintain large sizes for 2K visibility
8. **Terminal aesthetic** - Keep macOS terminal styling consistent
