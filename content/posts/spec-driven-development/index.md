---
title: "Spec Driven Development: IA como aliada do desenvolvedor"
description: "Aprenda a criar especificações que humanos e IA entendem. Melhore a consistência, qualidade e colaboração no seu código."
categories: ["tech"]
tags: ["specifications", "ai", "documentation", "best-practices"]
date: 2025-10-30
publishDate: 2025-10-30
draft: false
---

{{< lead >}}
Neste post eu vou tentar te mostrar o que é o spec-driven development da maneira mais clara e acessível possível e meu intuito é que você possa aplicar alguns conceitos aí no seu código tornando seu agente de IA o seu melhor amigo 🤝🤖
{{< /lead >}}

--- 
## 🧩 A importância da especificação

Tudo começa com um bom **README** — ele pode (e deve) ser usado não só pela IA, mas também por seres humanos que passarem pelo seu código.  
Um bom README geralmente contém:

- **Overview**
- **Tech Stack**
- **Prerequisites**
- **Getting Started**
- **Project Structure**
- **Deployment**
- **Resources**
---
Aqui vamos nos abster de citar ferramentas específicas, já que o **Copilot** chama suas instruções de *instructions*, enquanto o **Cursor** de *rules* — e provavelmente este artigo se tornaria obsoleto em questão de segundos se tentássemos acompanhar a terminologia de cada editor.

**O que realmente importa é o conceito:**
a **especificação** define como o seu código deve se comportar e, mais importante ainda, ela é a **fonte da verdade** para todos os seus agentes de IA e desenvolvedores que irão trabalhar naquele projeto.

Imagina que você é um **chef de cozinha** e suas especificações são o **livro de receitas** — aquele que você escreveu com todos os detalhes, inclusive a quantidade exata de gramas de sal que cada cozinheiro deve usar.  
Pronto: esse é o **desenvolvimento guiado por especificação**.

Seu time de cozinha, nesse caso, são os **agentes de IA** — e eles irão performar exatamente de acordo com o que você especificar.

---

## ✍️ Um exemplo prático

Vamos supor que o desenvolvedor **Mike** está trabalhando em um novo post para este blog.

Ao mesmo tempo, a desenvolvedora **Clara** também está escrevendo um artigo sobre síndrome do impostor e quer publicá-lo aqui.

Foi definido que os posts do blog devem seguir uma estrutura específica:  
devem conter **título**, **descrição**, **categoria**, **tags**, **data** e **data de publicação**.  
Além disso, o texto deve seguir um estilo de escrita consistente:

- O idioma principal é **português**;  
- **Termos técnicos** devem permanecer em **inglês**;  
- **Códigos** devem ter comentários em português;  
- O **título** deve respeitar um limite de caracteres;  
- Cada post pode ter **no máximo 5 tags**;  
- Existem diferentes **tipos de posts** — *news*, *tutorial* e *explicações gerais* (como este) — cada um com suas próprias regras;  
- E o mais importante: **nenhum conteúdo do post deve ser gerado por IA**.

Tudo isso é documentado em um arquivo Markdown de especificação, como por exemplo:

```markdown
### File Structure Requirements

- **REQ-001**: Every blog post MUST be created as a Page Bundle in `/content/posts/[post-slug]/`
- **REQ-002**: The main content file MUST be named `index.md`
- **REQ-003**: Each post MUST include a featured image named `featured.jpg` or `featured.png`
- **REQ-004**: All post assets (images, diagrams) MUST be stored in the same folder as `index.md`
- **REQ-005**: Post slug (folder name) MUST use lowercase letters, numbers, and hyphens only

### Front Matter Requirements

- **REQ-006**: Every post MUST include the following front matter fields:
  - `title`: String (40–60 characters, title case)
  - `description`: String (120–160 characters)
  - `categories`: Array (typically `["tech"]`)
  - `tags`: Array (3–5 tags, lowercase, hyphen-separated)
  - `date`: Date (YYYY-MM-DD format)
  - `publishDate`: Date (YYYY-MM-DD format)

### Content Structure Requirements

- **REQ-010**: Every post MUST start with a Lead section using `{{</* lead */>}}` shortcode
- **REQ-011**: Posts with disclaimers or context notes MUST use `{{</* alert */>}}` shortcode
- **REQ-012**: Every post MUST include a "Resumo rápido (em 1 minuto) ✨" section with 4–6 bullet points
- **REQ-013**: Every post MUST include an "O que isso significa para você 🧭" section
- **REQ-014**: Every post MUST conclude with a "Links úteis 🔗" section with at least 3 relevant links
- **REQ-015**: Main content sections MUST use `##` (H2) headers with relevant emoji
- **REQ-016**: Subsections MUST use `###` (H3) headers

### Scope
This specification applies to:
- All blog posts published under `/content/posts/`
- Technical articles, tutorials, and opinion pieces
- Content written in Portuguese (pt-BR) for the Brazilian developer audience
- Posts using Hugo Page Bundle architecture with Blowfish theme v2.91.0
- **Structure generation only** — content creation is out of scope for AI assistance
```
---

## 🤖 IA + especificação = harmonia

Mike pede ao seu agente de IA para criar um novo post.
Paralelamente, Clara faz o mesmo com sua LLM preferida.

Se a especificação estiver bem documentada, cada agente saberá exatamente como e quais regras seguir, resultando em dois posts estruturados de forma idêntica — mesmo sendo criados por modelos diferentes.

Com as especificações do projeto em arquivos Markdown, Clara e Mike podem usar um prompt como este:

> “Usando os arquivos contidos na pasta specs, crie um novo post com o título Spec Driven Development.
> Este post será do tipo explicações gerais, com a categoria tech e as tags AI e programming.
> O conteúdo será escrito por mim, portanto não escreva nenhum conteúdo, apenas configure a estrutura conforme a especificação.”

---

## 🚀 Escalando o conceito

Esse é um exemplo simples, mas o mesmo raciocínio pode ser aplicado a contextos muito mais complexos — definindo regras de negócio, estruturas de dados, validações, ou até pipelines de CI/CD que evoluem primeiro na especificação e só depois no código.

---

## ⚠️ Observaçoes importantes

Sua especificação não deve se preocupar com linguagem, framework ou ferramenta — ela apenas descreve o comportamento esperado.

No fim, Spec Driven Development é sobre escrever a documentação primeiro e codificar depois.
É sobre transformar a especificação na ponte entre humanos e IAs, garantindo clareza, consistência e previsibilidade no desenvolvimento.

E é assim que a IA deixa de ser apenas um assistente — e se torna a melhor amiga do dev. 💜

---

## 🐈 Dica extra pra quem utiliza github-copilot:

O projeto desse blog no git está especificado utilizando os arquivos de referencia que o github-copilot utiliza. Com convenções de nomeação de pastas e arquivos de acordo com a documentação oficial até a data deste post. 

Caso queira pegar de exemplo, pode ficar a vontade 😉


## 🔗 Links úteis para se aprofundar 
- [Este blog no github](https://github.com/alineavila/alineavila.dev)
- [Toolkit de specificações oficiais do github copilot](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/)
- [Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)