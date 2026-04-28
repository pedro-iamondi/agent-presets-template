# Preset: Sistema SaaS React

Leia também: `.agent-presets/base.md`.

Todos os caminhos citados neste preset são relativos à raiz do projeto.

## Objetivo

Criar e manter sistemas SaaS em React com foco em arquitetura limpa, segurança, usabilidade, consistência visual, testes e manutenção.

## Quando usar

- Dashboards.
- Backoffice.
- Áreas autenticadas.
- Fluxos de usuário dentro do produto.
- CRUDs, formulários, permissões e integrações internas.

## Quando não usar SDD completo

Não usar SDD completo para:

- Correção visual local.
- Ajuste de texto.
- Bug pequeno em componente isolado.
- Ajuste de validação simples.
- Fix de lint/tipo/teste.
- Refactor local sem mudança de comportamento.

Use modo `quick`.

## Quando usar full-sdd

Usar SDD quando:

- Criar módulo novo.
- Criar fluxo novo de usuário.
- Alterar permissões, autenticação ou autorização.
- Alterar modelo de dados.
- Integrar API externa relevante.
- Mudar arquitetura de estado, roteamento ou design system.
- Impactar billing, dados sensíveis ou auditoria.

## Skills principais

- [tlc-spec-driven](.agent-skills/tlc-spec-driven/SKILL.md) ([web](https://agent-skills.techleads.club/skills/tlc-spec-driven/))
- [technical-design-doc-creator](.agent-skills/technical-design-doc-creator/SKILL.md) ([web](https://agent-skills.techleads.club/skills/technical-design-doc-creator/))
- [react-best-practices](.agent-skills/react-best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/react-best-practices/))
- [frontend-design](.agent-skills/frontend-design/SKILL.md) ([web](https://agent-skills.techleads.club/skills/frontend-design/))
- [best-practices](.agent-skills/best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/best-practices/))
- [security-best-practices](.agent-skills/security-best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/security-best-practices/))
- [accessibility](.agent-skills/accessibility/SKILL.md) ([web](https://agent-skills.techleads.club/skills/accessibility/))
- [playwright-skill](.agent-skills/playwright-skill/SKILL.md) ([web](https://agent-skills.techleads.club/skills/playwright-skill/))
- [codenavi](.agent-skills/codenavi/SKILL.md) ([web](https://agent-skills.techleads.club/skills/codenavi/))

## Fluxo recomendado

### Feature nova

1. Especificar objetivo, usuários, estados e regras de negócio.
2. Mapear componentes, rotas, dados e permissões.
3. Verificar padrões existentes no código.
4. Implementar incrementalmente.
5. Validar tipos, estados vazios, loading, erro e sucesso.
6. Testar fluxo principal.

### Correção pequena

1. Reproduzir ou entender o erro.
2. Identificar causa raiz.
3. Aplicar menor correção possível.
4. Validar cenário corrigido e possíveis regressões.
5. Registrar aprendizado se for erro recorrente.

## Regras React

- Evitar estado global sem necessidade.
- Separar lógica de apresentação quando fizer sentido.
- Não duplicar componentes existentes.
- Reutilizar design system do projeto.
- Evitar `useEffect` para derivar estado simples.
- Tratar loading, empty, error e success states.
- Validar permissões no frontend apenas como UX; segurança real deve estar no backend.
- Não expor secrets no client.

## Checklist de aceite

- Fluxo principal funciona.
- Estados loading/empty/error tratados.
- Sem regressão visual óbvia.
- Sem dependências desnecessárias.
- Typecheck/lint/testes relevantes passam.
- Permissões e dados sensíveis revisados quando aplicável.
