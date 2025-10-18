# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static website for Gillan Geospatial LLC built using Hugo Blox (formerly Hugo Wowchemy). The site is deployed via Netlify and served at https://www.gillangeospatial.com. Domain is managed through Squarespace.

**Hugo Version**: 0.136.5 (specified in netlify.toml)
**Hugo Blox Module**: blox-tailwind v0.3.1

## Development Commands

### Initial Setup
```bash
# Clone repository
git clone git@github.com:jeffgillan/gillan_geospatial_website.git

# Install dependencies (macOS)
brew install hugo
brew install go

# Initialize submodules
git submodule update --init --recursive
```

### Local Development
```bash
# Start local development server
hugo server -D

# Site will be available at http://localhost:1313
```

### Build
```bash
# Production build (as used by Netlify)
hugo --gc --minify

# Output directory: public/
```

## Architecture & Customization Strategy

Hugo Blox uses a two-tier customization approach:

### 1. Superficial Customization (YAML Configuration)
Most common edits are done via YAML config files:

- **Home page**: `content/_index.md`
- **Other pages** (about, ai_mapping, etc.): `content/{page_name}/`
- **Header menu**: `config/_default/menus.yaml` and `config/_default/params.yaml`
- **Footer**: `config/_default/params.yaml`
- **Images for pages**: Place in `static/media/` and reference as `/media/example_image.png`

### 2. Deep Customization (HTML/CSS Overrides)
The base theme code lives remotely at https://github.com/HugoBlox/hugo-blox-builder/tree/modules/blox-tailwind/v0.3.1/modules/blox-tailwind

To customize HTML/CSS:
1. Copy the remote file to local repo (e.g., `layouts/partials/components/headers/my-navbar.html`)
2. Update the reference in YAML config (e.g., change `blox:navbar` to `blox:my-navbar` in params.yaml)

Reference: https://docs.hugoblox.com/reference/extend/

### Current Custom Components
- **Custom navbar**: `layouts/partials/components/headers/my-navbar.html` (referenced in params.yaml as `blox: "my-navbar"`)
- **Custom block**: `layouts/partials/blocks/cta-image-paragraph.html` (used in content/_index.md for image-text layouts)

## Content Structure

Content is organized under `content/`:
- `_index.md` - Home page with sections using Hugo Blox blocks
- `about/` - About page
- `ai_mapping/` - AI mapping services page
- `topo_surveying/` - Topographic surveying page
- `training/` - Education & training page
- `blog/` - Blog posts
- `authors/` - Author profiles

Home page uses custom `cta-image-paragraph` block for alternating image/text layout sections.

## Key Configuration Files

- `config/_default/params.yaml` - Site settings, header/footer, SEO, analytics
- `config/_default/menus.yaml` - Navigation menu structure
- `netlify.toml` - Netlify build settings and environment
- `go.mod` - Hugo module dependencies
- `hugoblox.yaml` - Hugo Blox specific config

## Module System

This site uses Hugo Modules defined in go.mod:
- `blox-plugin-netlify` - Netlify integration
- `blox-tailwind` v0.3.1 - Main theme module with Tailwind CSS

When the theme needs updating, modify go.mod and run `hugo mod get -u`.

## Deployment

Deployment is handled automatically via Netlify:
- **Production branch**: main
- **Build command**: `hugo --gc --minify -b $URL`
- **Publish directory**: public
- **Plugin**: netlify-plugin-hugo-cache-resources (caches Hugo resources between builds)

## Important Notes

- Images for content pages must be in `static/media/`, not `assets/media/`
- Logo and images referenced in YAML configs should be in `assets/media/`
- The navbar is customized - changes to justify-left vs justify-center in my-navbar.html affect logo/menu alignment
- Hugo stats are tracked in hugo_stats.json for Tailwind CSS purging
