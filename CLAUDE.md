# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hugo static site for **karljtaylor.com** with a unique deployment architecture using Netlify's branch deploy feature.

## Critical Branch Architecture

**NEVER merge the `blog` branch into `master` or vice versa.** These branches operate as separate sites:

| Branch | Domain | Theme | Purpose |
|--------|--------|-------|---------|
| `master` | karljtaylor.com | aerial | Simple landing page with social links |
| `blog` | blog.karljtaylor.com | hugo-future-imperfect | Full blog with posts and content |

Both branches share the same GitHub repo but have entirely different configurations, themes, and content structures.

## Development Commands

```bash
# Local development server
hugo server -D

# Build site
hugo

# Preview with drafts and future posts (used by Forestry CMS)
hugo server -D -E -F --port 8080

# Create new blog post (on blog branch)
hugo new blog/YYYY-MM-DD-post-title.md
```

## Branch-Specific Details

### Master Branch (Landing Page)
- **Theme:** `themes/aerial` (embedded, not a submodule)
- **Config:** `config.toml` - configures social links and personal info
- **Content:** Minimal - just a privacy policy page

### Blog Branch
- **Theme:** `themes/hugo-future-imperfect` (git submodule)
- **Config:** `config.toml` with `baseurl = "https://blog.karljtaylor.com/"`
- **Content structure:**
  - `content/blog/` - Blog posts (named: `YYYY-MM-DD-title.md`)
  - `content/about/` - About page
  - `content/assets/` - Images and media
  - `content/category/` - Category pages
  - `content/itemized/` - Itemized content type

### Blog Post Front Matter
```yaml
---
title: "Post Title"
author: "Karl Taylor"
date: "YYYY-MM-DD"
categories:
  - Category Name
description: "Post description"
featured: "image-filename.jpg"
featuredpath: "assets"
type: post
---
```

## Deployment

- Hosted on Netlify with automatic branch deploys
- `_redirects` file handles legacy URL redirects to the blog subdomain
- Forestry CMS configured for content editing (`.forestry/` directory)

## Working with Both Sites

Always check which branch you're on before making changes:
```bash
git branch          # Check current branch
git checkout master # Landing page work
git checkout blog   # Blog content work
```

To have both branches available locally:
```bash
git fetch origin blog
git checkout -b blog origin/blog
```
