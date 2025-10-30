# Create Blog Post Structure

## Description
Creates a complete blog post structure following the specifications in `/specs/spec-process-blog-post-creation.md` and `/specs/spec-design-content-structure.md`. This prompt generates ONLY the scaffolding (folders, files, headers, placeholders) - content must be written by the human author.

## Instructions

**CRITICAL: Structure Only - No Content**
- Generate folder structure, files, front matter, section headers, and [TODO] placeholders
- DO NOT write actual content (paragraphs, code examples, explanations, links)
- All substantive content must be marked with specific [TODO: ...] placeholders
- Ensure 100% human-written content by leaving clear placeholders for author

### Step 1: Gather Information

Ask the user for:
1. **Post slug** (lowercase, hyphens, ≤50 chars) - This will be the folder name
2. **Post title** (40-60 chars, title case)
3. **Short description** (120-160 chars)
4. **3-5 tags** (lowercase, hyphen-separated)
5. **Main topic category** (typically "tech")
6. **Expected publication date** (YYYY-MM-DD format)

### Step 2: Validate Input

Before creating files, validate:
- [ ] Slug uses only lowercase, numbers, and hyphens
- [ ] Slug is ≤ 50 characters
- [ ] Title is 40-60 characters
- [ ] Description is 120-160 characters
- [ ] 3-5 tags provided
- [ ] Date is in YYYY-MM-DD format

If validation fails, ask user to correct the input.

### Step 3: Create File Structure

Create the following structure:

```
content/posts/[slug]/
├── index.md              # Main post file with structure
└── [remind user to add featured.jpg - 1200x630px, <200KB]
```

### Step 4: Generate index.md with Placeholders

Create `content/posts/[slug]/index.md` with this exact structure:

```markdown
---
title: "[user-provided title]"
description: "[user-provided description]"
categories: ["[user-provided category]"]
tags: ["[user-provided tags]"]
date: [user-provided date]
publishDate: [user-provided date]
draft: true
---

{{< lead >}}
[TODO: Write engaging 1-2 sentence introduction that hooks the reader. End with relevant emoji] 🚀
{{< /lead >}}

{{< alert >}}
[TODO: Optional - Add disclaimer, transparency note, or important context. Remove this section if not needed]
{{< /alert >}}

## Resumo rápido (em 1 minuto) ✨
- [TODO: Key takeaway 1 - What is the main concept?]
- [TODO: Key takeaway 2 - Why does it matter?]
- [TODO: Key takeaway 3 - When should you use it?]
- [TODO: Key takeaway 4 - What's the core benefit?]
- [TODO: Optional - Add 5th or 6th point if needed]

## O que isso significa para você 🧭
[TODO: Write 1-2 paragraphs explaining:
- Why this topic matters to the reader specifically
- How it solves a real problem they face
- What practical benefit they'll gain
- Keep beginner-friendly, avoid jargon]

## [TODO: Main topic name] na prática 🧩

### [TODO: Subtopic 1 - e.g., "Conceitos fundamentais", "Como funciona", "Primeiros passos"]
[TODO: Write clear explanation with 1-2 paragraphs]

```[TODO: programming-language]
// TODO: Add brief comment explaining what this code does
[TODO: Add code example - ensure it's runnable]
```

[TODO: Explain the code above - what it does, why it works, key points to notice]

### [TODO: Subtopic 2 - e.g., "Exemplos práticos", "Casos de uso", "Boas práticas"]
[TODO: Write additional content with examples or use cases]

### [TODO: Subtopic 3 - Optional, add more sections as needed]
[TODO: Write content]

## [TODO: Optional section with emoji] 🎯
[TODO: Add additional sections as needed for your specific post type:
- For tutorials: "Erros comuns 🚫", "Dicas avançadas 💡"
- For news: "Mudanças importantes 📢", "Impacto na comunidade 🌍"
- For concepts: "Quando usar 🤔", "Alternativas 🔄"]

## Links úteis 🔗
- [TODO: Resource 1 - Official documentation or main reference](https://TODO.com)
- [TODO: Resource 2 - Tutorial, guide, or detailed explanation](https://TODO.com)
- [TODO: Resource 3 - Additional reading, video, or tool](https://TODO.com)
- [TODO: Optional - Add more relevant links]
```

### Step 5: Provide Next Steps

After creating the files, tell the user:

1. ✅ **Structure created** at `content/posts/[slug]/index.md`
2. 📸 **Add featured image**: Place `featured.jpg` (1200x630px, <200KB) in the post folder
3. ✍️ **Write content**: Replace all `[TODO: ...]` markers with your content
4. 🧪 **Preview**: Run `hugo server -D` to preview your post
5. 📋 **Validate**: Check against the validation checklist in `/specs/spec-process-blog-post-creation.md` (Section 10)
6. 🚀 **Publish**: When ready, remove `draft: true` from front matter

### Step 6: Remind About Content Guidelines

Remind the user to follow these content principles when writing:
- ✅ Write in Portuguese (pt-BR)
- ✅ Use friendly, educational tone
- ✅ Target beginner to intermediate audience
- ✅ Include practical examples over theory
- ✅ Add personal perspective and insights
- ✅ Ensure all code blocks specify language
- ✅ Keep it 100% human-written (🚫🤖 Conteúdo 100% humano)

## References

This prompt follows specifications from:
- `/specs/spec-process-blog-post-creation.md` - Complete process requirements
- `/specs/spec-design-content-structure.md` - Visual design and structure standards
- `/.github/copilot/copilot-instructions.md` - GitHub Copilot integration guidelines

## Example Usage

**User says:**
> "Crie estrutura para um post sobre Python decorators"

**Copilot asks:**
> Para criar a estrutura do post, preciso de algumas informações:
> 1. Post slug (ex: python-decorators-guia-pratico)
> 2. Título (40-60 chars)
> 3. Descrição (120-160 chars)
> 4. 3-5 tags
> 5. Data de publicação

**User provides info, Copilot:**
1. Validates input
2. Creates `/content/posts/python-decorators-guia-pratico/index.md`
3. Generates structure with [TODO] placeholders
4. Reminds user to add featured.jpg
5. Provides next steps for content creation

---

**Version**: 1.0
**Created**: 2025-10-30
**Last Updated**: 2025-10-30
