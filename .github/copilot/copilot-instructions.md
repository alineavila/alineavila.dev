# GitHub Copilot Instructions

## Priority Guidelines

When generating code or content for this repository:

1. **Version Compatibility**: Always respect the exact versions detected in this Hugo project
2. **Content Structure**: Follow established Page Bundle patterns and archetype templates
3. **Codebase Patterns**: Maintain consistency with existing content organization and front matter structure
4. **Architectural Consistency**: Respect Hugo's content organization and the Blowfish theme configuration
5. **Code Quality**: Prioritize maintainability, clarity, and consistency with existing patterns

## Technology Version Detection

### Detected Technology Stack

**Hugo Static Site Generator**
- Version: `v0.152.1+extended+withdeploy`
- Build Date: `2025-10-22T19:10:44Z`
- Platform: `darwin/arm64`
- Distribution: `brew`
- **Important**: This is Hugo Extended edition (required for SCSS/SASS processing)

**Blowfish Theme**
- Version: `2.91.0`
- Module: `github.com/nunocoracao/blowfish/v2`
- Go Module Version: `go 1.16`
- Installation: Git submodule in `themes/blowfish/`

**Content Format**
- Markdown with YAML/TOML front matter
- Goldmark renderer (Hugo's default)
- Syntax highlighting via Chroma
- Math support via KaTeX (passthrough delimiters: `\[...\]`, `$$...$$`, `\(...\)`)

## Content Organization Architecture

### Directory Structure

```
content/
├── about.md              # Simple layout page
└── posts/                # Blog posts section
    ├── _index.md         # Section index (empty, uses defaults)
    └── [post-name]/      # Page Bundle structure
        ├── index.md      # Post content
        ├── featured.jpg  # Featured image
        └── *.png         # Additional assets
```

### Page Bundle Pattern

**Always use Page Bundles for blog posts**:
- Each post must be in its own folder: `content/posts/[post-name]/`
- Main content file must be named `index.md`
- Images and assets are placed in the same folder
- This allows self-contained, portable content units

**Example**:
```
content/posts/java-25/
├── index.md
├── featured.jpg
└── diagram.png
```

## Front Matter Standards

### Post Front Matter (YAML Format)

Based on `content/posts/first/index.md`, use this structure:

```yaml
---
title: "Post Title in Title Case"
description: "Brief description for meta tags and summaries"
categories: ["tech"]  # Single category preferred
tags: ["tag1", "tag2", "tag3"]  # Multiple tags allowed
date: 2025-10-27  # Publication date (YYYY-MM-DD)
publishDate: 2025-10-27  # Same as date for immediate publication
---
```

**Field Guidelines**:
- `title`: Use title case, descriptive and concise
- `description`: One-sentence summary for SEO and previews
- `categories`: Array format, typically single category `["tech"]`
- `tags`: Array format, lowercase, hyphen-separated for multi-word
- `date` and `publishDate`: ISO 8601 format (YYYY-MM-DD)
- **Do not include** `draft: true` unless explicitly needed
- **Do not include** `author` (set globally in config)

### Simple Page Front Matter

For non-post pages like `about.md`:

```yaml
---
title: "Page Title"
layout: "simple"  # Use "simple" for clean pages without sidebar
---
```

## Archetype Templates

### Posts Archetype (`archetypes/posts/index.md`)

When creating new posts with `hugo new posts/[name]/index.md`, this template is used:

```markdown
---
title: "{{ replace .Name "-" " " | title }}"
description: ""
date: {{ .Date }}
publishDate: {{ .Date }}
draft: true
categories: []
tags: []
---

<!--
Escreva seu post abaixo. Este archetype cria um Page Bundle (index.md)
para que você possa adicionar imagens e outros assets na mesma pasta.
-->
```

**When generating new post content**:
1. Replace title with actual post title
2. Add meaningful description
3. Change `draft: true` to remove it (or keep for drafts)
4. Add appropriate categories and tags
5. Remove the HTML comment placeholder

## Blowfish Shortcodes

Based on analysis of `content/posts/first/index.md`, these shortcodes are used:

### Lead Shortcode
Highlights the introduction of a post:

```markdown
{{< lead >}}
Texto de introdução destacado com estilo especial.
{{< /lead >}}
```

### Alert Shortcode
Creates attention-grabbing notices:

```markdown
{{< alert >}}
Nota importante ou aviso para os leitores.
{{< /alert >}}
```

### Other Common Blowfish Shortcodes

While not present in the current codebase, Blowfish supports:

- `{{< badge >}}text{{< /badge >}}` - Inline badges
- `{{< button href="url" >}}Text{{< /button >}}` - Styled buttons
- `{{< figure src="image.jpg" alt="Alt text" caption="Caption" >}}` - Enhanced images
- `{{< katex >}}` - Math formulas

**Rule**: Only use shortcodes that are documented in Blowfish theme or exist in the codebase.

## Content Writing Standards

### Structure and Formatting

Based on `content/posts/first/index.md`:

1. **Lead Section**: Start with a `{{< lead >}}` shortcode for engaging introduction
2. **Section Headers**: Use `##` for main sections, `###` for subsections
3. **Emoji Usage**: Use emojis sparingly in headers for visual appeal (e.g., `✨`, `🧭`, `🔗`)
4. **Code Blocks**: Use triple backticks with language identifiers:

```java
// Example code with syntax highlighting
public class Example {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

5. **Lists**: Use numbered lists for steps, bullet points for features
6. **Alerts**: Use `{{< alert >}}` for disclaimers, warnings, or important notes

### Tone and Style

Based on existing content:

- **Audience**: Beginners and intermediate developers
- **Language**: Portuguese (pt-BR) for content, even though config is English
- **Tone**: Friendly, educational, practical
- **Approach**: 
  - Start with "Resumo rápido" (Quick summary)
  - Explain "O que isso significa para você" (What this means for you)
  - Include practical code examples
  - End with "Links úteis" (Useful links)

### Content Template Pattern

Follow this structure (from `first/index.md`):

```markdown
{{< lead >}}
Engaging introduction with emoji
{{< /lead >}}

{{< alert >}}
Transparency note or important disclaimer
{{< /alert >}}

## Resumo rápido (em 1 minuto) ✨
- Bullet points
- Key takeaways

## O que isso significa para você 🧭
Practical explanation

## [Main Topic] na prática 🧩
Code examples and demonstrations

## Links úteis 🔗
- [Resource 1](url)
- [Resource 2](url)
```

## Hugo Configuration

### Site Configuration (`config/_default/hugo.toml`)

**Key Settings**:
- `theme = "blowfish"`
- `baseURL = "https://alineavila.dev/"`
- `defaultContentLanguage = "en"` (but content is in Portuguese)
- `enableRobotsTXT = true`
- `enableEmoji = true`
- `enableGitInfo = true` (uses Git commit timestamps for lastmod)

### Taxonomies

```toml
[taxonomies]
  tag = "tags"
  category = "categories"
  author = "authors"
  series = "series"
```

**Usage in Posts**:
- Always include `tags` and `categories` in front matter
- Use lowercase, hyphen-separated values
- Categories: broad classification (usually "tech")
- Tags: specific topics (e.g., "java", "jdk25", "tutorial")

### Markup Configuration (`markup.toml`)

**Goldmark Settings**:
- `wrapStandAloneImageWithinParagraph = false` - Images stand alone
- `unsafe = true` - Allows raw HTML in Markdown
- Math passthrough enabled for KaTeX

**Syntax Highlighting**:
- `noClasses = false` - Uses CSS classes for styling
- Powered by Chroma

**Table of Contents**:
- `startLevel = 2` - Starts at `##` headers
- `endLevel = 4` - Includes up to `####` headers

## Theme Configuration

### Appearance (`config/_default/params.toml`)

**Current Settings**:
- Color scheme: `congo`
- Default appearance: `light`
- No automatic appearance switching
- Search: enabled
- Code copy: enabled

### Author Information

Defined in `config/_default/languages.en.toml`:

```toml
[params.author]
  name = "Aline Ávila"
  email = "aline.avila01@gmail.com"
  image = "https://avatars.githubusercontent.com/u/24813256?..."
  imageQuality = 96
  headline = "Desenvolvedora de software aprendendo em público..."
  bio = "🚫🤖 Conteúdo 100% humano."
```

**Important**: Author information is centralized in configuration, not in individual posts.

### Homepage Layout

```toml
[homepage]
  layout = "profile"  # Profile-style homepage
  showRecent = true
  showRecentItems = 8
  cardView = true
```

### Article Configuration

```toml
[article]
  showDate = true
  showDateUpdated = false  # Git-based updates not shown
  showAuthor = true
  showReadingTime = true
  showWordCount = true
  showTableOfContents = false  # TOC disabled by default
```

## Image Handling

### Featured Images

Place a file named `featured.jpg` (or `.png`) in the post's Page Bundle folder:

```
content/posts/my-post/
├── index.md
└── featured.jpg  # Automatically detected as featured image
```

### Inline Images

Reference images relative to the post folder:

```markdown
![Alt text](image.png)
```

Or use the figure shortcode for enhanced images:

```markdown
{{< figure src="diagram.png" alt="Architecture diagram" caption="System architecture overview" >}}
```

## Markdown Best Practices

### Code Blocks

Always specify the language for syntax highlighting:

````markdown
```java
public class Example {
    // Java code
}
```

```bash
hugo server -D
```

```yaml
---
key: value
---
```
````

### Escaping Code in Markdown

When showing code examples within code blocks (like in the post about Java), use four backticks:

`````markdown
````markdown
```java
// Example within example
```
````
`````

### Links

Use descriptive link text:

```markdown
[Hugo Documentation](https://gohugo.io/documentation/)
```

Not:
```markdown
[click here](https://example.com)
```

## Command Line Workflows

### Creating New Content

```bash
# Create a new post with archetype
hugo new posts/post-name/index.md

# Create content for other sections
hugo new about.md
```

### Development Server

```bash
# Start server with drafts
hugo server -D

# Start server without drafts (production preview)
hugo server

# Server will be at http://localhost:1313
```

### Building for Production

```bash
# Build with minification
hugo --minify

# Output will be in public/ directory
```

### Theme Management

```bash
# Initialize theme submodule (first time)
git submodule update --init --recursive

# Update theme to latest version
cd themes/blowfish
git pull origin main
cd ../..
git add themes/blowfish
git commit -m "Update Blowfish theme"
```

## Git Configuration

### Last Modified Dates

The site uses Git commit information for last modification dates:

```toml
enableGitInfo = true

[frontmatter]
  lastmod = [":git", "lastmod", "date", "publishDate"]
```

**Implication**: When you commit a file, its last modified date is automatically updated based on Git history.

## File Naming Conventions

### Post Folders

- Use lowercase
- Use hyphens for word separation
- Be descriptive but concise
- Example: `java-25-overview`, `spec-driven-development`

### Image Files

- Use lowercase
- Use hyphens or underscores
- Be descriptive
- Examples: `featured.jpg`, `architecture-diagram.png`, `code-example.png`

## Content Strategy

### Post Topics

Based on existing content, focus areas include:

- Programming language updates and features
- Software development practices
- Technical tutorials with practical examples
- Technology explanations for beginners

### Target Audience

- Portuguese-speaking developers
- Beginners and intermediate levels
- People interested in learning in public
- Readers seeking practical, example-driven content

### Content Principles

1. **100% Human Content**: "🚫🤖 Conteúdo 100% humano"
2. **Learning in Public**: "aprendendo em público"
3. **Practical Focus**: Always include code examples
4. **Beginner-Friendly**: Explain concepts clearly
5. **Transparency**: Use disclaimers when appropriate

## Static Assets

### Favicon and Icons

Located in `static/`:
- `favicon.ico`
- `android-chrome-192x192.png`
- `android-chrome-512x512.png`
- `apple-touch-icon.png`
- `favicon-16x16.png`
- `favicon-32x32.png`

These are served directly from the site root.

## Deployment

### Output Directory

- Hugo generates static files in `public/`
- This directory should be ignored in `.gitignore`
- Deploy the contents of `public/` to your hosting provider

### URLs

- Base URL: `https://alineavila.dev/`
- Posts appear at: `https://alineavila.dev/posts/[post-name]/`
- Tags: `https://alineavila.dev/tags/[tag-name]/`
- Categories: `https://alineavila.dev/categories/[category-name]/`

## Troubleshooting

### Common Issues

1. **Theme not appearing**: Ensure submodule is initialized
   ```bash
   git submodule update --init --recursive
   ```

2. **SCSS errors**: Ensure Hugo Extended is installed
   ```bash
   hugo version  # Should show "extended"
   ```

3. **Images not showing**: Check they are in the correct Page Bundle folder

4. **Post not appearing**: Check for `draft: true` in front matter

## Best Practices Summary

1. ✅ **Always use Page Bundles** for blog posts
2. ✅ **Include front matter** with title, description, categories, tags, and dates
3. ✅ **Start posts with** `{{< lead >}}` shortcode
4. ✅ **Use proper** syntax highlighting in code blocks
5. ✅ **Write in Portuguese** for Brazilian audience
6. ✅ **Include practical examples** and code snippets
7. ✅ **Place images** in the same folder as `index.md`
8. ✅ **Use emojis sparingly** for visual appeal
9. ✅ **Test locally** with `hugo server -D` before committing
10. ✅ **Follow Git best practices** for automatic lastmod updates

## Additional Resources

- [Hugo Documentation](https://gohugo.io/documentation/)
- [Blowfish Theme Documentation](https://blowfish.page/docs/)
- [Goldmark (Markdown Parser)](https://github.com/yuin/goldmark)
- [KaTeX Math Rendering](https://katex.org/)

---

**Last Updated**: Generated automatically from codebase analysis
**Hugo Version**: v0.152.1+extended
**Theme Version**: Blowfish 2.91.0
