---
title: "@custom-variant Directive"
impact: "Defines new custom variants for use in utilities"
impactDescription: "Use @custom-variant to create reusable variants that can be applied to utilities, simplifying complex selectors."
tags: ["directive", "custom-variant", "customization"]
---

## @custom-variant

Use `@custom-variant` to define a new variant that can be used like built-in variants (e.g., `hover:`, `focus:`).

### Defining a Custom Variant

You can define a custom variant using a selector or a body block.

#### Using a Selector
Pass the variant name and the selector it represents. Use `&` to represent the element.

```css
@custom-variant pointer-coarse (@media (pointer: coarse));
@custom-variant dark (&:where(.dark, .dark *));
```

Usage:
```html
<div class="pointer-coarse:hidden">...</div>
<div class="dark:bg-slate-900">...</div>
```

#### Using a Body Block with @slot
For more complex variants, use a block and `@slot` to indicate where the utility styles should be inserted.

```css
@custom-variant hocus {
  &:hover,
  &:focus {
    @slot;
  }
}
```

Usage:
```html
<button class="hocus:opacity-100">...</button>
```

### Circular Dependencies
Avoid circular dependencies where variants reference each other in a loop.
