# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the **blog branch** of karljtaylor.com, a Hugo static site hosted on Netlify at `blog.karljtaylor.com`.

## Critical Branch Architecture

**NEVER merge `blog` into `master` or vice versa.** These are separate sites:

| Branch | Domain | Purpose |
|--------|--------|---------|
| `master` | karljtaylor.com | Landing page |
| `blog` (this branch) | blog.karljtaylor.com | Full blog |

## Development Commands

```bash
hugo server -D          # Local dev server with drafts
hugo                    # Build site
hugo new blog/YYYY-MM-DD-post-title.md  # New post
```

## Content Structure

- `content/blog/` - Published posts
- `content/drafts/` - Local drafts (gitignored, for Ulysses workflow)
- `content/assets/` - Images and media
- `content/about/` - About page
- `content/contact/` - Legacy contact form (hidden, not linked)

## Post Format

Posts use **TOML front matter** (`+++` delimiters):

```toml
+++
author = "karl taylor"
categories = ["category1", "category2"]
date = "2025-01-22T12:00:00Z"
title = "Post Title"
type = "post"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
+++
```

## Image URLs

Images are stored in `content/assets/` and referenced via raw GitHub URLs:

```markdown
![](https://raw.githubusercontent.com/karljtaylor/kjt/blog/content/assets/filename.jpeg)
```

## Embeds

- **YouTube**: Use Hugo shortcode `{{< youtube VIDEO_ID >}}`
- **Twitter**: Use HTML blockquote embed
- **Other URLs**: Use markdown links

## Drafts Workflow (Ulysses)

1. Write in `content/drafts/` (gitignored)
2. Use `_template.md` as starting point
3. Move to `content/blog/` when ready to publish

## Menu Structure

Defined in `config.toml` under `[[menu.main]]`:
- Home (/) - weight 1
- About (/about/) - weight 2
- Contact (external: kjt.world) - weight 3
- Subscribe (external: substack) - weight 4

## Theme

[Hugo Future Imperfect](https://github.com/jpescador/hugo-future-imperfect) (git submodule in `themes/`)
