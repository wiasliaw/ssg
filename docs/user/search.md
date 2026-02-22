---
title: "Search"
description: "Full-text search powered by Pagefind"
created: 2026-01-11
tags: ["guide", "features"]
---

# Search

SSG includes full-text search powered by [Pagefind](https://pagefind.app/).

## How It Works

Pagefind generates a static search index at build time by scanning the rendered HTML output. No server-side processing is required — search runs entirely in the browser.

### Build-Time Index Generation

The search index is automatically generated during the build process:

```bash
pnpm build
```

This runs `pagefind --site dist` after the Astro build, creating the search index in `dist/_pagefind/`.

## Search UI

The search interface is integrated into the site header. Click the search icon or use keyboard shortcuts to open the search dialog.

### Features

- **Instant results** - Results appear as you type
- **Highlighted excerpts** - Matching text is highlighted in context
- **Keyboard navigation** - Navigate results with arrow keys

## Language Support

Pagefind supports Chinese (zh-TW) content out of the box. The search index is configured for multilingual content, ensuring accurate tokenization and matching for CJK characters.

## Troubleshooting

### Search not working after build

Ensure the build completed successfully and `dist/_pagefind/` directory exists. If deploying to Cloudflare Pages, verify that the build command includes the Pagefind step.

### Search index too large

Pagefind automatically splits the index into chunks for efficient loading. For very large sites, consider using `data-pagefind-ignore` attributes to exclude non-essential content from indexing.

## See Also

- [Getting Started](getting-started.md) - Build commands
- [SEO](seo.md) - Other discoverability features
