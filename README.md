# alineavila.dev

Personal website and tech blog built with Hugo and the Blowfish theme.

## Overview

This is the source code for [alineavila.dev](https://alineavila.dev), a personal website featuring technical articles, blog posts, and professional information.

## Tech Stack

- **[Hugo](https://gohugo.io/)** - Fast and flexible static site generator
- **[Blowfish Theme](https://blowfish.page/)** - Modern and feature-rich Hugo theme
- **Go** - Required for Hugo

## Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) (v0.87.0 or later)
- [Git](https://git-scm.com/)

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/alineavila/alineavila.dev.git
cd alineavila.dev
```

### Install Theme

The Blowfish theme is included as a submodule. Initialize it with:

```bash
git submodule update --init --recursive
```

### Run Development Server

Start the Hugo development server:

```bash
hugo server -D
```

The site will be available at `http://localhost:1313`.

## Project Structure

```
.
├── archetypes/          # Content templates
├── assets/              # Custom CSS, JS, and other assets
├── config/              # Hugo configuration files
│   └── _default/        # Default configuration
├── content/             # Markdown content files
│   ├── about.md         # About page
│   └── posts/           # Blog posts
├── data/                # Data files
├── i18n/                # Internationalization files
├── layouts/             # Custom layouts and partials
├── public/              # Generated static site (git-ignored)
├── resources/           # Hugo resources cache
├── static/              # Static files (images, favicons, etc.)
└── themes/              # Hugo themes
    └── blowfish/        # Blowfish theme
```

## Configuration

The site configuration is managed through TOML files in the `config/_default/` directory:

- `hugo.toml` - Main Hugo configuration
- `params.toml` - Theme parameters and site settings
- `menus.en.toml` - Navigation menu structure
- `languages.en.toml` - Language-specific settings
- `markup.toml` - Markdown and syntax highlighting configuration
- `module.toml` - Hugo modules configuration

## Creating Content

### New Blog Post

Create a new blog post using Hugo archetypes:

```bash
hugo new posts/my-new-post/index.md
```

Edit the generated file in `content/posts/my-new-post/index.md` and add your content.

### Front Matter

Posts support various front matter options:

```yaml
---
title: "Post Title"
date: 2025-10-29
draft: false
tags: ["tech", "tutorial"]
categories: ["development"]
---
```

## Building for Production

Generate the static site:

```bash
hugo --minify
```

The generated site will be in the `public/` directory, ready for deployment.

## Deployment

The site can be deployed to various platforms:

- **Netlify** - Connect your repository and deploy automatically
- **Vercel** - Import your repository for instant deployment
- **GitHub Pages** - Use GitHub Actions for automated deployment
- **Any static hosting** - Upload the contents of the `public/` folder

## Features

- 📱 Fully responsive design
- 🌗 Dark/light mode support
- 🔍 Built-in search functionality
- 📊 Analytics support (Fathom, Umami, Google Analytics)
- 🚀 Optimized performance
- ♿ Accessibility-focused
- 📝 Syntax highlighting for code blocks
- 🔗 Social media integration

## Customization

### Color Scheme

The color scheme is set to `congo` in `config/_default/params.toml`. You can change it to one of the available schemes:

- `blowfish`
- `avocado`
- `congo`
- `fire`
- `ocean`
- `forest`
- And more...

### Appearance

Modify appearance settings in `config/_default/params.toml`:

```toml
colorScheme = "congo"
defaultAppearance = "light"
autoSwitchAppearance = false
```

## Resources

- [Hugo Documentation](https://gohugo.io/documentation/)
- [Blowfish Theme Documentation](https://blowfish.page/docs/)
- [Hugo Community Forum](https://discourse.gohugo.io/)

## License

Content is © Aline Avila. All rights reserved.
