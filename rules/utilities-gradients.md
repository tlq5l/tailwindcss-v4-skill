---
title: "Gradient Color Interpolation"
impact: "Controls color space for gradient transitions"
impactDescription: "v4 allows specifying the color interpolation method for gradients, enabling smoother or more vibrant transitions."
tags: ["utilities", "gradients", "color-interpolation"]
---

## Gradient Color Interpolation

You can specify the color interpolation method for linear, conic, and radial gradients directly in the utility class.

### Syntax
Append the color space to the gradient utility.

- `bg-linear-to-r/oklch`
- `bg-linear-to-r/srgb`
- `bg-linear-to-r/hsl`

Also supports interpolation modifiers:
- `longer`
- `shorter`
- `increasing`
- `decreasing`

### Examples

```html
<!-- Linear gradient using OKLCH interpolation -->
<div class="bg-linear-to-r/oklch from-indigo-500 to-teal-400"></div>

<!-- Linear gradient using OKLCH with longer hue interpolation -->
<div class="bg-linear-to-r/oklch-longer from-indigo-500 to-teal-400"></div>
```

### Color Mix Fallbacks
Tailwind v4 automatically handles `color-mix()` fallbacks for browsers that don't support modern color spaces, ensuring progressive enhancement.

### Conic and Radial Gradients
Same syntax applies to `bg-conic` and `bg-radial`.

```html
<div class="bg-radial/oklch from-white to-black"></div>
```
