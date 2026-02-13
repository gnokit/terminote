# AGENTS.md - Astro Blog Development Guide

This guide is for AI agents working on this Astro blog codebase.

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
- **Blog Content**: kebab-case (`first-post.md`, `markdown-style-guide.md`)
- **Dynamic Routes**: Bracket notation (`[...slug].astro`)
- **Layouts**: Descriptive (`BlogPost.astro`)

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
import { SITE_TITLE } from '../consts';
```

### Styling Conventions

**CSS Variables** (defined in `src/styles/global.css`):
```css
:root {
    --accent: #2337ff;
    --black: 15, 18, 25;
    --gray: 96, 115, 159;
}
```

**Component-scoped styles** preferred over global styles. Use CSS custom properties for theming.

**Responsive breakpoints**:
```css
@media (max-width: 720px) {
    /* Mobile styles */
}
```

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

### Constants

Store global data in `src/consts.ts`:
```typescript
export const SITE_TITLE = 'Astro Blog';
export const SITE_DESCRIPTION = 'Welcome to my website!';
```

Update the `site` URL in `astro.config.mjs` before deploying.

## Project Structure

```
src/
├── components/       # Reusable UI components (.astro)
├── content/blog/     # Blog posts (.md, .mdx)
├── layouts/          # Page layouts (.astro)
├── pages/            # File-based routes (.astro)
├── styles/           # Global CSS
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
