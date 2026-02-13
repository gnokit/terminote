---
title: 'Customizing Your Terminal Blog'
description: 'Learn how to customize Terminote beyond the built-in themes - from CSS variables to component modifications.'
pubDate: 'Feb 13 2025'
heroImage: '../../assets/blog-placeholder-3.jpg'
---

While Terminote comes with four beautiful themes out of the box, the real power lies in how easily you can customize every aspect of your terminal blog. This guide covers advanced customization techniques.

## Understanding the CSS Architecture

Terminote uses a layered approach to styling:

1. **Base Variables** (`global.css`) - Core color definitions
2. **Theme Files** (`themes/*.css`) - Theme-specific overrides
3. **Component Styles** - Scoped styles within `.astro` files
4. **Terminal Styles** (`terminal.css`) - Terminal window aesthetics

## Customizing Colors

### Method 1: Edit Existing Themes

The simplest way to customize is modifying an existing theme file:

```css
/* src/styles/themes/catppuccin-mocha.css */
[data-theme="catppuccin-mocha"] {
  --terminal-bg: #1E1E2E;
  --terminal-text: #CDD6F4;
  --terminal-accent: #CBA6F7; /* Change this to your preferred accent */
  /* ... more variables */
}
```

### Method 2: Create a New Theme

Create a complete new theme:

```css
/* src/styles/themes/ocean.css */
[data-theme="ocean"] {
  /* Background colors */
  --terminal-bg: #0c1e3e;
  --terminal-bg-secondary: #1a3a5c;
  
  /* Text colors */
  --terminal-text: #e6f7ff;
  --terminal-text-muted: #7aa7c7;
  
  /* Accent colors */
  --terminal-accent: #00d4ff;
  --terminal-accent-secondary: #0099cc;
  --terminal-success: #00ff88;
  --terminal-warning: #ffaa00;
  --terminal-error: #ff5555;
  --terminal-cyan: #00ffff;
  --terminal-magenta: #ff66b2;
  
  /* Traffic lights (keep macOS colors or customize) */
  --traffic-close: #ff5f56;
  --traffic-minimize: #ffbd2e;
  --traffic-maximize: #27c93f;
  
  /* Shadows */
  --terminal-shadow: 0 20px 60px rgba(0, 212, 255, 0.15);
}
```

Then import it in `global.css`:

```css
@import './themes/ocean.css';
```

## Modifying Terminal Components

### Terminal Window

The `TerminalWindow` component accepts several props:

```astro
<TerminalWindow 
  title="custom-window" 
  showTrafficLights={true}
  showStatusBar={true}
  statusText="bash"
>
  Your content here
</TerminalWindow>
```

You can modify the component styling in `src/styles/terminal.css`:

```css
.terminal-window {
  border-radius: 15px; /* Change corner radius */
  box-shadow: var(--terminal-shadow);
}

.terminal-header {
  padding: 18px 24px; /* Adjust header padding */
}
```

### Blinking Cursor

Customize the cursor appearance:

```css
.blinking-cursor {
  width: 12px; /* Cursor width */
  height: 1.2em;
  background-color: currentColor;
  animation: blink 1s step-end infinite;
}

@keyframes blink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}
```

## Adding Custom Components

Create new terminal-styled components:

```astro
---
// src/components/TerminalCommand.astro
interface Props {
  command: string;
  output?: string;
}

const { command, output } = Astro.props;
---

<div class="terminal-command">
  <div class="command-line">
    <span class="prompt">➜</span>
    <span class="command-text">{command}</span>
  </div>
  {output && <div class="command-output">{output}</div>}
</div>

<style>
  .terminal-command {
    margin: 12px 0;
  }
  .prompt {
    color: var(--terminal-accent);
    margin-right: 8px;
  }
  .command-output {
    color: var(--terminal-text-muted);
    margin-left: 24px;
    margin-top: 4px;
  }
</style>
```

## Customizing Animations

Modify or add animations in `src/styles/animations.css`:

```css
/* Custom fade animation */
@keyframes customFade {
  from { 
    opacity: 0; 
    transform: translateY(20px); 
  }
  to { 
    opacity: 1; 
    transform: translateY(0); 
  }
}

.custom-fade {
  animation: customFade 0.5s ease-out;
}
```

## Typography Customization

Change the font family or size:

```css
/* In global.css */
body {
  font-family: "Your Font", "Menlo", monospace;
  font-size: 24px; /* Already scaled for 2K */
}
```

Popular alternatives to SF Mono:
- **Fira Code** - Great ligatures
- **JetBrains Mono** - Excellent readability
- **Cascadia Code** - Microsoft's terminal font

## Layout Modifications

### Container Width

Adjust the main content width:

```css
main {
  width: 1350px; /* Current 2K optimized */
  /* Change to your preferred width */
}
```

### Responsive Breakpoints

Modify breakpoints for different screen sizes:

```css
@media (max-width: 1080px) {
  /* Tablet styles */
  body {
    font-size: 21px;
  }
}

@media (max-width: 720px) {
  /* Mobile styles */
  body {
    font-size: 18px;
  }
}
```

## Adding Syntax Highlighting

Install a syntax highlighting library:

```bash
npm install @astrojs/prism
```

Then import a theme in your layout:

```astro
<link rel="stylesheet" href="/themes/prism-tomorrow.css" />
```

## Performance Considerations

When customizing:
- Keep CSS custom properties in theme files organized
- Use the cascade efficiently
- Test theme switching performance
- Ensure reduced motion preferences are respected

## Sharing Your Customizations

If you create an awesome custom theme:

1. Fork the Terminote repository
2. Add your theme files
3. Submit a pull request
4. Share screenshots in the PR description

The Terminote community would love to see what you create! 🎨
