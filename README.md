# Rory Allen - Portfolio Site

Terminal-style portfolio website for Rory Allen, an independent software engineer.

**Live Site**: [https://acmecat.github.io/rory-allen/](https://acmecat.github.io/rory-allen/)

## Tech Stack

Pure HTML5/CSS3 - No frameworks, no build process.

Terminal aesthetic:
- Bright green monospace on black background
- Cyan links, magenta hovers, yellow accents
- ASCII art header
- Command-line themed interface

## Local Development

Serve the site locally:

```bash
python3 -m http.server 8000
```

Then visit: `http://localhost:8000/index.html`

## Deployment

The site automatically deploys to GitHub Pages when changes are pushed to the `main` branch via GitHub Actions.

The workflow simply uploads the root directory (excluding `hugo-archive/`) to GitHub Pages.

## Structure

```
.
├── index.html          # About page
├── portfolio.html      # Portfolio listing
├── blog.html          # Blog listing
├── contact.html       # Contact info
├── css/
│   └── style.css      # Terminal-style CSS
├── portfolio/         # Individual project pages
│   ├── steadymama.html
│   ├── antsteroids.html
│   ├── ill-technique.html
│   ├── busta-blox.html
│   └── bujt.html
└── hugo-archive/      # Previous Hugo site (archived)
```

## Hugo Archive

The previous Hugo-based site has been archived in `hugo-archive/` for reference. Content from the Hugo site can be found in `hugo-archive/content/`.

## License

Content © Rory Allen. All rights reserved.
