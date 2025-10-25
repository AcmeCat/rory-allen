# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal portfolio website for Rory Allen, an independent software engineer specializing in Apple platforms with extensive web development and cloud deployment experience. The site is built using Hugo static site generator with the Ananke theme and deployed to GitHub Pages.

## Development Commands

### Local Development
```bash
# Start Hugo development server with drafts enabled
hugo server -D

# Start Hugo development server (production-like view without drafts)
hugo server

# Build the site (output goes to public/ directory)
hugo

# Build with minification and garbage collection (production build)
hugo --gc --minify
```

### Deployment
The site automatically deploys to GitHub Pages via GitHub Actions when changes are pushed to the `main` branch. See `.github/workflows/build.yaml` for the deployment workflow.

Manual build command matching CI/CD:
```bash
hugo --gc --minify --baseURL "https://acmecat.github.io/rory-allen/"
```

## Site Architecture

### Configuration
- **hugo.toml**: Main site configuration
  - Base URL: `https://acmecat.github.io/rory-allen/`
  - Theme: Ananke (installed as git submodule)
  - Pagination: 6 items per page
  - Custom styling via `static/css/custom.css`
  - Background color: near-black theme
  - Author: Rory Allen

### Content Structure
```
content/
├── _index.md           # Homepage (About Me section)
├── blog/               # Blog posts (menu weight: 2)
│   ├── _index.md      # Blog landing page
│   └── post-*.md      # Individual blog posts (date-based naming)
├── portfolio/          # Portfolio projects (menu weight: 1)
│   ├── _index.md      # Portfolio landing page
│   ├── antsteroids.md
│   ├── bujt.md
│   ├── busta-blox.md
│   └── ill-technique.md
└── contact/            # Contact page
    └── _index.md
```

### Content Guidelines

**Portfolio Pages**
Portfolio items showcase iOS apps and projects. Each portfolio page includes:
- Project title and description
- Screenshot/logo image from `/static/img/` (referenced as `/rory-allen/img/filename`)
- Features list
- Tech stack (e.g., Foundation, UIKit, AVKit, StoreKit)
- Link to app store or project

**Blog Posts**
- Naming convention: `post-YYYYMMDD.md`
- Include frontmatter with: title, date, tags (e.g., `['Swift','Music']`), and draft status
- Common topics: Swift development, music, D&D

**URL Paths**
All internal links must include the `/rory-allen/` base path prefix (e.g., `/rory-allen/portfolio`, `/rory-allen/img/logo.png`)

### Theme and Styling
- Uses Ananke theme (git submodule at `themes/ananke/`)
- Custom CSS overrides in `static/css/custom.css`
- Tachyons CSS framework for styling
- Featured images use "cover bg-top" class
- Color scheme: near-black background with configurable text colors

### Layouts
- Custom homepage layout: `layouts/index.html`
- Theme provides default layouts for blog, portfolio (list/single page templates)

### Static Assets
```
static/
├── css/
│   └── custom.css      # Custom styling overrides
└── img/                # Portfolio images and logos
```

## Working with Content

### Adding a New Blog Post
1. Create file: `content/blog/post-YYYYMMDD.md`
2. Add frontmatter with title, date, tags, and `draft: false`
3. Write content using Markdown
4. Preview with `hugo server -D`

### Adding a New Portfolio Item
1. Create file: `content/portfolio/project-name.md`
2. Add frontmatter with title and `draft: false`
3. Include project description, features, tech stack
4. Add image to `static/img/` and reference with `/rory-allen/img/filename`
5. Preview with `hugo server -D`

### Updating Theme
The Ananke theme is a git submodule. To update:
```bash
cd themes/ananke
git pull origin main
cd ../..
git add themes/ananke
git commit -m "update theme"
```

## Deployment Details

- Platform: GitHub Pages
- Hugo Version: 0.144.2 (extended)
- Auto-deployment: Triggered on push to `main` branch
- Workflow file: `.github/workflows/build.yaml`
- Build includes: Dart Sass compilation, submodule checkout, minification
- Timezone: America/Los_Angeles
