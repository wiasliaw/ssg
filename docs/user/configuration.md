---
title: "Configuration"
description: "Customize SSG behavior with ssg.config.ts"
created: 2026-01-11
tags: ["guide", "customization"]
---

# Configuration

SSG behavior is customized through a `ssg.config.ts` file in the project root.

## Quick Start

Create `ssg.config.ts` in your project root:

```typescript
import { defineConfig } from './src/lib/config';

export default defineConfig({
  content: {
    base: './docs',
    patterns: ['**/*.md'],
  },
});
```

A reference file `ssg.config.example.ts` is included in the repository.

## `defineConfig()` API

The `defineConfig()` function accepts an object with the following optional sections:

### `content` - Content Loader

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `base` | `string` | `'./docs'` | Root directory for content files |
| `patterns` | `string[]` | `['**/*.md']` | Glob patterns for matching content files |

```typescript
export default defineConfig({
  content: {
    base: './docs',
    patterns: ['**/*.md'],
  },
});
```

### `schema` - Frontmatter Schema

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `dateModifiedField` | `string` | `'modified'` | Frontmatter field name for modification date |
| `optionalDescription` | `boolean` | `false` | Allow posts without `description` |
| `optionalTags` | `boolean` | `false` | Allow posts without `tags` |
| `extraFields` | `(z) => Record<string, ZodType>` | - | Define additional frontmatter fields using Zod |

```typescript
export default defineConfig({
  schema: {
    dateModifiedField: 'modified',
    optionalDescription: false,
    optionalTags: false,
    extraFields: (z) => ({
      permalink: z.string().nullish(),
      category: z.enum(['tech', 'life']).optional(),
    }),
  },
});
```

The `extraFields` function receives the Zod library (`z`) as its argument, allowing you to define typed validation for custom frontmatter fields.

### `remarkPlugins` - Custom Remark Plugins

Add additional remark plugins to the Markdown processing pipeline:

```typescript
export default defineConfig({
  remarkPlugins: [
    './src/plugins/my-plugin.mjs',
    ['./src/plugins/another-plugin.mjs', { option: true }],
  ],
});
```

Plugins can be specified as:
- A string path to the plugin module
- A tuple of `[path, options]` for plugins that accept configuration

## Full Example

```typescript
import { defineConfig } from './src/lib/config';

export default defineConfig({
  content: {
    base: './docs',
    patterns: ['**/*.md'],
  },
  schema: {
    dateModifiedField: 'modified',
    optionalDescription: false,
    optionalTags: false,
    extraFields: (z) => ({
      permalink: z.string().nullish(),
    }),
  },
  remarkPlugins: [
    './src/plugins/my-plugin.mjs',
  ],
});
```

## See Also

- [Frontmatter](frontmatter.md) - Frontmatter fields reference
- [Getting Started](getting-started.md) - Initial setup
- [Writing Posts](writing-posts.md) - Content authoring guide
