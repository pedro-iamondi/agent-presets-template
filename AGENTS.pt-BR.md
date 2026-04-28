# AGENTS.md

Instruções operacionais para agentes de desenvolvimento neste projeto.

## Autor

Este projeto foi elaborado por Pedro H. Iamondi.

- LinkedIn: https://www.linkedin.com/in/pedro-henrique-iamondi
- Instagram: https://www.instagram.com/peh.iamondi/

## Objetivo

Padronizar como agentes trabalham em projetos da empresa, reduzindo retrabalho, alucinações, decisões inconsistentes e consumo desnecessário de tokens.

## Regra principal

Antes de executar qualquer tarefa, o agente deve:

1. Ler este `AGENTS.md`.
2. Identificar o tipo de tarefa.
3. Carregar apenas o preset necessário em `.agent-presets/`.
4. Inspecionar o código real antes de sugerir ou alterar arquivos.
5. Evitar carregar documentos, specs ou skills que não sejam relevantes para a tarefa atual.

## Convenção de caminhos

Todos os caminhos citados neste template são relativos à raiz do projeto onde o template foi instalado, salvo quando indicado explicitamente.

Exemplos:

- `.agent-presets/base.md`
- `.agent-skills/seo/SKILL.md`
- `scratch/`

## Presets disponíveis

- Landing page Next.js: `.agent-presets/landing-page.md`
- Blog Next.js: `.agent-presets/blog.md`
- Sistema SaaS React: `.agent-presets/saas-react.md`
- Manutenção geral: `.agent-presets/maintenance.md`
- Auditoria de release: `.agent-presets/audit-release.md`
- Base comum: `.agent-presets/base.md`

## Quando usar SDD

Use SDD completo apenas para:

- Projeto novo.
- Feature nova fora do escopo original.
- Mudança estrutural ou arquitetural.
- Alteração que impacta várias áreas do sistema.
- Mudança com risco em dados, autenticação, pagamentos, permissões, SEO público ou performance crítica.

Não use SDD completo para:

- Correções pequenas.
- Ajustes visuais simples.
- Refactors locais.
- Ajustes de copy.
- Correção de lint, tipos ou testes.
- Alterações em até 3 arquivos sem impacto arquitetural.

Para tarefas pequenas, use modo rápido:

1. Entender o problema.
2. Inspecionar arquivos relevantes.
3. Aplicar menor mudança segura.
4. Validar.
5. Registrar aprendizado somente se o erro for recorrente ou relevante.

## Skills baseadas no Tech Leads Club Agent Skills

Repositório principal:

- https://github.com/tech-leads-club/agent-skills
- https://tech-leads-club.github.io/agent-skills/

Skills principais usadas por estes presets:

- [tlc-spec-driven](.agent-skills/tlc-spec-driven/SKILL.md) ([web](https://agent-skills.techleads.club/skills/tlc-spec-driven/))
- [seo](.agent-skills/seo/SKILL.md) ([web](https://agent-skills.techleads.club/skills/seo/))
- [best-practices](.agent-skills/best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/best-practices/))
- [core-web-vitals](.agent-skills/core-web-vitals/SKILL.md) ([web](https://agent-skills.techleads.club/skills/core-web-vitals/))
- [technical-design-doc-creator](.agent-skills/technical-design-doc-creator/SKILL.md) ([web](https://agent-skills.techleads.club/skills/technical-design-doc-creator/))
- [frontend-design](.agent-skills/frontend-design/SKILL.md) ([web](https://agent-skills.techleads.club/skills/frontend-design/))

Skills recomendadas para instalar junto:

- [security-best-practices](.agent-skills/security-best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/security-best-practices/))
- [accessibility](.agent-skills/accessibility/SKILL.md) ([web](https://agent-skills.techleads.club/skills/accessibility/))
- [react-best-practices](.agent-skills/react-best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/react-best-practices/))
- [playwright-skill](.agent-skills/playwright-skill/SKILL.md) ([web](https://agent-skills.techleads.club/skills/playwright-skill/))
- [web-quality-audit](.agent-skills/web-quality-audit/SKILL.md) ([web](https://agent-skills.techleads.club/skills/web-quality-audit/))
- [perf-lighthouse](.agent-skills/perf-lighthouse/SKILL.md) ([web](https://agent-skills.techleads.club/skills/perf-lighthouse/))
- [codenavi](.agent-skills/codenavi/SKILL.md) ([web](https://agent-skills.techleads.club/skills/codenavi/))
- [mermaid-studio](.agent-skills/mermaid-studio/SKILL.md) ([web](https://agent-skills.techleads.club/skills/mermaid-studio/))
- [docs-writer](.agent-skills/docs-writer/SKILL.md) ([web](https://agent-skills.techleads.club/skills/docs-writer/))
- [coding-guidelines](.agent-skills/coding-guidelines/SKILL.md) ([web](https://agent-skills.techleads.club/skills/coding-guidelines/))

## Estratégia para poupar tokens

- Carregar `base.md` sempre.
- Carregar apenas um preset específico por tarefa.
- Não carregar SDD completo para tarefas pequenas.
- Não carregar múltiplos presets simultaneamente, exceto em auditoria final.
- Não resumir arquivos inteiros sem necessidade.
- Não ler todas as specs se a tarefa toca apenas uma feature.
- Preferir inspeção pontual de arquivos reais.
- Evitar repetir no chat o conteúdo integral de arquivos já existentes.

## Ordem de prioridade das instruções

Quando houver conflito, seguir esta ordem:

1. Instruções explícitas do usuário na conversa atual.
2. Regras de segurança e políticas do ambiente.
3. `AGENTS.md`.
4. Preset específico em `.agent-presets/`.
5. Documentação do projeto.
6. Convenções inferidas do código.

## Regra anti-alucinação

Nunca inventar:

- Arquivos.
- Rotas.
- Variáveis de ambiente.
- APIs.
- Bibliotecas instaladas.
- Estrutura de banco.
- Regras de negócio.
- Decisões de produto.

Se não encontrar evidência no projeto, declarar incerteza e propor verificação.

## Registro de aprendizados

Quando um erro for corrigido e for provável que aconteça novamente, sugerir registrar em um arquivo de memória do projeto, por exemplo:

- `.agent-memory/known-errors.md`
- `.agent-memory/lessons-learned.md`
- `.agent-memory/project-decisions.md`

Não registrar todo erro pequeno. Registrar apenas padrões reutilizáveis.

Modelo recomendado:

```md
## YYYY-MM-DD — título curto

### Contexto
O que estava sendo feito.

### Erro
O que aconteceu.

### Causa raiz
Por que aconteceu.

### Como evitar
Checklist prático para não repetir.

### Regra para agentes
Instrução curta e reutilizável.
```

## Encerramento de tarefa

Ao finalizar, responder de forma objetiva com:

- O que foi feito.
- Arquivos alterados.
- Como foi validado.
- Riscos ou pendências.
- Se algum aprendizado deveria ser registrado.
