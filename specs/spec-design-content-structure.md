---
title: Content Structure and Visual Design Specification
version: 1.0
date_created: 2025-10-30
last_updated: 2025-10-30
owner: Aline Ávila
tags: [design, content, structure, typography, visual-hierarchy]
---

# Introduction

This specification defines the visual design, typography, and structural patterns for blog content on alineavila.dev. It establishes standards for visual hierarchy, emoji usage, formatting conventions, and presentation patterns to ensure consistent, scannable, and engaging content across all posts.

## 1. Purpose & Scope

### Purpose
Define visual and structural design standards that:
- Create consistent visual hierarchy across all posts
- Optimize content scannability and readability
- Establish clear patterns for different content types
- Enable quick comprehension for busy readers
- Maintain brand identity and voice
- Guide AI tools in generating properly formatted content

### Scope
This specification applies to:
- All blog post content structure and formatting
- Typography and text hierarchy
- Emoji usage and placement
- Visual elements (headings, lists, code blocks, alerts)
- Content patterns for different post types (tutorials, news, explainers)

### Out of Scope
- Theme-level CSS customization (handled by Blowfish theme)
- Site-wide navigation and layout (handled by Hugo configuration)
- Infrastructure and deployment (covered in process specification)

### Audience
- Content creators and authors
- GitHub Copilot and AI-assisted tools
- Design reviewers and maintainers

## 2. Definitions

| Term | Definition |
|------|------------|
| **Visual Hierarchy** | Organization of content to show relative importance through size, color, spacing |
| **Scannability** | Ease with which readers can quickly extract key information |
| **Lead Section** | Opening hook that captures reader attention |
| **Alert Box** | Highlighted section for important notices or disclaimers |
| **Summary Section** | Condensed bullet-point overview of key points |
| **Code Block** | Formatted section containing programming code with syntax highlighting |
| **Emoji Icon** | Unicode character used for visual emphasis (e.g., ✨, 🚀, 🧭) |
| **Title Case** | Capitalization style where major words are capitalized |
| **Byline** | Author attribution and metadata displayed with post |

## 3. Requirements, Constraints & Guidelines

### Visual Hierarchy Requirements

- **REQ-001**: Content MUST follow a clear visual hierarchy: Lead → Summary → Main Content → Resources
- **REQ-002**: Headings MUST use semantic HTML levels (H2 for sections, H3 for subsections)
- **REQ-003**: No heading level may be skipped (no H2 → H4 without H3)
- **REQ-004**: The first content after front matter MUST be the Lead section
- **REQ-005**: Main sections MUST use H2 (`##`) with relevant emoji
- **REQ-006**: Subsections MUST use H3 (`###`) without emoji

### Typography Requirements

- **REQ-007**: Titles MUST use title case (capitalize major words)
- **REQ-008**: Body text MUST use sentence case
- **REQ-009**: Code inline MUST use backticks: \`code\`
- **REQ-010**: Emphasis MUST use *italic* (single asterisk) or **bold** (double asterisk)
- **REQ-011**: Lists MUST use consistent formatting (either `-` or `*` for bullets, never mixed)

### Emoji Usage Requirements

- **REQ-012**: Emojis MUST appear only in H2 section headers
- **REQ-013**: Emojis MUST NOT appear in body text
- **REQ-014**: Emojis MUST NOT appear in H3 subsection headers
- **REQ-015**: Each main section MUST have exactly one relevant emoji at the end of the header
- **REQ-016**: Emoji selection MUST be semantically relevant to section content
- **REQ-017**: The following emoji assignments MUST be used for standard sections:
  - "Resumo rápido" → ✨
  - "O que isso significa para você" → 🧭
  - "na prática" → 🧩
  - "Links úteis" → 🔗

### Shortcode Requirements

- **REQ-018**: Lead section MUST use `{{< lead >}}` shortcode
- **REQ-019**: Lead content MUST be 1-2 sentences maximum
- **REQ-020**: Lead MUST end with an emoji (🚀, 🎯, ⚡, 🌟 recommended)
- **REQ-021**: Disclaimers and important notes MUST use `{{< alert >}}` shortcode
- **REQ-022**: Alert shortcode MUST appear immediately after Lead section (if used)

### Code Block Requirements

- **REQ-023**: Code blocks MUST specify the language identifier
- **REQ-024**: Code blocks MUST include brief explanatory comment
- **REQ-025**: Code examples MUST be properly indented and formatted
- **REQ-026**: Long code examples SHOULD be broken into logical sections with explanations
- **REQ-027**: Output or expected results SHOULD be included as comments when relevant

### List Formatting Requirements

- **REQ-028**: Summary section (Resumo rápido) MUST use unordered list with 4-6 items
- **REQ-029**: Each summary item MUST be a single, scannable point
- **REQ-030**: Resources section (Links úteis) MUST use unordered list
- **REQ-031**: Links MUST use descriptive text, not "click here" or URLs

### Constraints

- **CON-001**: Maximum consecutive paragraphs without break: 3
- **CON-002**: Maximum bullet points in summary section: 6
- **CON-003**: Minimum bullet points in summary section: 4
- **CON-004**: Lead section maximum: 2 sentences or 140 characters
- **CON-005**: Emoji varieties per post: limit to 8 different emojis
- **CON-006**: Code block lines: recommend max 50 lines, split if longer

### Guidelines

- **GUD-001**: Use whitespace generously to improve scannability
- **GUD-002**: Break up long text blocks with subheadings
- **GUD-003**: Use bold for important terms on first mention
- **GUD-004**: Use code formatting for technical terms and file names
- **GUD-005**: Include blank line before and after headings
- **GUD-006**: Include blank line before and after code blocks
- **GUD-007**: Prefer short paragraphs (2-4 sentences) over long blocks
- **GUD-008**: Use consistent emoji style (prefer simple, universal emojis)

### Design Patterns

- **PAT-001**: Tutorial Pattern: Problem → Solution → Example → Explanation → Practice
- **PAT-002**: News Pattern: What Changed → Impact → Examples → Migration → Resources
- **PAT-003**: Explainer Pattern: Question → Context → Deep Dive → Use Cases → Resources
- **PAT-004**: Code-Heavy Pattern: Brief intro → Code → Explanation → Variations → Summary

## 4. Interfaces & Data Contracts

### Content Structure Template

```markdown
{{< lead >}}
[1-2 sentence hook with ending emoji] 🚀
{{< /lead >}}

{{< alert >}}
[Optional: Important context or disclaimer]
{{< /alert >}}

## Resumo rápido (em 1 minuto) ✨
- [Concise point 1]
- [Concise point 2]
- [Concise point 3]
- [Concise point 4]
- [Optional: point 5-6]

## O que isso significa para você 🧭
[1-2 paragraphs of practical relevance]

## [Main Topic] na prática 🧩

[Introduction paragraph]

### [Subtopic 1]
[Content with example]

```language
// Brief explanation
[code example]
```

[Explanation of code behavior and key points]

### [Subtopic 2]
[Additional content and examples]

## [Additional Sections] [Relevant Emoji]

[Content following same pattern]

## Links úteis 🔗
- [Resource Title](url) - Brief description
- [Resource Title](url) - Brief description
- [Resource Title](url) - Brief description
```

### Emoji Mapping

| Section Type | Recommended Emoji | Alternative Options |
|--------------|-------------------|---------------------|
| Quick Summary | ✨ | ⚡ 💡 🎯 |
| Practical Relevance | 🧭 | 💭 🎓 📍 |
| Practical Examples | 🧩 | 🔧 ⚙️ 🛠️ |
| Resources/Links | 🔗 | 📚 📖 🌐 |
| Performance | ⚙️ | ⚡ 🚀 💨 |
| Code/Technical | 💻 | 🖥️ ⌨️ 🔤 |
| Tips/Hints | 💡 | 🔑 ⭐ 💎 |
| Security | 🔒 | 🛡️ 🔐 🚨 |
| Testing | 🧪 | ✅ 🎯 🔍 |
| Database | 💾 | 🗄️ 📊 💽 |
| API/Network | 🌐 | 🔌 📡 🌍 |
| Documentation | 📚 | 📝 📄 📋 |
| Architecture | 🏗️ | 🏛️ 🗺️ 📐 |
| Deployment | 🚀 | 📦 ☁️ 🌍 |
| Cleanup/Refactor | 🧹 | ♻️ 🔄 ✨ |
| Warning/Caution | ⚠️ | 🚨 ⛔ 🛑 |
| Success/Done | ✅ | ✔️ 🎉 🏆 |

### Code Block Format

````markdown
### Descriptive Subheading

[Brief introduction to what this code does]

```language
// Comment explaining purpose or key concept
[actual code here]
// Optional: comment on important lines
[more code]
```

[Explanation of what the code does, key points to notice, and practical implications]
````

### Alert Box Patterns

```markdown
<!-- Transparency/Disclaimer -->
{{< alert >}}
Nota de transparência: [disclosure about sources, assumptions, or limitations]
{{< /alert >}}

<!-- Warning/Caution -->
{{< alert >}}
⚠️ Atenção: [important warning or cautionary note]
{{< /alert >}}

<!-- Context/Prerequisites -->
{{< alert >}}
Este tutorial assume [prerequisites or required knowledge]
{{< /alert >}}
```

## 5. Acceptance Criteria

### Visual Hierarchy

- **AC-001**: Given a published post, When viewing the content, Then the Lead section must be visually distinct and appear first
- **AC-002**: Given post sections, When ordered on the page, Then they must follow: Lead → Alert (optional) → Summary → Main Content → Resources
- **AC-003**: Given heading levels, When scanning the document, Then no heading level may be skipped in the hierarchy

### Typography

- **AC-004**: Given a post title, When displayed, Then all major words must be capitalized (title case)
- **AC-005**: Given inline code references, When viewing text, Then they must be wrapped in backticks and visually distinct
- **AC-006**: Given a list, When formatting, Then all items must use consistent markers (all `-` or all `*`)

### Emoji Usage

- **AC-007**: Given H2 headers, When checking emoji placement, Then each must have exactly one emoji at the end
- **AC-008**: Given H3 headers, When checking emoji usage, Then none may contain emojis
- **AC-009**: Given body paragraphs, When scanning for emojis, Then none may contain emojis except in shortcodes
- **AC-010**: Given the "Resumo rápido" section, When checking emoji, Then it must use ✨
- **AC-011**: Given the "Links úteis" section, When checking emoji, Then it must use 🔗

### Shortcodes

- **AC-012**: Given a post, When checking opening content, Then it must use `{{< lead >}}` shortcode
- **AC-013**: Given a Lead section, When checking length, Then it must not exceed 2 sentences or 140 characters
- **AC-014**: Given a Lead section, When checking emoji, Then it must end with exactly one emoji
- **AC-015**: Given a post with disclaimers, When checking structure, Then `{{< alert >}}` must appear immediately after Lead

### Code Blocks

- **AC-016**: Given a code block, When viewing the source, Then it must specify language identifier
- **AC-017**: Given a code example, When checking comments, Then it must include explanatory comment in Portuguese
- **AC-018**: Given a code block, When checking formatting, Then code must be properly indented
- **AC-019**: Given a long code example (>50 lines), When reviewing, Then it should be split with explanatory text

### Lists

- **AC-020**: Given the Resumo rápido section, When counting items, Then there must be 4-6 bullet points
- **AC-021**: Given summary bullet points, When checking content, Then each must be a single, scannable statement
- **AC-022**: Given the Links úteis section, When checking links, Then each must use descriptive text, not URLs

### Readability

- **AC-023**: Given consecutive paragraphs, When counting, Then there must not be more than 3 without a break (heading, list, code block)
- **AC-024**: Given a paragraph, When checking length, Then it should contain 2-4 sentences ideally
- **AC-025**: Given headings, When checking spacing, Then there must be blank lines before and after
- **AC-026**: Given code blocks, When checking spacing, Then there must be blank lines before and after

## 6. Test Automation Strategy

### Visual Validation

**Manual Review Checklist** (cannot be fully automated):
- Visual hierarchy flows logically
- Content is scannable at a glance
- Emoji usage is appropriate and consistent
- Code examples are clear and properly formatted
- Whitespace improves readability

### Automated Checks

**Linting Rules** (markdownlint configuration):
```json
{
  "MD001": true,  // Heading levels increment by one
  "MD003": { "style": "atx" },  // Use # style headings
  "MD004": { "style": "dash" },  // Use - for unordered lists
  "MD012": { "maximum": 1 },  // No multiple blank lines
  "MD022": true,  // Headings surrounded by blank lines
  "MD031": true,  // Code blocks surrounded by blank lines
  "MD032": true,  // Lists surrounded by blank lines
  "MD047": true  // Files end with newline
}
```

**Custom Validation Script** (pseudo-code):
```python
def validate_content_structure(markdown_file):
    checks = {
        'has_lead_shortcode': False,
        'lead_after_frontmatter': False,
        'has_summary_section': False,
        'summary_has_sparkle_emoji': False,
        'has_links_section': False,
        'links_has_chain_emoji': False,
        'h2_have_emojis': True,
        'h3_no_emojis': True,
        'code_blocks_have_language': True,
        'no_body_emojis': True
    }
    
    # Parse and validate
    # Return report with pass/fail for each check
```

### Coverage Requirements

- 100% of posts must pass heading hierarchy check
- 100% of posts must have Lead and Summary sections
- 100% of code blocks must specify language
- 100% of H2 sections must have emoji
- 0% of H3 sections may have emoji
- 0% of body paragraphs may have emoji (except in shortcodes)

## 7. Rationale & Context

### Why Strict Visual Hierarchy?
- Improves scannability for time-constrained readers
- Enables quick decision: "Is this post relevant to me?"
- Creates predictable reading experience across all posts
- Helps search engines understand content structure
- Makes content more accessible for screen readers

### Why Emoji in Headers Only?
- Creates visual landmarks for quick navigation
- Avoids emoji overuse which can appear unprofessional
- Maintains clean, readable body text
- Ensures emojis serve functional purpose (wayfinding) not decoration
- Improves accessibility (emojis in headers are less disruptive)

### Why Mandatory Summary Section?
- Respects reader's time ("Can I learn this in 1 minute?")
- Provides immediate value even if reader doesn't read full post
- Improves SEO with scannable, keyword-rich bullets
- Creates clear promise/contract with reader
- Enables readers to decide if full post is worth reading

### Why Lead Shortcode?
- Creates consistent, engaging opening across all posts
- Visually distinct section captures attention
- Forces authors to craft compelling hook
- Theme-styled element maintains design consistency
- Encourages concise, punchy introductions

### Why Strict Code Formatting?
- Ensures all examples are understandable without running them
- Language specification enables proper syntax highlighting
- Comments in Portuguese make code accessible to target audience
- Proper formatting signals code quality and professionalism
- Makes examples easy to copy and adapt

### Why Link Description Requirements?
- "Click here" links are bad for accessibility
- Descriptive text improves SEO
- Users can decide if link is relevant without clicking
- Better UX (know what to expect before click)
- Screen reader friendly

## 8. Dependencies & External Integrations

### External Systems

- **EXT-001**: Blowfish Theme Shortcodes - Required for Lead and Alert rendering
- **EXT-002**: Hugo Goldmark Renderer - Required for Markdown processing

### Third-Party Services

- **SVC-001**: Emoji Unicode Standard - Required for cross-platform emoji rendering
- **SVC-002**: Chroma Syntax Highlighter - Required for code block styling

### Infrastructure Dependencies

- **INF-001**: CSS Framework - Blowfish theme provides typography and spacing
- **INF-002**: Web Fonts - Theme handles font loading for readability

### Data Dependencies

- **DAT-001**: Blowfish Shortcode Templates - Required for consistent Lead/Alert rendering
- **DAT-002**: Chroma Language Definitions - Required for syntax highlighting support

### Technology Platform Dependencies

- **PLT-001**: Hugo Goldmark v1.4+ - Required for proper Markdown extension support
- **PLT-002**: Modern Browser - Required for emoji rendering (fallback to text)

### Compliance Dependencies

- **COM-001**: WCAG 2.1 - Heading hierarchy and semantic HTML requirements
- **COM-002**: Unicode Emoji Standard - Cross-platform emoji compatibility

## 9. Examples & Edge Cases

### Example: Perfect Visual Hierarchy

```markdown
---
title: "TypeScript Generics: Guia Completo"
description: "Domine generics em TypeScript com exemplos práticos e casos de uso reais."
categories: ["tech"]
tags: ["typescript", "generics", "tipos", "tutorial"]
date: 2025-10-30
publishDate: 2025-10-30
---

{{< lead >}}
Generics deixam seu código TypeScript mais flexível e type-safe! 🎯
{{< /lead >}}

{{< alert >}}
Este tutorial assume conhecimento básico de TypeScript e tipos.
{{< /alert >}}

## Resumo rápido (em 1 minuto) ✨
- Generics permitem criar componentes reutilizáveis e type-safe
- Sintaxe: `<T>` onde T é um placeholder para qualquer tipo
- Úteis em arrays, funções, classes e interfaces
- Podem ter constraints usando `extends`
- TypeScript infere tipos automaticamente na maioria dos casos

## O que isso significa para você 🧭
Se você já duplicou código só para mudar tipos, generics são a solução. Escreva uma vez, use com qualquer tipo, mantendo segurança de tipos.

## Generics básicos na prática 🧩

### Função genérica simples

```typescript
// Generic permite que a função trabalhe com qualquer tipo
function primeiroElemento<T>(array: T[]): T | undefined {
    return array[0];
}

// TypeScript infere o tipo automaticamente
const numero = primeiroElemento([1, 2, 3]); // number | undefined
const texto = primeiroElemento(['a', 'b']); // string | undefined
```

A função `primeiroElemento` funciona com qualquer tipo de array, mas mantém type-safety completo.

### Interface genérica

```typescript
// Interface reutilizável para respostas de API
interface ApiResponse<T> {
    data: T;
    status: number;
    message: string;
}

// Uso com diferentes tipos de dados
const userResponse: ApiResponse<User> = {
    data: { id: 1, name: 'Maria' },
    status: 200,
    message: 'Success'
};

const postsResponse: ApiResponse<Post[]> = {
    data: [{ id: 1, title: 'Post 1' }],
    status: 200,
    message: 'Success'
};
```

### Generic com constraint

```typescript
// Constraint: T deve ter propriedade length
function imprimirTamanho<T extends { length: number }>(item: T): void {
    console.log(`Tamanho: ${item.length}`);
}

imprimirTamanho('texto'); // ✅ string tem length
imprimirTamanho([1, 2, 3]); // ✅ array tem length
imprimirTamanho({ length: 10 }); // ✅ objeto com length
// imprimirTamanho(123); // ❌ Erro: number não tem length
```

O constraint `extends { length: number }` garante que apenas tipos com `length` podem ser usados.

## Casos de uso avançados 🚀

### Repository Pattern genérico

```typescript
// Repository reutilizável para qualquer entidade
class Repository<T extends { id: number }> {
    private items: T[] = [];

    add(item: T): void {
        this.items.push(item);
    }

    findById(id: number): T | undefined {
        return this.items.find(item => item.id === id);
    }

    getAll(): T[] {
        return [...this.items];
    }
}

// Uso com diferentes entidades
interface User { id: number; name: string; }
interface Product { id: number; title: string; price: number; }

const userRepo = new Repository<User>();
const productRepo = new Repository<Product>();

userRepo.add({ id: 1, name: 'João' });
productRepo.add({ id: 1, title: 'Laptop', price: 3000 });
```

## Erros comuns e como evitar ⚠️

### Erro 1: Esquecer o constraint

```typescript
// ❌ Problema: T pode não ter toUpperCase
function maiuscula<T>(texto: T): T {
    return texto.toUpperCase(); // Erro de compilação
}

// ✅ Solução: Adicionar constraint
function maiuscula<T extends string>(texto: T): Uppercase<T> {
    return texto.toUpperCase() as Uppercase<T>;
}
```

### Erro 2: Generic muito genérico

```typescript
// ❌ Muito vago: não adiciona valor
function processar<T>(data: T): T {
    return data; // Apenas retorna o input
}

// ✅ Melhor: ser específico sobre o que precisa
function processar<T extends { processable: boolean }>(data: T): T {
    if (!data.processable) {
        throw new Error('Não processável');
    }
    return data;
}
```

## Quando usar (e quando não usar) 💡

**Use generics quando:**
- Precisa reutilizar lógica para diferentes tipos
- Quer manter type-safety com flexibilidade
- Está criando bibliotecas ou utilitários
- Tipos têm estrutura similar mas dados diferentes

**Não use quando:**
- Tipos são completamente diferentes
- Lógica varia significativamente por tipo
- Aumenta complexidade sem benefício claro
- Type assertion resolveria de forma mais simples

## Links úteis 🔗
- [TypeScript Handbook: Generics](https://www.typescriptlang.org/docs/handbook/2/generics.html)
- [TypeScript Deep Dive: Generics](https://basarat.gitbook.io/typescript/type-system/generics)
- [Type Challenges](https://github.com/type-challenges/type-challenges) - Pratique generics
```

### Edge Case: Section Without Proper Emoji

```markdown
## Performance e Otimização  <!-- ❌ Missing emoji -->

## Performance e Otimização ⚙️  <!-- ✅ Correct -->
```

### Edge Case: Emoji in Wrong Place

```markdown
⚡ ## Performance e Otimização  <!-- ❌ Emoji before heading -->

## ⚡ Performance e Otimização  <!-- ❌ Emoji at start -->

## Performance e Otimização ⚡  <!-- ✅ Correct -->
```

### Edge Case: Body Text with Emoji

```markdown
<!-- ❌ Wrong: Emoji in body -->
Generics são muito úteis! 🎉 Eles permitem...

<!-- ✅ Correct: No emoji in body -->
Generics são muito úteis! Eles permitem...
```

### Edge Case: Code Block Without Language

````markdown
<!-- ❌ Wrong: No language specified -->
```
function example() {
    return true;
}
```

<!-- ✅ Correct: Language specified -->
```javascript
function example() {
    return true;
}
```
````

### Edge Case: Too Many Summary Points

```markdown
<!-- ❌ Wrong: 8 points (too many) -->
## Resumo rápido (em 1 minuto) ✨
- Ponto 1
- Ponto 2
- Ponto 3
- Ponto 4
- Ponto 5
- Ponto 6
- Ponto 7
- Ponto 8

<!-- ✅ Correct: 5 points (ideal) -->
## Resumo rápido (em 1 minuto) ✨
- Ponto 1
- Ponto 2
- Ponto 3
- Ponto 4
- Ponto 5
```

### Edge Case: Link with Poor Description

```markdown
<!-- ❌ Wrong: Generic link text -->
Para mais informações, [clique aqui](https://docs.example.com).

<!-- ✅ Correct: Descriptive link text -->
Consulte a [documentação oficial do TypeScript](https://docs.example.com) para mais detalhes.
```

## 10. Validation Criteria

### Visual Hierarchy Validation

**Automated Checks:**
```bash
# Check heading order (no skipped levels)
grep -E "^#{1,6} " content/posts/*/index.md | awk '{print length($1), $0}'

# Verify Lead shortcode present
grep "{{< lead >}}" content/posts/*/index.md

# Verify Summary section exists
grep "## Resumo rápido" content/posts/*/index.md

# Verify Links section exists
grep "## Links úteis" content/posts/*/index.md
```

**Manual Review:**
- [ ] Lead section appears first and is visually distinct
- [ ] Content flows logically from introduction to resources
- [ ] Headings create clear visual hierarchy
- [ ] No orphaned or confusing heading structure

### Emoji Usage Validation

**Automated Checks:**
```python
import re

def validate_emoji_usage(content):
    # Check H2 headers have emoji
    h2_pattern = r'^## [^\n]+$'
    h2_headers = re.findall(h2_pattern, content, re.MULTILINE)
    
    for header in h2_headers:
        if not contains_emoji(header):
            print(f"Warning: H2 without emoji: {header}")
    
    # Check H3 headers don't have emoji
    h3_pattern = r'^### [^\n]+$'
    h3_headers = re.findall(h3_pattern, content, re.MULTILINE)
    
    for header in h3_headers:
        if contains_emoji(header):
            print(f"Error: H3 with emoji: {header}")
    
    # Check body paragraphs (excluding shortcodes and headers)
    # Implementation details...
```

**Manual Review:**
- [ ] All H2 sections have relevant emoji at end
- [ ] No H3 subsections have emojis
- [ ] No emojis in body paragraphs
- [ ] Emoji selection is semantically appropriate
- [ ] Standard sections use standard emojis (✨, 🧭, 🧩, 🔗)

### Code Block Validation

**Automated Checks:**
```bash
# Find code blocks without language specifier
grep -Pzo '```\n[^`]' content/posts/*/index.md

# Count code blocks per file (should have explanatory text between)
grep -c '```' content/posts/*/index.md
```

**Manual Review:**
- [ ] All code blocks specify language
- [ ] Code includes explanatory comments in Portuguese
- [ ] Code is properly formatted and indented
- [ ] Long examples are broken up with explanatory text
- [ ] Code examples are practical and runnable

### Typography Validation

**Automated Checks:**
```python
def validate_typography(frontmatter, content):
    # Check title case
    title = frontmatter['title']
    if not is_title_case(title):
        print(f"Warning: Title not in title case: {title}")
    
    # Check list consistency
    list_markers = re.findall(r'^[\*\-] ', content, re.MULTILINE)
    if '-' in list_markers and '*' in list_markers:
        print("Error: Mixed list markers found")
    
    # Check inline code usage
    # Implementation details...
```

**Manual Review:**
- [ ] Title uses title case
- [ ] Lists use consistent markers
- [ ] Inline code uses backticks
- [ ] Emphasis (bold/italic) is used appropriately
- [ ] No excessive formatting that hurts readability

## 11. Related Specifications / Further Reading

### Internal References

- `/specs/spec-process-blog-post-creation.md` - Process and workflow for creating posts
- `/.github/copilot/copilot-instructions.md` - Complete Copilot instructions
- `/archetypes/posts/index.md` - Template with pre-formatted structure

### External Documentation

- [Markdown Guide: Basic Syntax](https://www.markdownguide.org/basic-syntax/)
- [Blowfish Shortcodes](https://blowfish.page/docs/shortcodes/)
- [Unicode Emoji List](https://unicode.org/emoji/charts/full-emoji-list.html)
- [WCAG 2.1: Heading Hierarchy](https://www.w3.org/WAI/WCAG21/Understanding/headings-and-labels)
- [Typography Best Practices for the Web](https://www.smashingmagazine.com/typography-guidelines-and-references/)

### Design Resources

- [Butterick's Practical Typography](https://practicaltypography.com/)
- [Material Design: Typography](https://material.io/design/typography)
- [Web Content Accessibility Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)

---

**Version History**

- v1.0 (2025-10-30): Initial design specification based on existing content patterns
