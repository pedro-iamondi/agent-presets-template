# Agent Presets Template

Este repositório fornece uma estrutura padronizada para orientar agentes de IA,
como Cursor, Claude, Cline e outros, durante o ciclo de desenvolvimento de
software da empresa.

Use este template para reduzir alucinações, economizar tokens e manter
arquitetura, segurança e qualidade de código consistentes por meio de
revelação progressiva de contexto.

## Autor

Elaborado por Pedro H. Iamondi.

- [Pedro H. Iamondi no LinkedIn](https://www.linkedin.com/in/pedro-henrique-iamondi)
- [Pedro H. Iamondi no Instagram](https://www.instagram.com/peh.iamondi/)

## Estrutura do projeto

A estrutura é modular para que agentes não precisem ler instruções
desnecessárias em tarefas simples.

- `AGENTS.md`: Ponto de entrada com regras globais, políticas de uso e
  orientação sobre quando usar cada preset.
- `AGENTS.pt-BR.md`: Cópia em português das instruções para agentes.
- `MANIFEST.md`: Catálogo do template com versão, presets, skills instaladas,
  origem das skills e regra de atualização.
- `MANIFEST.pt-BR.md`: Cópia em português do manifesto.
- `.agent-presets/`: Arquivos de contexto focados em cenários específicos,
  como landing pages, blogs e SaaS. Eles explicam como o agente deve abordar
  cada tipo de projeto e quais skills consultar.
- `.agent-skills/`: Cópias locais das
  [Tech Leads Club Agent Skills](https://github.com/tech-leads-club/agent-skills).
  Elas são manuais detalhados para domínios de engenharia como SEO,
  acessibilidade, segurança, React e arquitetura.
- `scratch/`: Pasta para rascunhos descartáveis, relatórios intermediários e
  outputs temporários de agentes.
- `README.pt-BR.md`: Cópia em português deste README.

## Convenção de caminhos

Todos os caminhos citados neste template são relativos à **raiz do projeto**
onde o template foi instalado.

Exemplos:

- `.agent-presets/base.md`
- `.agent-presets/saas-react.md`
- `.agent-skills/seo/SKILL.md`
- `scratch/`

## Instalação

Esta estrutura é portátil. Você pode cloná-la para iniciar um projeto novo ou
integrá-la a um repositório existente.

### Projeto existente

1. Baixe ou clone este repositório.
2. Copie `AGENTS.md` para a **raiz** do seu projeto atual.
3. Copie `MANIFEST.md` e as pastas `.agent-presets/`, `.agent-skills/` e
   `scratch/` para a **raiz** do seu projeto.
4. Opcional: Copie os arquivos `*.pt-BR.md` se sua equipe quiser manter a
   documentação em português no projeto.

### Projeto novo

1. Clone este repositório.
2. Inicialize seu framework, como Next.js ou Vite, dentro desta mesma pasta.
3. Comece a desenvolver com apoio do agente.

## Uso

A regra principal é **não carregar tudo de uma vez**. Carregar contexto demais
consome tokens e pode confundir o agente.

Use este fluxo:

1. Comece pelo contexto base. Ao iniciar uma nova conversa ou projeto, garanta
   que o agente leia `AGENTS.md`. Em ferramentas como Cursor, você pode
   referenciar `@AGENTS.md` ou adicioná-lo às regras do workspace.
2. Carregue a base comum. O agente deve sempre carregar
   `.agent-presets/base.md`.
3. Direcione a tarefa. Diga ao agente qual é o objetivo e peça para carregar no
   máximo um preset específico em `.agent-presets/`, exceto em auditorias
   finais.

Use `MANIFEST.md` como catálogo do template quando precisar revisar quais
presets e skills estão disponíveis.

## Presets vs. skills

Entender a diferença ajuda você a orientar melhor a IA:

- **Presets (`.agent-presets/`)**: Use presets como ponto de partida ao iniciar
  uma tarefa, como criar uma landing page ou fazer uma auditoria de release. O
  preset define o contexto da tarefa e orquestra o trabalho.
- **Skills (`.agent-skills/`)**: Use skills como referências especializadas. Na
  maioria das vezes, você não precisa invocar skills manualmente. Os presets já
  apontam para elas. Quando um agente guiado por um preset precisar aplicar uma
  regra de SEO, ele deve consultar `.agent-skills/seo/SKILL.md`.

## Dimensionamento de tarefas

Para evitar gasto de tempo e tokens analisando toda a arquitetura para uma
mudança simples, direcione sempre o escopo da tarefa. A estrutura orienta
agentes a trabalhar em três modos principais.

### 1. Tarefas pequenas (modo `quick`)

Use o modo `quick` para mudanças de cor, ajustes de posição, refactors locais
isolados, correções de texto ou alterações em até 3 arquivos.

Exemplo de prompt:

> Ajuste a margem do botão primário em `Header.tsx` para `mt-4`. Trate isso
> como uma tarefa `quick`.

### 2. Tarefas médias (modo `standard`)

Use o modo `standard` para pequenas features que cabem no escopo e na
arquitetura atuais, como adicionar um campo a um formulário existente ou criar
um componente visual baseado em outro.

Exemplo de prompt:

> `@.agent-presets/saas-react.md` Adicione o campo "Telefone" no perfil do
> usuário. Inspecione os componentes relevantes e implemente como uma tarefa
> `standard`.

### 3. Tarefas grandes (modo `full-sdd`)

Use o modo `full-sdd` para features não planejadas, projetos novos, integrações
complexas ou mudanças na arquitetura principal. Peça ao agente para criar um
documento de planejamento técnico antes de programar.

Exemplo de prompt:

> Precisamos criar um dashboard de relatórios do zero. Leia `@AGENTS.md`,
> carregue `@.agent-presets/saas-react.md` e inicie uma tarefa `full-sdd`.
> Crie o documento de design técnico para revisão antes da implementação.

## Exemplos de prompts por cenário

### Tarefa quick

> Leia `AGENTS.md` e trate isso como uma tarefa `quick`. Ajuste a margem do
> botão primário em `Header.tsx`, inspecione apenas os arquivos relevantes e
> valide com o menor check aplicável.

### Landing page

> Leia `AGENTS.md`, carregue `.agent-presets/base.md` e
> `.agent-presets/landing-page.md`. Crie a seção de preços da landing mantendo
> SEO, acessibilidade e performance. Inspecione os componentes existentes antes
> de alterar arquivos.

### Blog ou post

> Leia `AGENTS.md`, carregue `.agent-presets/base.md` e
> `.agent-presets/blog.md`. Adicione um novo post seguindo a estrutura atual de
> conteúdo, validando slug, metadata e links internos.

### SaaS React

> Leia `AGENTS.md`, carregue `.agent-presets/base.md` e
> `.agent-presets/saas-react.md`. Adicione o campo "Telefone" no perfil do
> usuário, reutilizando padrões existentes e tratando loading, erro e sucesso.

### Manutenção geral

> Leia `AGENTS.md`, carregue `.agent-presets/base.md` e
> `.agent-presets/maintenance.md`. Investigue por que o filtro da tabela não
> atualiza corretamente, encontre a causa raiz, aplique a menor correção segura
> e valide o fluxo.

### Auditoria de release

> Leia `AGENTS.md`, carregue `.agent-presets/base.md` e
> `.agent-presets/audit-release.md`. Faça uma auditoria antes do deploy e
> reporte bloqueadores, recomendações e validações executadas. Não corrija
> automaticamente sem autorização.

### Feature full-SDD

> Leia `AGENTS.md`, carregue `.agent-presets/base.md` e o preset específico
> mais adequado. Esta é uma tarefa `full-sdd`: crie primeiro o documento de
> design técnico para revisão antes de implementar.
