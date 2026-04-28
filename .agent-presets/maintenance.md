# Preset: Manutenção Geral

Leia também: `.agent-presets/base.md`.

Todos os caminhos citados neste preset são relativos à raiz do projeto.

## Objetivo

Manter código existente com segurança, foco e baixo retrabalho, cobrindo bugfixes, investigações, refactors locais, melhorias pequenas ou médias e redução de dívida técnica.

## Quando usar

- Bugfix em código existente.
- Investigação de fluxo ou comportamento.
- Refactor local sem mudança arquitetural.
- Melhoria pequena ou média já alinhada.
- Ajuste de testes, lint, tipos ou qualidade.
- Redução pontual de dívida técnica.
- Tarefa de manutenção recorrente sem preset mais específico.

## Quando nao usar

- Landing page, blog ou SaaS quando houver preset específico mais adequado.
- Auditoria final de release ou pre-deploy.
- Projeto novo, módulo novo grande ou mudança arquitetural.
- Alterações com impacto amplo em dados, autenticação, autorização, billing, SEO público ou performance crítica.

Nesses casos, use o preset específico ou `full-sdd` conforme o risco.

## Skills principais

- [codenavi](.agent-skills/codenavi/SKILL.md) ([web](https://agent-skills.techleads.club/skills/codenavi/))
- [coding-guidelines](.agent-skills/coding-guidelines/SKILL.md) ([web](https://agent-skills.techleads.club/skills/coding-guidelines/))
- [best-practices](.agent-skills/best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/best-practices/))

## Skills condicionais

- [docs-writer](.agent-skills/docs-writer/SKILL.md) ([web](https://agent-skills.techleads.club/skills/docs-writer/)): usar apenas quando a tarefa gerar decisão, aprendizado ou documentação reutilizável.
- [react-best-practices](.agent-skills/react-best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/react-best-practices/)): usar apenas em projetos React.
- [security-best-practices](.agent-skills/security-best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/security-best-practices/)): usar quando tocar dados, autenticação, autorização, inputs, envs, permissões ou segredos.
- [playwright-skill](.agent-skills/playwright-skill/SKILL.md) ([web](https://agent-skills.techleads.club/skills/playwright-skill/)): usar quando houver fluxo web a validar.

## Fluxo recomendado

1. Classificar a tarefa como `quick`, `standard` ou `full-sdd`.
2. Reproduzir ou entender o problema antes de alterar.
3. Inspecionar arquivos reais e buscar padrões similares.
4. Aplicar a menor mudança segura.
5. Validar com checks proporcionais ao risco.
6. Registrar aprendizado apenas se o erro for recorrente ou relevante.

## Regras de manutenção

- Não criar abstração sem repetição real ou complexidade comprovada.
- Não substituir padrão local por preferência pessoal.
- Não instalar dependência para resolver problema local sem justificativa forte.
- Não ampliar escopo de refactor durante bugfix.
- Preservar compatibilidade de APIs, rotas, props e contratos existentes.
- Quando encontrar comportamento incerto, buscar evidência no código antes de assumir.

## Checklist de aceite

- Causa raiz ou motivação da mudança compreendida.
- Mudança limitada aos arquivos relevantes.
- Fluxo ou caso corrigido validado.
- Typecheck, lint, teste ou build executado quando aplicável.
- Riscos e pendências informados no encerramento.
