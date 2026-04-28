# Preset Base

Use este preset em todas as tarefas.

Todos os caminhos citados neste preset são relativos à raiz do projeto.

## Objetivo

Trabalhar com segurança, pouco retrabalho e baixo consumo de tokens.

## Modo de execução

Antes de agir:

1. Classifique a tarefa como `quick`, `standard` ou `full-sdd`.
2. Leia somente os arquivos necessários.
3. Inspecione o código real antes de propor alterações.
4. Liste mentalmente os arquivos prováveis de impacto.
5. Execute a menor mudança que resolve o problema.

## Classificação de tarefa

### quick

Use para:

- Bug pequeno.
- Ajuste visual simples.
- Copy.
- Lint.
- Tipagem.
- Teste quebrado.
- Alteração em até 3 arquivos.

Não criar SDD. Não criar TDD. Não gerar documentação extensa.

### standard

Use para:

- Feature pequena ou média já prevista.
- Alteração em fluxo existente.
- Nova tela simples.
- Integração pequena.

Criar apenas notas curtas de decisão se necessário.

### full-sdd

Use para:

- Projeto novo.
- Feature nova fora do escopo original.
- Mudança arquitetural.
- Mudança com impacto em dados, autenticação, autorização, billing, SEO público ou performance crítica.
- Alteração que exige alinhamento de produto.

Usar `tlc-spec-driven` e, se necessário, `technical-design-doc-creator`.

## Skills comuns

- [best-practices](.agent-skills/best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/best-practices/))
- [security-best-practices](.agent-skills/security-best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/security-best-practices/))
- [coding-guidelines](.agent-skills/coding-guidelines/SKILL.md) ([web](https://agent-skills.techleads.club/skills/coding-guidelines/))
- [docs-writer](.agent-skills/docs-writer/SKILL.md) ([web](https://agent-skills.techleads.club/skills/docs-writer/))
- [codenavi](.agent-skills/codenavi/SKILL.md) ([web](https://agent-skills.techleads.club/skills/codenavi/))

## Regras anti-alucinação

- Não assumir stack: verificar `package.json`, configs e estrutura.
- Não assumir rotas: verificar diretórios reais.
- Não assumir componentes: pesquisar antes de criar duplicados.
- Não assumir padrões: observar arquivos similares.
- Não instalar dependência sem verificar necessidade e impacto.
- Não inventar APIs ou props.
- Quando incerto, dizer: `Não encontrei evidência no projeto para X`.

## Verificação mínima

Sempre que possível, rodar validação adequada à mudança:

- Typecheck.
- Lint.
- Testes relevantes.
- Build.
- Teste manual do fluxo alterado.

Se não puder validar, informar claramente.

## Registro de erro recorrente

Após corrigir erro relevante, sugerir entrada em `.agent-memory/known-errors.md` com:

- Contexto.
- Erro.
- Causa raiz.
- Como evitar.
- Regra para agentes.

Não transformar correções duvidosas em regra permanente sem revisão humana.
