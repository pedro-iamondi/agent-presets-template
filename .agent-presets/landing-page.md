# Preset: Landing Page Next.js

Leia também: `.agent-presets/base.md`.

Todos os caminhos citados neste preset são relativos à raiz do projeto.

## Objetivo

Criar e manter landing pages em Next.js com foco em SEO, Core Web Vitals, conversão, acessibilidade e manutenção simples.

## Quando usar

- Nova landing page.
- Página pública de produto, serviço, campanha ou captação.
- Otimização de SEO/performance/conversão de página pública.

## Quando não usar SDD completo

Não usar SDD completo para:

- Troca de copy.
- Ajuste de espaçamento, cor ou responsividade local.
- Correção de link.
- Ajuste pequeno em metadata.
- Fix de build/lint/tipo.

Use modo `quick` nesses casos.

## Quando usar full-sdd

Usar SDD quando:

- A landing representa produto novo.
- Há nova proposta de valor ou nova persona.
- A página exige nova arquitetura de componentes.
- Há formulários, tracking, CRM, checkout ou integrações.
- Há mudança relevante de SEO, conteúdo ou funil.

## Skills principais

- [tlc-spec-driven](.agent-skills/tlc-spec-driven/SKILL.md) ([web](https://agent-skills.techleads.club/skills/tlc-spec-driven/))
- [frontend-design](.agent-skills/frontend-design/SKILL.md) ([web](https://agent-skills.techleads.club/skills/frontend-design/))
- [seo](.agent-skills/seo/SKILL.md) ([web](https://agent-skills.techleads.club/skills/seo/))
- [core-web-vitals](.agent-skills/core-web-vitals/SKILL.md) ([web](https://agent-skills.techleads.club/skills/core-web-vitals/))
- [best-practices](.agent-skills/best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/best-practices/))
- [accessibility](.agent-skills/accessibility/SKILL.md) ([web](https://agent-skills.techleads.club/skills/accessibility/))
- [security-best-practices](.agent-skills/security-best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/security-best-practices/))
- [perf-lighthouse](.agent-skills/perf-lighthouse/SKILL.md) ([web](https://agent-skills.techleads.club/skills/perf-lighthouse/))
- [playwright-skill](.agent-skills/playwright-skill/SKILL.md) ([web](https://agent-skills.techleads.club/skills/playwright-skill/))

## Fluxo recomendado

### Para landing nova

1. Especificar objetivo, público, oferta e CTA.
2. Definir estrutura da página.
3. Criar design visual consistente.
4. Implementar em Next.js.
5. Adicionar metadata, Open Graph, canonical e schema quando aplicável.
6. Otimizar imagens, fontes, carregamento e componentes client-side.
7. Validar acessibilidade básica.
8. Validar build e performance.

### Para correções pequenas

1. Localizar o componente ou seção.
2. Aplicar menor mudança possível.
3. Validar visualmente e via build/lint se aplicável.
4. Não criar specs ou docs extensos.

## Regras Next.js

- Preferir Server Components por padrão.
- Usar Client Components apenas quando houver interatividade real.
- Usar `next/image` para imagens relevantes.
- Evitar bibliotecas pesadas para animações simples.
- Definir metadata de forma consistente com o padrão do projeto.
- Não duplicar metadata entre `layout.tsx` e `page.tsx` sem necessidade.
- Garantir heading structure coerente.
- Garantir CTA claro acima da dobra.

## Checklist de aceite

- Página responsiva.
- Title e description definidos.
- Open Graph quando aplicável.
- Imagens com alt adequado.
- Sem dependência desnecessária.
- Sem layout shift evidente.
- Build sem erro.
- Links e CTAs testados.
