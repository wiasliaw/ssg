---
title: "Graph and Backlinks"
description: "Interactive graph visualization and automatic backlinks"
created: 2026-01-11
tags: ["guide", "features"]
---

# Graph and Backlinks

SSG provides interactive graph visualization and automatic backlinks, inspired by tools like Obsidian and Roam Research.

## Global Graph

Visit `/graph` to see a full interactive graph of all posts and their connections.

- **D3 force-directed layout** - Nodes are positioned using physics simulation
- **Clickable nodes** - Click any node to navigate to that post
- **Visual clusters** - Densely connected posts naturally group together

## Local Graph

Each post displays a local graph at the bottom, showing its immediate neighborhood:

- The current post (highlighted node)
- All posts that this post links to (outgoing wiki links)
- All posts that link to this post (incoming backlinks)

## Backlinks

Below each post, a backlinks section automatically lists all posts that contain a wiki link pointing to the current post.

For example, if Post A contains `[[post-b]]`, then Post B's backlinks section will show Post A.

### How It Works

1. During build, all wiki links (`[[slug]]`) are extracted from every post
2. A bidirectional link map is constructed
3. Each post page renders its incoming links as backlinks

## Building Connections

Connections are established through [[wiki-links|wiki links]]. To connect two posts:

```markdown
Check out [[other-post]] for more details.
```

The more you interlink your posts, the richer the graph becomes.

## Best Practices

- **Link generously** - Create wiki links whenever you reference related concepts
- **Use descriptive slugs** - Node labels come from post titles
- **Review the global graph** - Identify orphan posts that could benefit from connections

## See Also

- [Wiki Links](wiki-links.md) - Wiki link syntax reference
- [Search](search.md) - Another way to discover content
