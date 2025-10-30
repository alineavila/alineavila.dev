---
title: Blog Post Creation Process Specification
version: 1.0
date_created: 2025-10-30
last_updated: 2025-10-30
owner: Aline Ávila
tags: [process, content, blog, hugo, workflow]
---

# Introduction

This specification defines the complete process for creating, structuring, and publishing blog posts on alineavila.dev. It establishes standards for content organization, front matter structure, visual hierarchy, and quality assurance to ensure consistency and maintainability across all blog content.

## 1. Purpose & Scope

### Purpose
Define a standardized, repeatable process for creating blog posts that:
- Ensures consistent structure and quality across all posts
- Optimizes content for both human readers and search engines
- Maintains compatibility with Hugo static site generator and Blowfish theme
- Enables efficient content creation workflow
- Facilitates AI-assisted **structure generation** (not content writing) through clear specifications

**CRITICAL: GitHub Copilot's Role**
- Copilot should **ONLY create the post structure** (directories, files, front matter, section headers, placeholders)
- Copilot should **NEVER write the actual content** (paragraphs, code examples, explanations)
- All substantive content must be written exclusively by the human author
- This ensures 100% human-generated content and authentic voice

### Scope
This specification applies to:
- All blog posts published under `/content/posts/`
- Technical articles, tutorials, and opinion pieces
- Content written in Portuguese (pt-BR) for Brazilian developer audience
- Posts using Hugo Page Bundle architecture with Blowfish theme v2.91.0
- **Structure generation only** - content creation is out of scope for AI assistance

### Audience
- Content creators and authors (primary content writers)
- GitHub Copilot and AI-assisted tools (structure scaffolding only)
- Future contributors to the blog
- Maintainers of the alineavila.dev site

### Assumptions
- Hugo Extended v0.152.1+ is installed and available
- Blowfish theme v2.91.0 is installed as git submodule
- Git is configured for version control
- Content is written in Markdown with YAML front matter
- **Human author will write all content after structure is created**

## 2. Definitions

| Term | Definition |
|------|------------|
| **Page Bundle** | Hugo's content organization pattern where a post folder contains `index.md` plus all related assets |
| **Front Matter** | YAML metadata block at the top of Markdown files containing post configuration |
| **Archetype** | Hugo template used to scaffold new content with pre-defined structure |
| **Shortcode** | Hugo's reusable content snippet (e.g., `{{< lead >}}`, `{{< alert >}}`) |
| **Slug** | URL-friendly post identifier (e.g., `java-25-novidades`) |
| **Featured Image** | Primary image displayed in post previews and social media shares |
| **Goldmark** | Hugo's default Markdown renderer |
| **Taxonomy** | Hugo's classification system (tags, categories, series, authors) |
| **Draft** | Unpublished post with `draft: true` in front matter |
| **SEO** | Search Engine Optimization |
| **OG** | Open Graph (social media sharing protocol) |

## 3. Requirements, Constraints & Guidelines

### File Structure Requirements

- **REQ-001**: Every blog post MUST be created as a Page Bundle in `/content/posts/[post-slug]/`
- **REQ-002**: The main content file MUST be named `index.md`
- **REQ-003**: Each post MUST include a featured image named `featured.jpg` or `featured.png`
- **REQ-004**: All post assets (images, diagrams) MUST be stored in the same folder as `index.md`
- **REQ-005**: Post slug (folder name) MUST use lowercase letters, numbers, and hyphens only

### Front Matter Requirements

- **REQ-006**: Every post MUST include the following front matter fields:
  - `title`: String (40-60 characters, title case)
  - `description`: String (120-160 characters)
  - `categories`: Array (typically `["tech"]`)
  - `tags`: Array (3-5 tags, lowercase, hyphen-separated)
  - `date`: Date (YYYY-MM-DD format)
  - `publishDate`: Date (YYYY-MM-DD format)

- **REQ-007**: Front matter MUST use YAML format (not TOML or JSON)
- **REQ-008**: Posts in draft state MUST include `draft: true`, published posts MUST omit this field
- **REQ-009**: Author field MUST NOT be included in front matter (defined globally in config)

### Content Structure Requirements

- **REQ-010**: Every post MUST start with a Lead section using `{{< lead >}}` shortcode
- **REQ-011**: Posts with disclaimers or context notes MUST use `{{< alert >}}` shortcode
- **REQ-012**: Every post MUST include a "Resumo rápido (em 1 minuto) ✨" section with 4-6 bullet points
- **REQ-013**: Every post MUST include an "O que isso significa para você 🧭" section
- **REQ-014**: Every post MUST conclude with a "Links úteis 🔗" section with minimum 3 relevant links
- **REQ-015**: Main content sections MUST use `##` (H2) headers with relevant emoji
- **REQ-016**: Subsections MUST use `###` (H3) headers

### Code Example Requirements

- **REQ-017**: All code blocks MUST specify the programming language for syntax highlighting
- **REQ-018**: Code examples MUST be runnable or clearly marked as pseudocode
- **REQ-019**: Code MUST include brief explanatory comments in Portuguese
- **REQ-020**: Nested code examples (meta-examples) MUST use 4 backticks for outer block

### Image Requirements

- **REQ-021**: Featured images MUST be 1200x630px (Open Graph standard)
- **REQ-022**: Featured images MUST be optimized for web (< 200KB)
- **REQ-023**: All images MUST include meaningful alt text
- **REQ-024**: Inline images MUST use descriptive filenames (e.g., `architecture-diagram.png`)
- **REQ-025**: Image filenames MUST use lowercase with hyphens (no spaces or underscores)

### SEO Requirements

- **REQ-026**: Title MUST be 40-60 characters and include primary keyword
- **REQ-027**: Description MUST be 120-160 characters and include primary keyword
- **REQ-028**: Posts MUST include 3-5 relevant tags
- **REQ-029**: Tags MUST be lowercase and hyphen-separated for multi-word tags

### Content Quality Requirements

- **REQ-030**: Content MUST be written in Portuguese (pt-BR)
- **REQ-031**: Content MUST be 100% human-generated (no undisclosed AI content)
- **REQ-032**: Posts MUST include "🚫🤖 Conteúdo 100% humano" principle adherence
- **REQ-033**: Technical terms MAY remain in English when commonly used
- **REQ-034**: All external links MUST be verified as working before publication
- **REQ-035**: GitHub Copilot MUST generate structure only (folders, files, headers, placeholders)
- **REQ-036**: GitHub Copilot MUST NOT write substantive content (paragraphs, code, explanations)

### Constraints

- **CON-001**: Maximum post slug length: 50 characters
- **CON-002**: Minimum post word count: 500 words
- **CON-003**: Maximum featured image file size: 200KB
- **CON-004**: Maximum inline image file size: 100KB each
- **CON-005**: Hugo Extended is required (not standard Hugo)
- **CON-006**: Theme compatibility: Blowfish v2.91.0+

### Guidelines

- **GUD-001**: Prefer practical code examples over theoretical explanations
- **GUD-002**: Target beginner to intermediate developer audience
- **GUD-003**: Use friendly, educational tone without condescension
- **GUD-004**: Include personal perspective and "learning in public" approach
- **GUD-005**: Use emojis sparingly for visual hierarchy, not in body text
- **GUD-006**: Explain acronyms on first use
- **GUD-007**: Provide context for examples (OS, environment dependencies)
- **GUD-008**: Keep sentences clear and concise for better comprehension
- **GUD-009**: AI tools should generate scaffolding with clear `[TODO: ...]` placeholders for human content
- **GUD-010**: Placeholders should be specific (e.g., `[TODO: Explain why this matters to beginners]`)

### Patterns to Follow

- **PAT-001**: Follow existing post structure from `/content/posts/first/index.md` as exemplar
- **PAT-002**: Use consistent emoji placement: section titles only
- **PAT-003**: Structure tutorials as: Problem → Solution → Code → Explanation → Resources
- **PAT-004**: Structure news/updates as: What Changed → Why It Matters → Examples → Migration Guide → Resources

## 4. Interfaces & Data Contracts

### Front Matter Schema

```yaml
---
title: string                    # Required: 40-60 chars, title case
description: string              # Required: 120-160 chars
categories: string[]             # Required: typically ["tech"]
tags: string[]                   # Required: 3-5 tags, lowercase
date: date                       # Required: YYYY-MM-DD
publishDate: date                # Required: YYYY-MM-DD
draft: boolean                   # Optional: omit for published posts
---
```

### Post Structure Template

**For GitHub Copilot: Create this structure with placeholders, DO NOT write content**

```markdown
---
title: "[TODO: Title here - 40-60 chars]"
description: "[TODO: Description here - 120-160 chars]"
categories: ["tech"]
tags: ["[TODO]", "[TODO]", "[TODO]"]
date: YYYY-MM-DD
publishDate: YYYY-MM-DD
---

{{< lead >}}
[TODO: Write engaging 1-2 sentence introduction with emoji at end] 🚀
{{< /lead >}}

{{< alert >}}
[TODO: Optional - Add disclaimer, transparency note, or important context if needed]
{{< /alert >}}

## Resumo rápido (em 1 minuto) ✨
- [TODO: Key point 1]
- [TODO: Key point 2]
- [TODO: Key point 3]
- [TODO: Key point 4]
- [TODO: Optional - Key point 5-6]

## O que isso significa para você 🧭
[TODO: Write 1-2 paragraphs explaining practical relevance and implications for the reader]

## [TODO: Main Topic] na prática 🧩

### [TODO: Subtopic 1]
[TODO: Write content with code examples]

```[TODO: language]
// TODO: Add brief explanation
[TODO: Code example]
```

[TODO: Explain the code above]

### [TODO: Subtopic 2]
[TODO: Write additional content]

## Links úteis 🔗
- [TODO: Resource 1 Title](https://[TODO].com)
- [TODO: Resource 2 Title](https://[TODO].com)
- [TODO: Resource 3 Title](https://[TODO].com)
```

**Important Notes:**
- All `[TODO: ...]` markers must be replaced by the human author
- Copilot should create folder structure: `/content/posts/[slug]/index.md`
- Copilot should create placeholder `featured.jpg` or remind author to add it
- All substantive content (paragraphs, code, links) must be written by human

### File System Contract

```
content/posts/[post-slug]/
├── index.md              # Main content (required)
├── featured.jpg          # Featured image (required)
├── diagram.png           # Additional assets (optional)
└── screenshot.png        # Additional assets (optional)
```

## 5. Acceptance Criteria

### Post Creation

- **AC-001**: Given a new post topic, When using `hugo new posts/[slug]/index.md` or requesting Copilot assistance, Then a properly structured Page Bundle is created with archetype template
- **AC-002**: Given a post slug, When it contains uppercase letters or spaces, Then the system should reject it or convert to lowercase with hyphens
- **AC-003**: Given a new post, When front matter is missing required fields, Then the post should not pass validation
- **AC-016**: Given a Copilot-generated post structure, When reviewing the output, Then all content sections must contain `[TODO: ...]` placeholders and no substantive content
- **AC-017**: Given a completed post, When checking for AI content, Then all `[TODO: ...]` markers must be replaced with human-written content

### Content Structure

- **AC-004**: Given a published post, When viewing the content, Then it must include all required sections (Lead, Summary, Main Content, Links)
- **AC-005**: Given a post with code examples, When viewing the rendered page, Then all code blocks must have proper syntax highlighting
- **AC-006**: Given a post with images, When checking accessibility, Then all images must have descriptive alt text

### SEO & Metadata

- **AC-007**: Given a post title, When it exceeds 60 characters, Then a warning should be issued
- **AC-008**: Given a post description, When it is less than 120 or more than 160 characters, Then a warning should be issued
- **AC-009**: Given a post with tags, When fewer than 3 or more than 5 tags are present, Then a recommendation should be provided

### Image Optimization

- **AC-010**: Given a featured image, When file size exceeds 200KB, Then it must be optimized before publication
- **AC-011**: Given a featured image, When dimensions are not 1200x630px, Then it should be resized or a warning issued
- **AC-012**: Given inline images, When any file exceeds 100KB, Then they must be optimized

### Publication Readiness

- **AC-013**: Given a post ready for publication, When `draft: true` is present in front matter, Then it must be removed
- **AC-014**: Given a published post, When running `hugo server`, Then the post must appear in the post list and be accessible
- **AC-015**: Given a published post, When checking all external links, Then all links must return 200 OK status

## 6. Test Automation Strategy

### Test Levels

**Unit Testing**
- Front matter validation (YAML parsing, required fields)
- Slug format validation (lowercase, hyphens, length)
- Image file size checks
- Title and description length validation

**Integration Testing**
- Hugo build process with post content
- Theme rendering with all shortcodes
- Image loading and optimization
- Internal link resolution

**End-to-End Testing**
- Complete post creation workflow
- Preview in development server
- Build for production
- Accessibility checks (alt text, keyboard navigation)

### Frameworks & Tools

- **Markdown Linting**: `markdownlint-cli` for Markdown syntax validation
- **Link Checking**: `markdown-link-check` for broken link detection
- **Image Optimization**: `imagemin` or manual optimization tools
- **Hugo Validation**: Built-in Hugo validation during `hugo` command
- **Accessibility**: `pa11y` or manual WCAG checks

### Test Data Management

- Use example posts in `/content/posts/examples/` for testing
- Maintain test fixtures with various edge cases (long titles, many tags, etc.)
- Keep sample images in test fixtures with known sizes and dimensions

### CI/CD Integration

- **Pre-commit Hooks**: Validate front matter and file structure before commit
- **GitHub Actions**: Run Hugo build, link checking, and accessibility tests on PR
- **Deployment Checks**: Verify all images load correctly in production build

### Coverage Requirements

- 100% of posts must pass front matter validation
- 100% of external links must be checked before publication
- 100% of images must have alt text
- All code blocks must specify language (no empty language specifiers)

### Performance Testing

- Measure Hugo build time with increasing number of posts
- Monitor page load time with different image sizes
- Test responsive rendering on mobile devices

## 7. Rationale & Context

### Why Page Bundles?
Page Bundles provide a self-contained content structure where all assets (images, data files) are co-located with the content. This improves:
- Portability (easy to move or reorganize posts)
- Maintainability (all related files in one place)
- Asset management (relative URLs always work)
- Git workflow (all changes in one directory)

### Why Strict Front Matter Requirements?
Consistent front matter ensures:
- Reliable SEO optimization across all posts
- Proper rendering in theme layouts
- Accurate post metadata for feeds and lists
- Better search functionality
- Consistent social media sharing previews

### Why Specific Content Structure?
The defined structure (Lead → Alert → Summary → Content → Links) provides:
- Predictable reading experience for visitors
- Quick scanability for time-constrained readers
- SEO-friendly content organization
- Clear hierarchy for search engines
- Consistent voice and tone across posts

### Why Image Optimization Requirements?
Optimized images ensure:
- Fast page load times (critical for SEO and UX)
- Better mobile experience (reduced data usage)
- Lower hosting costs (reduced bandwidth)
- Improved Core Web Vitals scores
- Better accessibility (properly sized images)

### Why Portuguese Content?
Target audience is Brazilian developers, making Portuguese:
- More accessible and inclusive for primary audience
- Better for explaining complex concepts in native language
- More authentic and relatable (learning in public approach)
- Fills content gap (less Portuguese technical content available)

### Why 100% Human Content Principle?
This ensures:
- Authentic voice and personal perspective
- Original insights from real experience
- Trust and credibility with readers
- Compliance with search engine content policies
- Alignment with "learning in public" philosophy

### Why Copilot Creates Structure Only?
Separating structure generation from content creation ensures:
- **Authentic Voice**: Author's unique perspective and tone are preserved
- **Original Insights**: Content reflects real experience, not AI-generated text
- **Efficiency**: Copilot handles repetitive scaffolding, author focuses on valuable content
- **Consistency**: All posts follow the same structural pattern
- **Compliance**: No undisclosed AI-generated content in final publication
- **Learning in Public**: Author's genuine learning journey is documented
- **Quality Control**: Human judgment for accuracy, relevance, and appropriateness

## 8. Dependencies & External Integrations

### External Systems

- **EXT-001**: Hugo Static Site Generator - Required for content compilation and site generation
- **EXT-002**: Git Version Control - Required for content versioning and deployment workflow

### Third-Party Services

- **SVC-001**: Hosting Platform (Netlify/Vercel/GitHub Pages) - Required for site deployment with automatic builds
- **SVC-002**: CDN Service - Required for fast global content delivery
- **SVC-003**: Image Optimization Service (Optional) - For automated image optimization pipeline

### Infrastructure Dependencies

- **INF-001**: Homebrew Package Manager - Required for Hugo Extended installation on macOS
- **INF-002**: Git Submodule System - Required for Blowfish theme management
- **INF-003**: Markdown Processor (Goldmark) - Built into Hugo for content rendering

### Data Dependencies

- **DAT-001**: Blowfish Theme v2.91.0+ - Required for layout, styling, and shortcodes
- **DAT-002**: Git Repository History - Required for automatic lastmod dates via `enableGitInfo`

### Technology Platform Dependencies

- **PLT-001**: Hugo Extended v0.152.1+ - Required for SCSS/SASS processing and theme compatibility
- **PLT-002**: Go 1.16+ - Required by Blowfish theme module system
- **PLT-003**: Goldmark Markdown Renderer - Required for Markdown processing with extensions

### Compliance Dependencies

- **COM-001**: WCAG 2.1 Level AA - Required for accessibility compliance (alt text, keyboard navigation)
- **COM-002**: Open Graph Protocol - Required for social media sharing compatibility
- **COM-003**: Schema.org Structured Data - Recommended for enhanced search results

## 9. Examples & Edge Cases

### Example: Standard Tutorial Post

```markdown
---
title: "Python Decorators: Guia Prático para Iniciantes"
description: "Aprenda a usar decorators em Python com exemplos práticos e casos de uso reais para melhorar seu código."
categories: ["tech"]
tags: ["python", "decorators", "tutorial", "iniciantes"]
date: 2025-10-30
publishDate: 2025-10-30
---

{{< lead >}}
Decorators em Python parecem mágica, mas são simples de entender e usar! 🎯
{{< /lead >}}

{{< alert >}}
Este tutorial assume conhecimento básico de Python (funções e closures).
{{< /alert >}}

## Resumo rápido (em 1 minuto) ✨
- Decorators são funções que modificam outras funções
- Sintaxe: `@decorator` antes da definição da função
- Úteis para logging, validação, cache e controle de acesso
- Podem aceitar argumentos e serem empilhados
- Python tem decorators built-in como `@property` e `@staticmethod`

## O que isso significa para você 🧭
Se você já copiou e colou código repetitivo em várias funções (logging, validação, etc.), decorators são a solução. Eles permitem reutilizar comportamentos sem poluir o código principal.

## Decorators básicos na prática 🧩

### Seu primeiro decorator

```python
def meu_decorator(funcao):
    def wrapper():
        print("Antes da função")
        funcao()
        print("Depois da função")
    return wrapper

@meu_decorator
def dizer_ola():
    print("Olá!")

dizer_ola()
# Output:
# Antes da função
# Olá!
# Depois da função
```

### Decorator com argumentos

```python
def repetir(vezes):
    def decorator(funcao):
        def wrapper(*args, **kwargs):
            for _ in range(vezes):
                resultado = funcao(*args, **kwargs)
            return resultado
        return wrapper
    return decorator

@repetir(vezes=3)
def cumprimentar(nome):
    print(f"Olá, {nome}!")

cumprimentar("Maria")
# Output:
# Olá, Maria!
# Olá, Maria!
# Olá, Maria!
```

## Links úteis 🔗
- [Python Decorators PEP 318](https://peps.python.org/pep-0318/)
- [Real Python: Primer on Python Decorators](https://realpython.com/primer-on-python-decorators/)
- [Python Documentation: Decorators](https://docs.python.org/3/glossary.html#term-decorator)
```

### Edge Case: Post with Multiple Code Languages

```markdown
---
title: "Fullstack: Conectando React com Node.js API"
description: "Tutorial completo de integração frontend/backend com React e Express, incluindo autenticação e deploy."
categories: ["tech"]
tags: ["react", "nodejs", "express", "fullstack", "api"]
date: 2025-10-30
publishDate: 2025-10-30
---

{{< lead >}}
Construa uma aplicação fullstack completa do zero! 🚀
{{< /lead >}}

## Resumo rápido (em 1 minuto) ✨
- Backend com Express.js e autenticação JWT
- Frontend com React e hooks modernos
- Comunicação via REST API
- Deploy na Vercel (frontend) e Render (backend)

## O que isso significa para você 🧭
Este tutorial mostra a arquitetura completa de uma aplicação moderna, desde o banco de dados até a interface do usuário.

## Backend: Node.js + Express 🧩

### Configurando o servidor

```javascript
// server.js
const express = require('express');
const cors = require('cors');

const app = express();

// Middlewares
app.use(cors());
app.use(express.json());

// Rota de teste
app.get('/api/health', (req, res) => {
    res.json({ status: 'ok', timestamp: Date.now() });
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
    console.log(`Servidor rodando na porta ${PORT}`);
});
```

## Frontend: React 🎨

### Hook customizado para API

```jsx
// hooks/useApi.js
import { useState, useEffect } from 'react';

export function useApi(endpoint) {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);

    useEffect(() => {
        fetch(`http://localhost:3000/api/${endpoint}`)
            .then(res => res.json())
            .then(setData)
            .catch(setError)
            .finally(() => setLoading(false));
    }, [endpoint]);

    return { data, loading, error };
}
```

### Usando o hook

```jsx
// App.jsx
import { useApi } from './hooks/useApi';

function App() {
    const { data, loading, error } = useApi('health');

    if (loading) return <p>Carregando...</p>;
    if (error) return <p>Erro: {error.message}</p>;

    return (
        <div>
            <h1>Status: {data.status}</h1>
            <p>Timestamp: {data.timestamp}</p>
        </div>
    );
}

export default App;
```

## Deploy 🚀

### Backend (Render)

```bash
# Adicionar ao package.json
{
    "scripts": {
        "start": "node server.js"
    }
}
```

### Frontend (Vercel)

```bash
# Instalar Vercel CLI
npm i -g vercel

# Deploy
vercel --prod
```

## Links úteis 🔗
- [Express.js Documentation](https://expressjs.com/)
- [React Hooks Documentation](https://react.dev/reference/react)
- [Vercel Deployment Guide](https://vercel.com/docs)
- [Render Deployment Guide](https://render.com/docs)
```

### Edge Case: Post with Math Formulas

```markdown
---
title: "Big O Notation: Entendendo Complexidade de Algoritmos"
description: "Guia visual e prático sobre notação Big O com exemplos em Python e análise de performance."
categories: ["tech"]
tags: ["algoritmos", "big-o", "performance", "python"]
date: 2025-10-30
publishDate: 2025-10-30
---

{{< lead >}}
Descubra por que seu código está lento e como melhorá-lo! ⚡
{{< /lead >}}

## Resumo rápido (em 1 minuto) ✨
- Big O mede como o tempo de execução cresce com o tamanho da entrada
- O(1) é constante, O(n) é linear, O(n²) é quadrático
- Não se preocupe com constantes, foque no termo dominante
- Loops aninhados geralmente são O(n²) ou pior
- Usar estruturas de dados adequadas pode reduzir complexidade

## O que isso significa para você 🧭
Entender Big O ajuda a escrever código mais eficiente e identificar gargalos antes que se tornem problemas em produção.

## Complexidades comuns na prática 🧩

### O(1) - Tempo Constante

```python
def acessar_primeiro(lista):
    # Sempre leva o mesmo tempo, independente do tamanho
    return lista[0]  # O(1)
```

Complexidade: \(O(1)\)

### O(n) - Tempo Linear

```python
def buscar_elemento(lista, alvo):
    # Precisa verificar cada elemento no pior caso
    for elemento in lista:  # O(n)
        if elemento == alvo:
            return True
    return False
```

Complexidade: \(O(n)\) onde \(n\) é o tamanho da lista

### O(n²) - Tempo Quadrático

```python
def imprimir_pares(lista):
    # Loop dentro de loop: n × n operações
    for i in lista:  # O(n)
        for j in lista:  # O(n)
            print(f"Par: ({i}, {j})")  # O(1)
```

Complexidade: \(O(n^2)\)

### O(log n) - Tempo Logarítmico

```python
def busca_binaria(lista_ordenada, alvo):
    esquerda, direita = 0, len(lista_ordenada) - 1
    
    while esquerda <= direita:  # O(log n)
        meio = (esquerda + direita) // 2
        
        if lista_ordenada[meio] == alvo:
            return meio
        elif lista_ordenada[meio] < alvo:
            esquerda = meio + 1
        else:
            direita = meio - 1
    
    return -1
```

Complexidade: \(O(\log n)\) - divide o problema pela metade a cada iteração

## Comparação visual 📊

Para \(n = 1000\) elementos:

| Complexidade | Operações | Exemplo |
|--------------|-----------|---------|
| \(O(1)\) | 1 | Acessar array[0] |
| \(O(\log n)\) | ~10 | Busca binária |
| \(O(n)\) | 1,000 | Loop simples |
| \(O(n \log n)\) | ~10,000 | Merge sort |
| \(O(n^2)\) | 1,000,000 | Loop duplo |
| \(O(2^n)\) | ~10^301 | Fibonacci recursivo |

## Links úteis 🔗
- [Big O Cheat Sheet](https://www.bigocheatsheet.com/)
- [Python Time Complexity](https://wiki.python.org/moin/TimeComplexity)
- [Algorithm Visualizer](https://algorithm-visualizer.org/)
```

### Edge Case: Very Long Title (Should Trigger Warning)

```yaml
---
title: "Este É Um Título Extremamente Longo Que Ultrapassa os 60 Caracteres Recomendados e Deve Gerar Um Alerta"
# ❌ This title is 110 characters - should trigger warning
description: "Description here"
categories: ["tech"]
tags: ["example"]
date: 2025-10-30
publishDate: 2025-10-30
---
```

### Edge Case: Missing Required Front Matter

```yaml
---
title: "Post Sem Tags ou Categorias"
description: "Este post está incompleto"
date: 2025-10-30
# ❌ Missing: categories, tags, publishDate
---
```

## 10. Validation Criteria

### Pre-Publication Validation Checklist

**File Structure**
- [ ] Post is in `/content/posts/[slug]/` directory
- [ ] Main file is named `index.md`
- [ ] `featured.jpg` or `featured.png` exists
- [ ] Slug uses lowercase and hyphens only
- [ ] Slug is ≤ 50 characters

**Front Matter**
- [ ] YAML format is valid (no syntax errors)
- [ ] `title` is present and 40-60 characters
- [ ] `description` is present and 120-160 characters
- [ ] `categories` array is present
- [ ] `tags` array is present with 3-5 items
- [ ] `date` is present in YYYY-MM-DD format
- [ ] `publishDate` is present in YYYY-MM-DD format
- [ ] `draft: true` is removed (for published posts)
- [ ] No `author` field is present

**Content Structure**
- [ ] Post starts with `{{< lead >}}` shortcode
- [ ] "Resumo rápido (em 1 minuto) ✨" section is present
- [ ] "O que isso significa para você 🧭" section is present
- [ ] "Links úteis 🔗" section is present with ≥3 links
- [ ] Main sections use `##` headers with emoji
- [ ] Subsections use `###` headers

**Code Quality**
- [ ] All code blocks specify language
- [ ] Code examples are runnable or marked as pseudocode
- [ ] Code includes explanatory comments in Portuguese
- [ ] Nested examples use 4 backticks correctly

**Images**
- [ ] Featured image is 1200x630px
- [ ] Featured image is < 200KB
- [ ] All images have descriptive alt text
- [ ] Inline images are < 100KB each
- [ ] Image filenames use lowercase with hyphens

**Links & References**
- [ ] All external links are verified (return 200 OK)
- [ ] Links use descriptive text (not "click here")
- [ ] Links include protocol (https://)
- [ ] Minimum 3 links in "Links úteis" section

**SEO & Accessibility**
- [ ] Title includes primary keyword
- [ ] Description includes primary keyword
- [ ] Tags are relevant and lowercase
- [ ] All images have meaningful alt text
- [ ] Content is written in Portuguese
- [ ] Headings follow logical hierarchy (H2 → H3)

**Build & Preview**
- [ ] Post builds without errors with `hugo`
- [ ] Post previews correctly with `hugo server -D`
- [ ] Images load correctly in preview
- [ ] Code syntax highlighting works
- [ ] Shortcodes render properly
- [ ] Mobile responsive layout works

### Automated Validation

Tools and commands for automated validation:

```bash
# Validate Markdown syntax
markdownlint content/posts/[slug]/index.md

# Check for broken links
markdown-link-check content/posts/[slug]/index.md

# Build site (catches Hugo errors)
hugo --minify

# Preview (visual validation)
hugo server -D

# Check image sizes
find content/posts/[slug]/ -name "*.jpg" -o -name "*.png" | xargs du -h
```

### Manual Validation

Human review checklist:

- [ ] Content is grammatically correct
- [ ] Tone is friendly and educational
- [ ] Examples are clear and relevant
- [ ] Code is properly formatted and indented
- [ ] Explanations are beginner-friendly
- [ ] Personal perspective is included
- [ ] "Learning in public" spirit is present
- [ ] Content adds value to readers

## 11. Related Specifications / Further Reading

### Internal References

- `/specs/spec-design-content-structure.md` - Visual design and typography standards
- `/.github/copilot/copilot-instructions.md` - Complete GitHub Copilot instructions
- `/archetypes/posts/index.md` - Post template for `hugo new` command
- `/config/_default/params.toml` - Theme and site configuration

### External Documentation

- [Hugo Documentation: Content Organization](https://gohugo.io/content-management/organization/)
- [Hugo Documentation: Page Bundles](https://gohugo.io/content-management/page-bundles/)
- [Blowfish Theme Documentation](https://blowfish.page/docs/)
- [Markdown Guide](https://www.markdownguide.org/)
- [Open Graph Protocol](https://ogp.me/)
- [Schema.org for Articles](https://schema.org/Article)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [Google SEO Starter Guide](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)

### Related Tools

- [Hugo Extended](https://gohugo.io/installation/)
- [markdownlint-cli](https://github.com/igorshubovych/markdownlint-cli)
- [markdown-link-check](https://github.com/tcort/markdown-link-check)
- [imagemin](https://github.com/imagemin/imagemin)
- [TinyPNG](https://tinypng.com/) - Image optimization service

---

**Version History**

- v1.0 (2025-10-30): Initial specification created from existing blog patterns and requirements
