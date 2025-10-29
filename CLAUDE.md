# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static HTML portfolio website for Rory Allen, an independent software engineer specializing in Apple platforms. The site features a terminal-inspired aesthetic with a green-on-black color scheme.

**Live Site**: https://acmecat.github.io/rory-allen/

## Technology Stack

- Pure HTML5/CSS3 - No frameworks, no build process
- Terminal aesthetic using monospace fonts and green/cyan/magenta color scheme
- Deployed via GitHub Actions to GitHub Pages

## Local Development

Start a local server:
```bash
python3 -m http.server 8000
```

Then visit: http://localhost:8000/index.html

## Project Structure

```
.
├── index.html          # About page (main landing)
├── portfolio.html      # Portfolio listing page
├── blog.html          # Blog listing page
├── contact.html       # Contact information
├── css/
│   ├── style.css      # Main terminal-style CSS
│   └── ugotgdm.css    # Project-specific styles
├── portfolio/         # Individual project detail pages
│   ├── ugotgdm.html
│   ├── antsteroids.html
│   ├── ill-technique.html
│   ├── busta-blox.html
│   └── bujt.html
├── blog/              # Individual blog post pages
│   └── YYYYMMDD-slug.html
└── hugo-archive/      # Archived Hugo site (not deployed)
```

## Architecture & Design Patterns

### Site Navigation
- All pages share a common `<nav>` structure with 4 main links: about, portfolio, blog, contact
- Active page is indicated with `class="active"` on the nav link
- Navigation styling uses hover effects that invert colors (background becomes text color)

### CSS Design System
The terminal aesthetic is maintained through CSS custom properties in `css/style.css`:
- `--terminal-green: #00ff00` - Primary text color
- `--terminal-bg: #000000` - Background color
- `--cyan: #00ffff` - Link color
- `--magenta: #ff00ff` - Hover states
- `--yellow: #ffff00` - Accent color (h3, prompts)
- `--terminal-gray: #808080` - Secondary text (visited links, dates)

### Content Patterns

**Portfolio Grid**: Uses CSS Grid with `.portfolio-grid` and `.portfolio-item` classes for responsive card layout

**Blog List**: Uses `.blog-list` with `.card` classes. Each blog post card includes:
- Date in YYYY-MM-DD format (class `.date`)
- Title in h3
- Brief description
- Tags (class `.tag`)

**Blog Post Naming**: Blog posts use date-prefixed filenames: `YYYYMMDD-slug.html`

### Responsive Design
- Max-width container: 900px
- Mobile breakpoint: 768px
- Mobile navigation switches to column layout

## Deployment

The site deploys automatically via GitHub Actions when changes are pushed to `main` branch.

### GitHub Actions Workflow (`.github/workflows/build.yaml`)

The workflow:
1. Creates a `_site` directory
2. Copies all HTML files from root
3. Copies `css/`, `portfolio/`, and `blog/` directories
4. Optionally copies `js/` and `img/` if they exist
5. Uploads to GitHub Pages

**Important**: The workflow has duplicate "Create deployment directory" steps (lines 40-47 and 52-60). The second one is the active version that includes the `blog/` directory.

## Content Guidelines

### Adding New Blog Posts

1. Create a new HTML file in `blog/` with format: `YYYYMMDD-slug.html`
2. Update `blog.html` to add a new card entry at the top of `.blog-list`
3. Blog card should include:
   - Link to the blog post file
   - Date in YYYY-MM-DD format
   - Title (h3)
   - Brief description (p)
   - Tags as needed

Example blog card structure:
```html
<a href="blog/YYYYMMDD-slug.html" class="card">
    <span class="date">YYYY-MM-DD</span>
    <h3>Post Title</h3>
    <p>Brief description...</p>
    <div>
        <span class="tag">Tag1</span>
        <span class="tag">Tag2</span>
    </div>
</a>
```

### Adding New Portfolio Items

1. Create a new HTML file in `portfolio/`
2. Update `portfolio.html` to add a new entry in `.portfolio-grid`
3. Portfolio item should follow the established pattern with title, description, and technology tags

## Special Considerations

### Blog Post Styling
Some blog posts (like `20251029-ios-notification-cheat-sheet.html`) include embedded CSS instead of using the main stylesheet. This allows for specialized formatting (e.g., code syntax highlighting, tables, cards with different styles).

### Hugo Archive
The `hugo-archive/` directory contains the previous Hugo-based site and is NOT part of the deployed site. It's kept for reference and content migration purposes only.

### URL Paths
- Blog post links should be relative paths: `blog/YYYYMMDD-slug.html`
- Note inconsistency in blog.html:line 25 uses absolute path `/blog/...` while others use relative `blog/...`
- Portfolio links use relative paths: `portfolio/project-name.html`

## Common Tasks

**Test changes locally**:
```bash
python3 -m http.server 8000
# Visit http://localhost:8000/index.html
```

**Verify deployment**:
After pushing to `main`, check GitHub Actions tab for workflow status. Changes appear at https://acmecat.github.io/rory-allen/ once deployed.

**Check scheduled notifications** (if applicable):
The site doesn't have backend functionality, but the blog contains technical documentation about iOS notification systems that may be referenced for iOS projects.
