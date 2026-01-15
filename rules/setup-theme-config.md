---
title: Theme Configuration with @theme
impact: CRITICAL
impactDescription: Core v4 pattern - replaces tailwind.config.js
tags: setup, theme, configuration, css-variables
---

## Theme Configuration with @theme

v4 uses `@theme` blocks in CSS to define design tokens. This replaces the JS-based `tailwind.config.js` for most use cases.

**Incorrect (v3 JS config as primary):**

```js
// tailwind.config.js - still works but not the v4 way
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: '#3b82f6',
      }
    }
  }
}
```

**Correct (v4 CSS-first):**

```css
@import 'tailwindcss';

@theme {
  --color-primary: #3b82f6;
  --color-secondary: #64748b;
  --breakpoint-3xl: 1920px;
  --font-display: "Satoshi", sans-serif;
}
```

**Override entire namespace:**

```css
@theme {
  /* Remove all default colors */
  --color-*: initial;

  /* Define only your colors */
  --color-brand: #ff6b00;
  --color-surface: #fafafa;
}
```

**Reference variables (use @theme inline):**

```css
@theme inline {
  /* Can reference other variables */
  --color-primary-light: oklch(from var(--color-primary) calc(l + 0.1) c h);
}
```

Reference: [Theme Variables](https://tailwindcss.com/docs/theme)
