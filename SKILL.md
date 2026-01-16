---
name: tailwindcss-v4
description: "Tailwind CSS v4 patterns: CSS-first config, @theme/@utility/@variant directives, migration from v3. Use when working with Tailwind v4 projects."
proactive: match
match:
  - "tailwind"
  - "tailwindcss"
  - "@theme"
  - "@utility"
  - "@variant"
---

# Tailwind CSS v4 Skill

> CSS-first configuration, new directives, migration from v3.

## Quick Reference

### v4 Entry Point
```css
@import "tailwindcss";
```

**NOT the v3 way:**
```css
/* ❌ These cause errors in v4 */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Key Directives
| Directive | Purpose |
|-----------|---------|
| `@theme` | Define design tokens (colors, spacing, fonts) |
| `@utility` | Create custom utility classes |
| `@variant` | Define custom variants (hover, focus, etc.) |
| `@source` | Control class detection and safelisting |
| `@reference` | Import for @apply without emitting CSS |

## Theme Configuration (CSS-first)

```css
@import "tailwindcss";

@theme {
  --color-primary: #3b82f6;
  --color-secondary: #64748b;
  --font-display: "Inter", sans-serif;
  --spacing-18: 4.5rem;
}
```

**NOT tailwind.config.js:**
```javascript
// ❌ v3 pattern - don't use in v4
module.exports = {
  theme: {
    extend: {
      colors: { primary: '#3b82f6' }
    }
  }
}
```

## Custom Utilities

```css
@utility content-auto {
  content-visibility: auto;
}

@utility scrollbar-hidden {
  scrollbar-width: none;
  &::-webkit-scrollbar { display: none; }
}
```

## Custom Variants

```css
@variant hocus (&:hover, &:focus);

/* Dark mode with class strategy */
@custom-variant dark (&:is(.dark *));
```

## Theme Inline (preserve CSS vars)

```css
/* Variables emitted AND used for utilities */
@theme inline {
  --font-sans: "SF Pro Text", system-ui;
  --color-primary: #0066cc;
}
```

## New Gradient Syntax

```html
<!-- v4 preferred -->
<div class="bg-linear-to-r from-blue-500 to-purple-500"></div>

<!-- Also: bg-linear-to-b, bg-radial, bg-conic -->
```

## Safelisting Classes

```css
/* Inline safelist */
@source inline("bg-red-500 text-white hidden");

/* From external source */
@source "../content/**/*.md";
```

## Migration from v3

| v3 | v4 |
|----|-----|
| `@tailwind base/components/utilities` | `@import "tailwindcss"` |
| `tailwind.config.js theme.extend` | `@theme { --color-* }` |
| PostCSS `tailwindcss` plugin | `@tailwindcss/postcss` |
| `@apply` with config values | `@reference` import first |

## PostCSS Setup

```javascript
// postcss.config.js
export default {
  plugins: {
    '@tailwindcss/postcss': {}  // NOT 'tailwindcss'
  }
}
```

## Vite Setup

```javascript
// vite.config.ts
import tailwindcss from '@tailwindcss/vite'

export default {
  plugins: [tailwindcss()]
}
```

Reference: [Tailwind v4 Docs](https://tailwindcss.com/docs)
