# blog.karljtaylor.com

The blog for Karl Taylor, built with [Hugo](https://gohugo.io/) and hosted on Netlify.

## Branch Architecture

This is the `blog` branch, which deploys separately from `master`:

| Branch | URL | Description |
|--------|-----|-------------|
| `master` | [karljtaylor.com](https://karljtaylor.com) | Landing page |
| `blog` (this branch) | [blog.karljtaylor.com](https://blog.karljtaylor.com) | Full blog |

**Important:** These branches should never be merged.

## Content Management

Blog posts are authored using [Netlify CMS](https://www.netlifycms.org/) (now deprecated, but functional).

### Post Format

Posts use **TOML front matter** (`+++` delimiters):

```toml
+++
author = "karl taylor"
categories = ["category1", "category2"]
date = "YYYY-MM-DDTHH:MM:SS"
title = "Post Title"
type = "post"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
+++
```

### Image URLs

Images are stored in `content/assets/` and referenced via raw GitHub URLs:

```markdown
![](https://raw.githubusercontent.com/karljtaylor/kjt/blog/content/assets/filename.jpeg)
```

### Known Formatting Issues

Some older posts have formatting problems that may prevent proper display:
- Inconsistent leading whitespace on lines
- `[embed]` shortcodes that don't render
- Mixed use of inline HTML

## Local Development

```bash
# Install Hugo (macOS)
brew install hugo

# Run development server
hugo server -D

# Build for production
hugo
```

## Theme

[Hugo Future Imperfect](https://github.com/jpescador/hugo-future-imperfect) (git submodule)
