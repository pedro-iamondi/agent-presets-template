# Preset: Blog Next.js

Leia também: `.agent-presets/base.md`.

Todos os caminhos citados neste preset são relativos à raiz do projeto.

## Objetivo

Criar e manter blogs em Next.js com foco em SEO, conteúdo indexável, performance, estrutura editorial e manutenção escalável.

## Quando usar

- Blog institucional.
- Área de artigos.
- Páginas de categoria/tag.
- Templates de post.
- SEO programático ou conteúdo evergreen.

## Quando não usar SDD completo

Não usar SDD completo para:

- Publicar artigo simples em estrutura já existente.
- Corrigir typo ou copy.
- Ajustar metadata de um post.
- Corrigir imagem, slug ou link.
- Ajuste visual pequeno no template.

Use modo `quick`.

## Quando usar full-sdd

Usar SDD quando:

- Criar arquitetura do blog do zero.
- Definir CMS ou fonte de conteúdo.
- Criar taxonomia de categorias/tags.
- Implementar busca, filtros ou paginação.
- Criar SEO programático.
- Alterar estrutura de URLs.

## Skills principais

- [tlc-spec-driven](.agent-skills/tlc-spec-driven/SKILL.md) ([web](https://agent-skills.techleads.club/skills/tlc-spec-driven/))
- [technical-design-doc-creator](.agent-skills/technical-design-doc-creator/SKILL.md) ([web](https://agent-skills.techleads.club/skills/technical-design-doc-creator/))
- [seo](.agent-skills/seo/SKILL.md) ([web](https://agent-skills.techleads.club/skills/seo/))
- [core-web-vitals](.agent-skills/core-web-vitals/SKILL.md) ([web](https://agent-skills.techleads.club/skills/core-web-vitals/))
- [frontend-design](.agent-skills/frontend-design/SKILL.md) ([web](https://agent-skills.techleads.club/skills/frontend-design/))
- [accessibility](.agent-skills/accessibility/SKILL.md) ([web](https://agent-skills.techleads.club/skills/accessibility/))
- [perf-lighthouse](.agent-skills/perf-lighthouse/SKILL.md) ([web](https://agent-skills.techleads.club/skills/perf-lighthouse/))

## Fluxo recomendado

### Blog novo

1. Definir objetivos editoriais e público.
2. Definir fonte de conteúdo: MDX, CMS, banco ou API.
3. Definir rotas: índice, post, categoria, tag, autor.
4. Definir metadata, sitemap, RSS e schema.
5. Implementar templates.
6. Validar indexabilidade e performance.

### Post ou ajuste pequeno

1. Verificar padrão atual de posts.
2. Aplicar mudança local.
3. Validar slug, metadata e links.
4. Não criar documentação extensa.

## Regras SEO para blog

- URLs estáveis e legíveis.
- Um H1 por página.
- Title e description únicos.
- Canonical quando aplicável.
- Dados estruturados quando fizer sentido.
- Sitemap atualizado.
- Evitar conteúdo duplicado por tag/categoria.
- Garantir links internos relevantes.

## Regras Next.js

- Preferir geração estática quando possível.
- Evitar carregar conteúdo desnecessário no client.
- Usar `next/image` para imagens de capa e conteúdo quando aplicável.
- Preservar performance do template de post.

## Checklist de aceite

- Post ou página indexável.
- Metadata correta.
- Canonical correto.
- Layout responsivo.
- Imagens otimizadas.
- Links internos funcionando.
- Build sem erro.
