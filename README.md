# Rory Allen - Portfolio Website

Personal portfolio and blog for Rory Allen, an independent software engineer specializing in Apple platforms, web development, and cloud deployment.

**Live Site**: [https://acmecat.github.io/rory-allen/](https://acmecat.github.io/rory-allen/)

## About

This is a static site built with [Hugo](https://gohugo.io/) using the [Ananke theme](https://github.com/theNewDynamic/gohugo-theme-ananke) and deployed to GitHub Pages.

The site features:
- Portfolio showcasing iOS apps and development projects
- Blog posts about Swift development, music, and D&D
- Contact information

## Local Development

### Prerequisites
- Hugo Extended v0.144.2 or later ([installation guide](https://gohugo.io/installation/))
- Git (for cloning and submodule management)

### Setup

1. Clone the repository with submodules:
```bash
git clone --recurse-submodules https://github.com/acmecat/rory-allen.git
cd rory-allen
```

If you already cloned without submodules:
```bash
git submodule update --init --recursive
```

2. Start the development server:
```bash
hugo server -D
```

The site will be available at `http://localhost:1313/rory-allen/`

### Building

To build the site for production:
```bash
hugo --gc --minify
```

Output will be in the `public/` directory.

## Content Management

### Adding Blog Posts

Create a new markdown file in `content/blog/`:
```bash
content/blog/post-YYYYMMDD.md
```

Example frontmatter:
```yaml
---
title: "Your Post Title"
date: 2025-01-06
tags: ['Swift','Music']
draft: false
---
```

### Adding Portfolio Items

Create a new markdown file in `content/portfolio/`:
```bash
content/portfolio/project-name.md
```

Include project details, features, tech stack, and images from `static/img/`.

## Deployment

The site automatically deploys to GitHub Pages when changes are pushed to the `main` branch via GitHub Actions (see `.github/workflows/build.yaml`).

## Theme

This site uses the Ananke theme as a git submodule. Custom styling is in `static/css/custom.css`.

To update the theme:
```bash
cd themes/ananke
git pull origin main
cd ../..
git add themes/ananke
git commit -m "update theme"
```

## License

Content © Rory Allen. All rights reserved.
