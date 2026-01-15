---
title: Shadow Scale Shift
impact: CRITICAL
impactDescription: Visual regression - shadows will be smaller than expected
tags: migration, v3-to-v4, shadow, scale
---

## Shadow Scale Shift

v4 shifted the shadow scale down by one step. What was `shadow` in v3 is now `shadow-sm` in v4.

**Incorrect (v3 mental model):**

```html
<div class="shadow">Card with shadow</div>
<!-- In v4, this produces a SMALLER shadow than v3's "shadow" -->
```

**Correct (v4 equivalent):**

```html
<div class="shadow-sm">Card with shadow</div>
<!-- Matches v3's "shadow" visual output -->
```

**Full scale mapping:**

| v3 Class | v4 Equivalent |
|----------|---------------|
| `shadow-sm` | `shadow-xs` |
| `shadow` | `shadow-sm` |
| `shadow-md` | `shadow` |
| `shadow-lg` | `shadow-md` |
| `shadow-xl` | `shadow-lg` |
| `shadow-2xl` | `shadow-xl` |

Reference: [Upgrade Guide](https://tailwindcss.com/docs/upgrade-guide)
