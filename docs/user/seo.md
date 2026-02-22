---
title: "SEO"
description: "Sitemap, RSS feed, and OpenGraph metadata"
created: 2026-01-11
tags: ["guide", "features"]
---

# SEO

SSG automatically generates sitemap, RSS feed, and OpenGraph metadata for optimal search engine visibility.

## Sitemap

A sitemap is automatically generated at `/sitemap-0.xml`.

- All published posts are included with priority `0.8`
- Tag pages are excluded from the sitemap
- The sitemap updates on every build

Configure the `site` URL in `astro.config.mjs` to ensure correct absolute URLs:

```js
export default defineConfig({
  site: 'https://your-domain.com',
});
```

## RSS Feed

An RSS feed is generated at `/rss.xml`.

- All published posts are included with full content
- Language is set to `zh-TW`
- Draft posts are excluded
- The feed updates on every build

Share `/rss.xml` with RSS readers to allow subscribers to follow your content.

## OpenGraph / Meta Tags

The Head component automatically generates meta tags for every page:

| Meta Tag | Source |
|----------|--------|
| `og:title` | Post `title` from frontmatter |
| `og:description` | Post `description` from frontmatter |
| `og:type` | `article` for posts |
| `article:published_time` | Post `created` date |
| `article:modified_time` | Post `modified` date (if set) |
| `article:tag` | Post `tags` array |

### How It Works

Frontmatter fields are mapped directly to meta tags. Ensure every post has a descriptive `title` and `description` for best results when shared on social media.

## Site Configuration

The `site` property in `astro.config.mjs` is used as the base URL for:

- Sitemap URLs
- RSS feed links
- OpenGraph `og:url` tags
- Canonical URLs

```js
export default defineConfig({
  site: 'https://your-domain.com',
});
```

## See Also

- [Frontmatter](frontmatter.md) - Fields that drive SEO metadata
- [Search](search.md) - On-site discoverability
- [Cloudflare Pages Deployment](../deployment/cloudflare-pages.md) - Deploy and go live
