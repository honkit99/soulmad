# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Soulmad is a modern web blog/portfolio built with **Astro 5.16.1**. It deploys to GitHub Pages at `https://honkit99.github.io/soulmad`.

## Visual Development

### Design Principles

- Comprehensive design checklist in `/context/design-principles.md`
- Brand style guide in `/context/style-guide.md`
- When making visual (front-end, UI/UX) changes, always refer to these files for guidance

### Quick Visual Check

IMMEDIATELY after implementing any front-end change:

1. **Identify what changed** - Review the modified components/pages
2. **Navigate to affected pages** - Use `mcp__playwright__browser_navigate` to visit each changed view
3. **Verify design compliance** - Compare against `.claude/context/design-principles.md` and `.claude/context/style-guide.md`
4. **Validate feature implementation** - Ensure the change fulfills the user's specific request
5. **Check acceptance criteria** - Review any provided context files or requirements
6. **Capture evidence** - Take full page screenshot at desktop viewport (1440px) of each changed view
7. **Check for errors** - Run `mcp__playwright__browser_console_messages`

This verification ensures changes meet design standards and user requirements.

### Comprehensive Design Review

Invoke the `@agent-design-review` subagent for thorough design validation when:

- Completing significant UI/UX features
- Before finalizing PRs with visual changes
- Needing comprehensive accessibility and responsiveness testing

## Development Commands

```bash
npm run dev          # Start dev server with hot reload
npm run build        # Type check + production build
npm run preview      # Preview production build locally
npm run check        # TypeScript/Astro type checking
npm run lint         # Lint JS/TS/Astro files
npm run lint:fix     # Auto-fix linting issues
npm run format       # Format all files with Prettier
npm run format:check # Check formatting without changes
```

## Architecture

**Tech Stack:** Astro 5, TypeScript 5, Scoped CSS, Markdown Content Collections

**Source Structure:**
Refer Astro mcp for source structure

## Key Configuration

**astro.config.mjs:** Configured for GitHub Pages with `base: '/soulmad'`, HTML compression, CSS minification enabled.

**TypeScript:** Strict mode with Astro's strict preset.

**ESLint:** Flat config with astro and typescript-eslint plugins. Underscore-prefixed vars allowed unused.

**Prettier:** 2-space indent, single quotes, trailing commas (es5), Astro plugin.

## Git Workflow

Pre-commit hook (Husky + lint-staged) runs ESLint and Prettier on staged files automatically.

## CI/CD

- **ci.yml:** Runs lint, type check, and build on push/PR to main
- **deploy.yml:** Auto-deploys to GitHub Pages on push to main
