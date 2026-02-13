# DudeX Parkiety — Jekyll Website

## Project Overview
A production website for DudeX Parkiety — a local carpentry shop specializing in hardwood floors and wooden stairs. Built with Jekyll and Tailwind CSS v4, hosted on Netlify.

## Tech Stack
- **Static Site Generator**: Jekyll 4.3
- **CSS Framework**: Tailwind CSS v4 (using `@tailwindcss/cli`)
- **Gallery**: PhotoSwipe Lightbox 5
- **Hosting**: Netlify
- **Ruby**: 3.4.2

## Development Commands
```bash
npm run dev         # Start dev server (Tailwind watch + Jekyll serve with livereload)
npm run build:css   # Build Tailwind CSS (minified)
npm run build       # Production build (CSS + Jekyll)
bundle exec jekyll serve --livereload  # Jekyll only dev server
```

## Project Structure
```
_config.yml          # Jekyll configuration (collections, defaults, plugins)
_layouts/            # HTML layouts (default, page, project, service, city)
_includes/           # Reusable components (header, footer, gallery-init)
_data/               # Translation files (pl.yml, en.yml), cities.yml
_projects/           # Project posts (portfolio items with galleries)
assets/
  css/main.css       # Tailwind CSS source (edit this)
  css/output.css     # Generated Tailwind output (do NOT edit)
  js/                # PhotoSwipe JS files
  images/            # All images including project photos
```

## Internationalization (i18n)
- **Default language**: Polish (pl) — pages at root `/`
- **Secondary language**: English (en) — pages under `/en/`
- Translation strings in `_data/pl.yml` and `_data/en.yml`
- Each page has `lang` front matter and `alternate_url` for the other language version
- Access translations in templates: `{% assign t = site.data[page.lang] %}`

## Page Types
- **Homepage**: `index.html` / `en/index.html`
- **Projects listing**: `projekty/index.html` / `en/projects/index.html`
- **Individual project**: `_projects/*.md` (uses `project` layout)
- **Service pages**: `uslugi/*.html` / `en/services/*.html` (uses `service` layout)
- **City SEO pages**: `miasta/*.html` / `en/cities/*.html` (uses `city` layout)
- **Contact**: `kontakt/index.html` / `en/contact/index.html`

## Adding a New Project
Create a new `.md` file in `_projects/` with this front matter:
```yaml
---
title: "Project Title"
date: 2024-01-01
thumbnail: /assets/images/projects/thumbnail.jpg
description: "Short description"
location: "City"
images:
  - url: /assets/images/projects/photo1.jpg
    alt: "Description"
    width: 1200
    height: 800
---
Markdown content here.
```

## Tailwind CSS
- Using Tailwind CSS v4 with `@tailwindcss/cli`
- Source file: `assets/css/main.css`
- Custom brand colors defined as CSS custom properties in `@theme` block
- Brand color palette: warm wood tones (brand-50 through brand-950)
- Output: `assets/css/output.css` (auto-generated, gitignored in dev)

## SEO
- `jekyll-seo-tag` and `jekyll-sitemap` plugins active
- JSON-LD structured data in layouts (LocalBusiness, Service, Article, BreadcrumbList)
- Open Graph and Twitter Card meta tags in default layout
- Hreflang tags for language alternates
- Per-page SEO fields: `seo_title`, `seo_description`, `seo_keywords`
- City pages have unique localized content for SEO value

## Netlify Deployment
- Build command: `npm run build`
- Publish directory: `_site`
- Ruby and Node.js required at build time
