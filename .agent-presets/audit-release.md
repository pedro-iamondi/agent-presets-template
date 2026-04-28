# Preset: Audit Release

Leia também: `.agent-presets/base.md`.

Todos os caminhos citados neste preset são relativos à raiz do projeto.

## Objetivo

Auditar o projeto antes de release/deploy, encontrando riscos de qualidade, SEO, performance, acessibilidade, segurança, regressão visual e problemas de build.

## Quando usar

- Antes de publicar landing page.
- Antes de publicar blog ou nova estrutura de conteúdo.
- Antes de deploy de feature SaaS relevante.
- Antes de entregar versão para cliente.
- Após refactor significativo.

## Quando não usar

Não usar para correções pequenas durante desenvolvimento diário, a menos que a correção toque área crítica.

## Skills principais

- [web-quality-audit](.agent-skills/web-quality-audit/SKILL.md) ([web](https://agent-skills.techleads.club/skills/web-quality-audit/))
- [best-practices](.agent-skills/best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/best-practices/))
- [core-web-vitals](.agent-skills/core-web-vitals/SKILL.md) ([web](https://agent-skills.techleads.club/skills/core-web-vitals/))
- [perf-lighthouse](.agent-skills/perf-lighthouse/SKILL.md) ([web](https://agent-skills.techleads.club/skills/perf-lighthouse/))
- [seo](.agent-skills/seo/SKILL.md) ([web](https://agent-skills.techleads.club/skills/seo/))
- [accessibility](.agent-skills/accessibility/SKILL.md) ([web](https://agent-skills.techleads.club/skills/accessibility/))
- [security-best-practices](.agent-skills/security-best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/security-best-practices/))
- [playwright-skill](.agent-skills/playwright-skill/SKILL.md) ([web](https://agent-skills.techleads.club/skills/playwright-skill/))

## Estratégia para poupar tokens

- Não carregar todos os documentos do projeto.
- Primeiro rodar checks automáticos disponíveis.
- Depois inspecionar apenas áreas com falha ou alto risco.
- Priorizar achados por severidade.
- Não refatorar durante auditoria sem autorização explícita.

## Checklist de auditoria

### Build e qualidade

- Instalação reproduzível.
- Build passa.
- Typecheck passa.
- Lint passa.
- Testes relevantes passam.
- Sem logs/debugs indevidos.

### Segurança

- Nenhum secret exposto no client.
- Variáveis de ambiente revisadas.
- Inputs e formulários validados.
- Fluxos autenticados revisados.
- Dependências novas justificadas.

### SEO, quando página pública

- Title e description.
- Canonical.
- Open Graph.
- Sitemap/robots quando aplicável.
- Heading structure.
- Conteúdo indexável.

### Performance

- Bundle sem crescimento injustificado.
- Imagens otimizadas.
- Fontes otimizadas.
- Client Components usados somente quando necessário.
- Sem layout shift óbvio.

### Acessibilidade

- Navegação por teclado.
- Contraste adequado.
- Labels em formulários.
- Alt text em imagens relevantes.
- Sem uso incorreto de ARIA.

### UX

- Estados loading, empty, error e success.
- Responsividade.
- CTAs ou ações principais funcionando.
- Mensagens de erro compreensíveis.

## Saída esperada

Gerar relatório curto com:

```md
# Audit Release

## Resultado
Aprovado | Aprovado com ressalvas | Bloqueado

## Bloqueadores
- ...

## Recomendações antes do deploy
- ...

## Melhorias não bloqueantes
- ...

## Validações executadas
- ...

## Arquivos ou áreas revisadas
- ...
```

## Regra importante

Auditoria deve primeiro reportar. Só corrigir automaticamente quando o usuário pedir explicitamente ou quando for correção trivial e segura.
