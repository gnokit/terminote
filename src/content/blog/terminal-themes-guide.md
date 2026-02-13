---
title: 'Terminal Themes Guide'
description: 'Explore the four popular Ghostty terminal themes included with Terminote: Catppuccin Mocha, Dracula, Catppuccin Latte, and Solarized Light.'
pubDate: 'Feb 13 2025'
heroImage: '../../assets/blog-placeholder-2.jpg'
---

Terminote includes **four popular Ghostty terminal themes** that are beloved by developers worldwide. Each theme offers a carefully crafted color palette optimized for readability and aesthetics.

## Catppuccin Mocha (Default)

**Catppuccin Mocha** is a soft, pastel dark theme that's easy on the eyes during long coding sessions:

- **Background**: Deep purple-gray (#1E1E2E)
- **Primary Text**: Soft blue-white (#CDD6F4)
- **Accent**: Lavender purple (#CBA6F7)
- **Success**: Pastel green (#A6E3A1)
- **Vibe**: Soft, soothing, modern

This is the default theme for Terminote, providing a comfortable reading experience with gentle contrast.

## Dracula

**Dracula** is a bold, vivid dark theme that makes your content pop with vibrant colors:

- **Background**: Dark gray (#282A36)
- **Primary Text**: Near-white (#F8F8F2)
- **Accent**: Bright purple (#BD93F9)
- **Success**: Neon green (#50FA7B)
- **Vibe**: Bold, vibrant, energetic

Dracula is one of the most popular color schemes in the developer community, known for its high contrast and distinctive look.

## Catppuccin Latte

**Catppuccin Latte** brings the Catppuccin aesthetic to a warm, muted light theme:

- **Background**: Warm off-white (#EFF1F5)
- **Primary Text**: Dark gray (#4C4F69)
- **Accent**: Rich purple (#8839EF)
- **Success**: Forest green (#40A02B)
- **Vibe**: Warm, gentle, elegant

Perfect for daytime reading or when you prefer a light interface. The muted colors provide excellent readability without harsh contrast.

## Solarized Light

**Solarized Light** is a precision-engineered light theme based on the iconic Solarized color palette:

- **Background**: Warm beige (#FDF6E3)
- **Primary Text**: Desaturated blue-gray (#657B83)
- **Accent**: True blue (#268BD2)
- **Success**: Olive green (#859900)
- **Vibe**: Precise, balanced, professional

Solarized is renowned for its scientific approach to color selection, ensuring consistent luminance across all colors for reduced eye strain.

## How Themes Work

Each theme is defined using CSS custom properties (variables). Here's a simplified example from Catppuccin Mocha:

```css
[data-theme="catppuccin-mocha"] {
  --terminal-bg: #1E1E2E;
  --terminal-bg-secondary: #313244;
  --terminal-text: #CDD6F4;
  --terminal-accent: #CBA6F7;
  --terminal-success: #A6E3A1;
  --terminal-warning: #F9E2AF;
  --terminal-error: #F38BA8;
  --terminal-cyan: #89DCEB;
  --terminal-magenta: #F5C2E7;
}
```

These variables control everything from background colors to text colors, accents, and even the traffic light button colors.

## Theme Persistence

Your theme selection is automatically saved to localStorage, so your preference persists across browser sessions. The theme is also applied immediately when the page loads to prevent any flash of unstyled content.

## Accessibility

All Ghostty themes are designed with accessibility in mind:
- High contrast ratios for readability
- Support for `prefers-reduced-motion` to disable animations
- Semantic HTML structure for screen readers
- Keyboard navigation support

## Switching Themes

Click the theme buttons in the header to instantly switch between:
1. **Mocha** (Catppuccin Mocha)
2. **Dracula** (Dracula)
3. **Latte** (Catppuccin Latte)
4. **Solarized** (Solarized Light)

Choose the theme that best fits your style and enjoy the terminal blogging experience! 🎨
