# Agent Instructions

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is the Recoup API documentation site built with [Mintlify](https://mintlify.com). It provides API reference documentation for the Recoup platform.

## Git Workflow

**Always commit and push changes after completing a task.** Follow these rules:

1. After making changes, always commit with a descriptive message
2. Push commits to the current feature branch
3. **NEVER push directly to `main`** - always use feature branches and PRs

### Starting a New Task

Branch from `main`:

```bash
git checkout main && git pull origin main && git checkout -b <branch-name>
```

## Project Structure

```
docs/
├── docs.json           # Mintlify configuration (navigation, branding, theme)
├── index.mdx           # Homepage
├── quickstart.mdx      # Getting started guide
├── development.mdx     # Development setup guide
├── api-reference/      # API endpoint documentation
│   ├── introduction.mdx
│   ├── openapi.json    # OpenAPI spec for API endpoints
│   └── [category]/     # Grouped API endpoints (tasks, artists, chat, etc.)
├── essentials/         # Core documentation pages
├── ai-tools/           # AI tool integration guides
├── logo/               # Brand logos (light.svg, dark.svg)
├── favicon.svg         # Site favicon
├── images/             # Documentation images
└── snippets/           # Reusable MDX snippets
```

## Development

Mintlify docs are deployed automatically. To preview locally:

```bash
npx mintlify@latest dev
```

## Configuration

All site configuration is in `docs.json`:
- **name**: Site name displayed in navigation
- **colors**: Brand colors (primary, light, dark)
- **logo**: Light and dark mode logo paths
- **favicon**: Favicon path
- **navigation**: Tab and page structure
- **navbar**: Top navigation links and buttons
- **footer**: Social links

## Branding

Reference `Recoup-Chat` codebase for correct branding values:
- **Primary color**: `#345A5D` (from `tailwind.config.ts` primaryGreen)
- **Support email**: `agent@recoupable.com`
- **App URL**: `https://chat.recoupable.com`
- **Website**: `https://recoupable.com`
- **Social URLs**:
  - X: `https://x.com/recoupai`
  - GitHub: `https://github.com/recoupable-com`
  - LinkedIn: `https://www.linkedin.com/company/recoupable`

## Writing Documentation

### MDX Files

Documentation pages use MDX (Markdown + JSX). Key conventions:
- Use frontmatter for page metadata (title, description)
- Use Mintlify components for callouts, code blocks, and interactive elements
- Keep content concise and scannable

### API Reference

API endpoints are documented in `api-reference/` with:
- OpenAPI spec in `openapi.json` for auto-generated endpoint docs
- MDX pages in `api-reference/[category]/` that reference the OpenAPI spec

**CRITICAL: API reference MDX pages should be frontmatter-only.** Do NOT add custom sections (Overview, Availability, etc.) — let Mintlify auto-generate everything from the OpenAPI spec. All descriptions, parameter docs, and response schemas belong in `openapi.json`.

```mdx
---
title: 'List Items'
openapi: 'GET /api/items'
---
```

This is the correct pattern. Nothing else should go in the file.

## Code Principles

From `Recoup-Chat/principles.md`:

- **DRY**: Don't duplicate content across pages - use snippets
- **Single Responsibility**: One concept per page
- **Clear Organization**: Group related pages in directories
- **Self-Documenting**: Use clear titles and descriptions
- **Comments**: Explain 'why', not 'what'
