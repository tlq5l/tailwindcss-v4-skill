---
title: Custom Utilities with @utility
impact: HIGH
impactDescription: Replaces @layer utilities pattern
tags: customization, utilities, directives
---

## Custom Utilities with @utility

v4 uses `@utility` directive to define custom utilities that work with variants. This replaces the v3 `@layer utilities` pattern.

**Incorrect (v3 @layer pattern):**

```css
@layer utilities {
  .content-auto {
    content-visibility: auto;
  }
}
```

**Correct (v4 @utility directive):**

```css
@utility content-auto {
  content-visibility: auto;
}
```

**With variants - they just work:**

```html
<div class="hover:content-auto md:content-auto">
  <!-- Variants apply automatically -->
</div>
```

**Functional utility with values:**

```css
@utility tab-* {
  tab-size: --value(--tab-size-*, integer);
}

/* Usage: tab-2, tab-4, tab-8 based on --tab-size-* variables */
```

Reference: [Functions and Directives](https://tailwindcss.com/docs/functions-and-directives)
