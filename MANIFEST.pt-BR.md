# Agent Presets Template Manifest

## Identidade

- Nome: Agent Presets Template
- Versão: 0.1.0
- Data de referência: 2026-04-28
- Objetivo: padronizar como agentes de IA trabalham em projetos da empresa usando presets, skills locais e carregamento progressivo de contexto.
- Autor: Pedro H. Iamondi
- LinkedIn: https://www.linkedin.com/in/pedro-henrique-iamondi
- Instagram: https://www.instagram.com/peh.iamondi/

## Convenção de caminhos

Todos os caminhos citados neste template são relativos à raiz do projeto onde o template foi instalado.

Exemplos:

- `AGENTS.md`
- `.agent-presets/base.md`
- `.agent-skills/seo/SKILL.md`
- `scratch/`

## Presets instalados

- Base comum: `.agent-presets/base.md`
- Landing page Next.js: `.agent-presets/landing-page.md`
- Blog Next.js: `.agent-presets/blog.md`
- Sistema SaaS React: `.agent-presets/saas-react.md`
- Manutenção geral: `.agent-presets/maintenance.md`
- Auditoria de release: `.agent-presets/audit-release.md`

## Skills instaladas

As skills locais ficam em `.agent-skills/` e foram selecionadas a partir do catálogo do Tech Leads Club Agent Skills. Quando uma skill upstream inclui arquivos auxiliares como `references/`, `scripts/`, `rules/` ou `assets/`, esses arquivos devem acompanhar a cópia local para que a skill funcione como previsto.

- accessibility
- best-practices
- codenavi
- coding-guidelines
- core-web-vitals
- docs-writer
- frontend-design
- mermaid-studio
- perf-lighthouse
- playwright-skill
- react-best-practices
- security-best-practices
- seo
- technical-design-doc-creator
- tlc-spec-driven
- web-quality-audit

## Origem das skills

- Repositório: https://github.com/tech-leads-club/agent-skills
- Site: https://tech-leads-club.github.io/agent-skills/
- Registry consultado: https://github.com/tech-leads-club/agent-skills/blob/main/packages/skills-catalog/skills-registry.json

## Regra de atualização

1. Atualizar skills de forma intencional, preferencialmente em uma branch própria.
2. Comparar mudanças relevantes com o registry upstream antes de substituir conteúdo local.
3. Não editar skills copiadas sem registrar a decisão no histórico do projeto.
4. Atualizar este manifesto quando presets, skills ou regras de uso mudarem.
5. Validar links e caminhos após qualquer atualização.

## Sugestões futuras

Não foram adicionadas novas skills além das já instaladas. Para evoluções futuras, avaliar skills de arquitetura e tooling do registry original apenas quando houver demanda real, por exemplo:

- coupling-analysis
- modular-decomposition
- component-common-domain-detection
- chrome-devtools
- gh-fix-ci
