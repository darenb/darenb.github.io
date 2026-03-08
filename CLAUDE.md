# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Hugo blog ("Daren's Blog") deployed to GitHub Pages at https://darenb.github.io/. Uses the Ananke theme installed as a git submodule.

## Build & Dev Commands

```bash
# Local development server with drafts
hugo server -D

# Production build
hugo --minify

# Create a new post
hugo new posts/my-post-title.md
```

Hugo extended v0.128.0+ is required (Dart Sass support).

## Architecture

- **Theme**: Ananke (`themes/ananke/`) — git submodule from `theNewDynamic/gohugo-theme-ananke`
- **Content**: Blog posts live in `content/posts/` as Markdown with TOML frontmatter (`+++`)
- **Customization**: Override theme templates by placing files in `layouts/`, `assets/`, or `static/` (all currently empty — theme defaults are used)
- **Config**: `hugo.toml` — minimal config (baseURL, language, title, theme)

## Deployment

GitHub Actions workflow (`.github/workflows/hugo.yml`) auto-builds and deploys to GitHub Pages on push to `main`. Source is set to GitHub Actions in repo settings.

## Key Conventions

- Posts use TOML frontmatter (`+++` delimiters, not `---`)
- Set `draft = false` for posts to appear in production builds
- `public/` is gitignored — built by CI, not committed
- Theme is a submodule — clone with `--recurse-submodules` or run `git submodule update --init --recursive`
