# karljtaylor.com

Personal website and blog for Karl Taylor, built with [Hugo](https://gohugo.io/) and hosted on Netlify.

## Branch Architecture

This repository uses Netlify's branch deploy feature to serve two separate sites from the same repo:

| Branch | URL | Description |
|--------|-----|-------------|
| `master` | [karljtaylor.com](https://karljtaylor.com) | Landing page with social links |
| `blog` | [blog.karljtaylor.com](https://blog.karljtaylor.com) | Full blog |

**Important:** These branches should never be merged. They have different themes, configurations, and content structures.

## Local Development

```bash
# Install Hugo (macOS)
brew install hugo

# Run development server
hugo server -D

# Build for production
hugo
```

## Themes

- **Landing page (master):** [Aerial](https://html5up.net/aerial) by HTML5 UP
- **Blog (blog):** [Hugo Future Imperfect](https://github.com/jpescador/hugo-future-imperfect)

## Content Management

Content can be edited via [Forestry CMS](https://forestry.io/) or directly in the repository.
