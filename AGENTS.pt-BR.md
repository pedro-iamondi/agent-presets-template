# AGENTS.md

Instruções operacionais para agentes de desenvolvimento neste projeto.

## Autor

Este projeto foi elaborado por Pedro H. Iamondi.

- [Pedro H. Iamondi no LinkedIn](https://www.linkedin.com/in/pedro-henrique-iamondi)
- [Pedro H. Iamondi no Instagram](https://www.instagram.com/peh.iamondi/)

## Objetivo

Padronizar como agentes trabalham em projetos da empresa. Use este template
para reduzir retrabalho, alucinações, decisões inconsistentes e consumo
desnecessário de tokens.

## Regra principal

Antes de executar qualquer tarefa, o agente deve:

1. Ler este `AGENTS.md`.
2. Identificar o tipo de tarefa.
3. Carregar apenas o preset necessário em `.agent-presets/`.
4. Inspecionar o código real antes de sugerir ou alterar arquivos.
5. Evitar carregar documentos, specs ou skills que não sejam relevantes para a
   tarefa.

## Convenção de caminhos

Todos os caminhos citados neste template são relativos à raiz do projeto onde o
template foi instalado, salvo quando indicado explicitamente.

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

## Uso de SDD

Use SDD completo apenas para:

- Projeto novo.
- Feature nova fora do escopo original.
- Mudança estrutural ou arquitetural.
- Alteração que impacta várias áreas do sistema.
- Mudança com risco em dados, autenticação, pagamentos, permissões, SEO público
  ou performance crítica.

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
3. Aplicar a menor mudança segura.
4. Validar.
5. Registrar aprendizado somente se o erro for recorrente ou relevante.

## Skills do Tech Leads Club

Estes presets usam skills baseadas no Tech Leads Club Agent Skills:

- [Repositório Tech Leads Club Agent Skills](https://github.com/tech-leads-club/agent-skills)
- [Site Tech Leads Club Agent Skills](https://tech-leads-club.github.io/agent-skills/)

Skills principais usadas por estes presets:

- [Skill local tlc-spec-driven](.agent-skills/tlc-spec-driven/SKILL.md)
  ([referência web tlc-spec-driven](https://agent-skills.techleads.club/skills/tlc-spec-driven/))
- [Skill local seo](.agent-skills/seo/SKILL.md)
  ([referência web seo](https://agent-skills.techleads.club/skills/seo/))
- [Skill local best-practices](.agent-skills/best-practices/SKILL.md)
  ([referência web best-practices](https://agent-skills.techleads.club/skills/best-practices/))
- [Skill local core-web-vitals](.agent-skills/core-web-vitals/SKILL.md)
  ([referência web core-web-vitals](https://agent-skills.techleads.club/skills/core-web-vitals/))
- [Skill local technical-design-doc-creator](.agent-skills/technical-design-doc-creator/SKILL.md)
  ([referência web technical-design-doc-creator](https://agent-skills.techleads.club/skills/technical-design-doc-creator/))
- [Skill local frontend-design](.agent-skills/frontend-design/SKILL.md)
  ([referência web frontend-design](https://agent-skills.techleads.club/skills/frontend-design/))

Skills recomendadas para instalar junto:

- [Skill local security-best-practices](.agent-skills/security-best-practices/SKILL.md)
  ([referência web security-best-practices](https://agent-skills.techleads.club/skills/security-best-practices/))
- [Skill local accessibility](.agent-skills/accessibility/SKILL.md)
  ([referência web accessibility](https://agent-skills.techleads.club/skills/accessibility/))
- [Skill local react-best-practices](.agent-skills/react-best-practices/SKILL.md)
  ([referência web react-best-practices](https://agent-skills.techleads.club/skills/react-best-practices/))
- [Skill local playwright-skill](.agent-skills/playwright-skill/SKILL.md)
  ([referência web playwright-skill](https://agent-skills.techleads.club/skills/playwright-skill/))
- [Skill local web-quality-audit](.agent-skills/web-quality-audit/SKILL.md)
  ([referência web web-quality-audit](https://agent-skills.techleads.club/skills/web-quality-audit/))
- [Skill local perf-lighthouse](.agent-skills/perf-lighthouse/SKILL.md)
  ([referência web perf-lighthouse](https://agent-skills.techleads.club/skills/perf-lighthouse/))
- [Skill local codenavi](.agent-skills/codenavi/SKILL.md)
  ([referência web codenavi](https://agent-skills.techleads.club/skills/codenavi/))
- [Skill local mermaid-studio](.agent-skills/mermaid-studio/SKILL.md)
  ([referência web mermaid-studio](https://agent-skills.techleads.club/skills/mermaid-studio/))
- [Skill local docs-writer](.agent-skills/docs-writer/SKILL.md)
  ([referência web docs-writer](https://agent-skills.techleads.club/skills/docs-writer/))
- [Skill local coding-guidelines](.agent-skills/coding-guidelines/SKILL.md)
  ([referência web coding-guidelines](https://agent-skills.techleads.club/skills/coding-guidelines/))

## Estratégia para poupar tokens

- Carregar `base.md` sempre.
- Carregar apenas um preset específico por tarefa.
- Não carregar SDD completo para tarefas pequenas.
- Não carregar múltiplos presets simultaneamente, exceto em auditoria final.
- Não resumir arquivos inteiros sem necessidade.
- Não ler todas as specs se a tarefa toca apenas uma feature.
- Preferir inspeção pontual de arquivos reais.
- Evitar repetir no chat o conteúdo integral de arquivos já existentes.

## Prioridade das instruções

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

Quando um erro for corrigido e for provável que aconteça novamente, sugerir o
registro em um arquivo de memória do projeto, por exemplo:

- `.agent-memory/known-errors.md`
- `.agent-memory/lessons-learned.md`
- `.agent-memory/project-decisions.md`

Não registrar todo erro pequeno. Registrar apenas padrões reutilizáveis.

Modelo recomendado:

```md
## YYYY-MM-DD - título curto

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
