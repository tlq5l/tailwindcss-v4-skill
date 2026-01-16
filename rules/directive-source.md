---
title: "@source Directive"
impact: "HIGH"
impactDescription: "Ensures no class is missed in non-standard project structures."
tags: ["directive", "source", "configuration"]
---

## @source

Use `@source` to specify files that contain Tailwind classes.

### File Discovery
Use globs to match files:
```css
@source "../src/**/*.html";
@source "../components/**/*.{js,ts,jsx,tsx}";
```

### Excluding Files
Use `not` to exclude files:
```css
@source "../src/**/*.html";
@source not "../src/ignored/**/*.html";
```

### Inline Content
Use `inline()` to provide content directly in the CSS file (useful for testing or small examples):
```css
@source inline("bg-red-500 text-white p-4");
```

### Disable Auto-Detection
Use `source(none)` to disable automatic source detection:
```css
@import "tailwindcss";
@source "none";
@source "../manual-path/**/*.js";
```
