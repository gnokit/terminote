---
title: 'Welcome to Terminote'
description: 'Get started with Terminote, a terminal-themed blog template for developers built with Astro.'
pubDate: 'Feb 13 2025'
heroImage: '../../assets/blog-placeholder-1.jpg'
---

Welcome to **Terminote**! This is the introductory post to help you get started with your new terminal-themed blog.

## What is Terminote?

Terminote is a blog template designed for developers who appreciate the aesthetics of terminal interfaces. It combines the clean, distraction-free environment of a command line with modern web technologies to create a unique blogging experience.

## Features at a Glance

- 🎨 **4 Terminal Themes** - Catppuccin Mocha, Dracula, Catppuccin Latte, and Solarized Light
- ⚡ **Lightning Fast** - Built with Astro's zero-JS architecture
- 📝 **Content Collections** - Type-safe Markdown & MDX
- 📱 **2K Optimized** - Scaled to 150% for high-resolution displays
- 🔍 **SEO Ready** - RSS, sitemap, and OpenGraph included

## Quick Start

Getting started is as simple as running a few commands:

```bash
# Clone the repository
git clone https://github.com/gnokit/terminote.git
cd terminote

# Install dependencies
npm install

# Start the dev server
npm run dev
```

Visit `http://localhost:4321` and you'll see your Terminote blog running!

## Customization

### Site Configuration

Edit `src/consts.ts` to update your site details:

```typescript
export const SITE_TITLE = 'Your Blog Name';
export const SITE_DESCRIPTION = 'Your description';
export const AUTHOR_NAME = 'Your Name';
```

### Adding Posts

Create new posts in `src/content/blog/`:

```markdown
---
title: 'My Post'
description: 'Description here'
pubDate: '2025-02-13'
heroImage: '../../assets/blog-placeholder-1.jpg'
---

Your content here...
```

## Switching Themes

Click the theme buttons in the header to switch between:

- **Catppuccin Mocha** - Soft pastel dark theme
- **Dracula** - Bold vivid dark theme
- **Catppuccin Latte** - Warm muted light theme
- **Solarized Light** - Precision warm light theme

Your theme preference is saved in localStorage and persists across sessions.

## Next Steps

- Check out the [Markdown Style Guide](/blog/markdown-style-guide) to see all formatting options
- Learn about [Terminal Themes](/blog/terminal-themes-guide) and how they work
- Read [Customizing Your Terminal](/blog/customizing-your-terminal) for advanced customization

Happy blogging in the terminal! 🖥️
