---
title: 'Terminal Themes Guide'
description: 'Explore the four beautiful terminal themes included with Terminote and learn how to customize them.'
pubDate: 'Feb 13 2025'
heroImage: '../../assets/blog-placeholder-2.jpg'
---

Terminote comes with **four carefully crafted terminal themes** that capture different aesthetics from the world of command-line interfaces. Each theme provides a unique visual experience while maintaining excellent readability.

## Pro Theme (Default)

The **Pro** theme is inspired by the default macOS Terminal.app dark theme. It features:

- **Background**: Deep gray (#1e1e1e)
- **Primary Text**: Off-white (#f0f0f0)
- **Accent**: macOS blue (#0a84ff)
- **Success**: macOS green (#32d74b)
- **Warning**: macOS orange (#ff9f0a)

This theme is perfect for those who want a clean, professional look that matches their development environment.

## Homebrew Theme

The **Homebrew** theme brings the iconic Matrix green aesthetic to your blog:

- **Background**: Deep black (#0d1117)
- **Primary Text**: Matrix green (#00ff41)
- **Accent**: Cyan (#00d9ff)
- **Glow Effect**: Subtle text shadow for neon appearance

This theme is ideal for developers who love the classic green-on-black terminal look popularized by the Matrix movies and hacker culture.

## Nocturnal Theme

The **Nocturnal** theme offers a cyberpunk-inspired color palette:

- **Background**: Almost black (#0a0a0f)
- **Primary Text**: Neon cyan (#00f0ff)
- **Accent**: Purple (#bf5af2)
- **Secondary**: Indigo (#5e5ce6)

Perfect for night owls and fans of synthwave/cyberpunk aesthetics. The purple and cyan combination creates a futuristic, high-tech feel.

## Retro Theme

The **Retro** theme recreates the vintage amber monitor experience:

- **Background**: Warm dark (#1a1814)
- **Primary Text**: Amber (#ffb000)
- **Accent**: Orange (#ff9500)
- **Glow**: Subtle text shadow for CRT effect

This theme evokes nostalgia for the early days of computing when amber monochrome monitors were common. It provides a warm, inviting reading experience.

## How Themes Work

Each theme is defined using CSS custom properties (variables). Here's a simplified example from the Pro theme:

```css
[data-theme="pro"] {
  --terminal-bg: #1e1e1e;
  --terminal-bg-secondary: #2d2d2d;
  --terminal-text: #f0f0f0;
  --terminal-accent: #0a84ff;
  --terminal-success: #32d74b;
  --terminal-warning: #ff9f0a;
  --terminal-error: #ff453a;
  --terminal-cyan: #64d2ff;
  --terminal-magenta: #ff375f;
}
```

These variables control everything from background colors to text colors, accents, and even the traffic light button colors.

## Creating Custom Themes

You can easily create your own theme:

1. Create a new file: `src/styles/themes/mytheme.css`
2. Define your color scheme using the CSS variable pattern
3. Import it in `src/styles/global.css`
4. Add a theme button in `ThemeToggle.astro`

Your theme will automatically work with all terminal components!

## Theme Persistence

Your theme selection is automatically saved to localStorage, so your preference persists across browser sessions. The theme is also applied immediately when the page loads to prevent any flash of unstyled content.

## Accessibility

All themes are designed with accessibility in mind:
- High contrast ratios for readability
- Support for `prefers-reduced-motion` to disable animations
- Semantic HTML structure for screen readers
- Keyboard navigation support

Choose the theme that best fits your style and enjoy the terminal blogging experience! 🎨
