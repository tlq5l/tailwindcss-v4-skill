# Tailwind CSS v4 Skill

AI-agent skill for Tailwind CSS v4 patterns, migration, and best practices.

## What is this?

A skill file that teaches AI coding agents (Claude, Copilot, Cursor, etc.) the correct patterns for Tailwind CSS v4. Agents read `AGENTS.md` and apply the knowledge when helping with Tailwind code.

## Quick Start

1. Copy `AGENTS.md` to your project root (or `.claude/` for Claude Code)
2. Your AI agent will automatically pick up the v4 patterns

## Structure

```
tailwindcss-v4/
├── AGENTS.md           # Compiled skill (agents read this)
├── rules/              # Modular rule files
│   ├── setup-*.md      # Configuration patterns
│   ├── migration-*.md  # v3 → v4 migration
│   └── customization-*.md  # Custom utilities/variants
├── test-cases.json     # Bad/good code pairs for testing
├── metadata.json       # Version, status, test results
└── src/
    ├── build.ts        # Compiles rules → AGENTS.md
    ├── validate.ts     # Unfakeable validation (real CLI)
    └── test-llm.ts     # LLM evaluation runner
```

## Validation

This skill includes **unfakeable validation** - tests that run real Tailwind CLI and grep actual source code. No AI opinions, only facts.

```bash
bun run validate
```

Output:
```
LAYER 1: EXECUTION TESTS (real Tailwind CLI)
LAYER 2: SOURCE VERIFICATION (grep against repo)

TOTAL: 15/15 (100%)
✅ ALL TESTS PASS - VERIFIED
```

## Key v4 Patterns

### Entry Point
```css
/* v4 - single import */
@import "tailwindcss";

/* NOT the v3 way */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Theme Configuration
```css
@theme {
  --color-primary: #3b82f6;
  --font-display: "Inter", sans-serif;
}
```

### Custom Utilities
```css
@utility content-auto {
  content-visibility: auto;
}
```

### Custom Variants
```css
@variant hocus (&:hover, &:focus);
```

### Safelisting
```css
@source inline("bg-red-500 text-white");
```

## Development

```bash
# Build AGENTS.md from rules
bun run build

# Run validation
bun run validate

# Test LLM comprehension
bun run test:llm
```

## Contributing

1. Add/edit rules in `rules/*.md`
2. Add test cases to `test-cases.json`
3. Run `bun run build`
4. Run `bun run validate` - must pass 100%
5. Submit PR

## License

MIT
