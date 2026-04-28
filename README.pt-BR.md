# Agent Presets Template

Este repositório fornece uma estrutura padronizada para orientar agentes de IA (como Cursor, Claude, Cline, etc.) durante o ciclo de desenvolvimento de software da empresa. 

O objetivo principal é reduzir alucinações, economizar tokens e garantir consistência na arquitetura, segurança e qualidade do código através de "revelação progressiva" de contexto.

## Autor

Elaborado por Pedro H. Iamondi.

*   LinkedIn: https://www.linkedin.com/in/pedro-henrique-iamondi
*   Instagram: https://www.instagram.com/peh.iamondi/

## 📂 Estrutura do Projeto

A estrutura foi desenhada para ser modular, evitando que o agente leia instruções desnecessárias para tarefas simples.

*   `AGENTS.md`: O "ponto de entrada". Contém as regras globais, políticas de uso e o guia de quando usar cada preset.
*   `MANIFEST.md`: Catálogo do template. Lista versão, presets, skills instaladas, origem das skills e regra de atualização.
*   `.agent-presets/`: Arquivos de contexto focados em cenários específicos (ex: landing pages, blogs, SaaS). Eles instruem o agente sobre como abordar aquele tipo de projeto e quais skills ele precisa consultar.
*   `.agent-skills/`: Cópias locais das skills oficiais do [Tech Leads Club](https://github.com/tech-leads-club/agent-skills). São manuais detalhados sobre domínios específicos de engenharia (SEO, acessibilidade, segurança, React, arquitetura, etc).
*   `scratch/`: Pasta para rascunhos descartáveis, relatórios intermediários e outputs temporários de agentes.

## 🧭 Convenção de Caminhos

Todos os caminhos citados neste template são relativos à **raiz do projeto** onde ele foi instalado.

Exemplos:

*   `.agent-presets/base.md`
*   `.agent-presets/saas-react.md`
*   `.agent-skills/seo/SKILL.md`
*   `scratch/`

## 🚀 Como Instalar

Esta estrutura foi feita para ser portátil. Você pode cloná-la para iniciar um projeto do zero ou integrá-la a um repositório existente.

### Para um projeto existente:
1. Faça o download ou clone este repositório.
2. Copie o arquivo `AGENTS.md` para a **raiz** do seu projeto atual.
3. Copie o `MANIFEST.md` e as pastas `.agent-presets/`, `.agent-skills/` e `scratch/` para a **raiz** do seu projeto.

### Para um novo projeto:
1. Clone este repositório.
2. Inicialize seu framework (Next.js, Vite, etc) dentro desta mesma pasta.
3. Comece a codar com a ajuda do seu agente.

## 🧠 Como Utilizar

A regra de ouro é **não carregar tudo de uma vez**. Isso consome muitos tokens e confunde o agente.

O fluxo ideal de trabalho é:

1.  **Contexto Base:** Sempre que iniciar uma nova conversa ou projeto, certifique-se de que o agente leia o `AGENTS.md`. Em ferramentas como o Cursor, você pode referenciar `@AGENTS.md` ou adicioná-lo às regras do workspace.
2.  **Base comum:** O agente deve carregar `.agent-presets/base.md` sempre.
3.  **Direcionamento:** Diga ao agente qual o seu objetivo e peça para ele carregar no máximo um preset específico em `.agent-presets/`, salvo auditoria final.
    *   *Exemplo de Prompt:* "Preciso que você crie a página de preços. Leia o `AGENTS.md` primeiro e veja qual preset em `.agent-presets/` melhor se aplica."
    *   *Exemplo Direto:* "@.agent-presets/saas-react.md Crie um formulário de login seguindo estas diretrizes."

Use o `MANIFEST.md` como catálogo do template quando precisar revisar quais presets e skills estão disponíveis.

## ⚖️ Quando usar Presets vs Skills

Entender a diferença entre os dois ajuda a guiar melhor a IA:

*   **Presets (`.agent-presets/`)**: São o seu **Ponto de Partida**. Você os invoca quando vai iniciar uma tarefa (ex: criar uma landing page, fazer uma auditoria de release). O preset define o "clima" da tarefa e orquestra o trabalho.
*   **Skills (`.agent-skills/`)**: São as **Ferramentas Especializadas**. Na maioria das vezes, **você não precisa invocar as skills manualmente**. Os presets já contêm links para elas. Quando o agente, instruído por um preset, precisar aplicar uma regra de SEO, ele mesmo irá até a pasta `.agent-skills/seo/SKILL.md` para aprender como fazer isso da forma correta.

## 📏 Dimensionamento de Tarefas (Poupando Tokens)

Para evitar que o agente perca tempo e consuma muitos tokens analisando toda a arquitetura para fazer uma simples mudança, sempre direcione o escopo da sua solicitação. A estrutura instrui o agente a operar em três modos principais:

### 1. Tarefas Pequenas (Modo `quick`)
*   **O que é:** Correção de cor, ajustes de posição, refatorações locais isoladas, correção de typos ou ajustes em até 3 arquivos (ex: mexer num botão).
*   **Como solicitar:** Seja direto, informe o arquivo e classifique a tarefa para evitar leituras desnecessárias.
    *   *Exemplo:* "Ajuste a margem do botão primário no `Header.tsx` para `mt-4`. Considere isso uma tarefa `quick`."

### 2. Tarefas Médias (Modo `standard`)
*   **O que é:** Alterar ou implementar uma pequena feature que já estava pré-definida no escopo e na arquitetura atual (ex: adicionar um novo campo num formulário existente, ou criar um novo componente visual baseado em outro).
*   **Como solicitar:** Peça para o agente ler o preset específico da área e inspecionar o código antes de implementar, mas sem criar documentação excessiva.
    *   *Exemplo:* "@.agent-presets/saas-react.md Vamos adicionar o campo 'Telefone' no perfil do usuário. Inspecione os componentes relevantes e implemente como uma tarefa `standard`."

### 3. Tarefas Grandes (Modo `full-sdd`)
*   **O que é:** Criar uma feature que não foi planejada anteriormente, criar um novo projeto do zero, fazer integrações complexas (ex: novo gateway de pagamento) ou mudanças na arquitetura principal.
*   **Como solicitar:** Exija que o agente crie um documento de planejamento técnico (SDD - *Software Design Document*) antes de codar. O agente irá carregar skills pesadas de arquitetura para isso.
    *   *Exemplo:* "Precisamos criar um novo painel de relatórios (dashboard) do zero. Leia o `@AGENTS.md`, carregue o preset `@.agent-presets/saas-react.md` e inicie uma tarefa `full-sdd`. Crie o documento de design técnico para eu revisar antes de programarmos."

## 💬 Exemplos de Prompts por Cenário

### Tarefa quick

> Leia o `AGENTS.md` e trate isso como tarefa `quick`. Ajuste a margem do botão primário em `Header.tsx`, inspecione apenas os arquivos relevantes e valide com o menor check aplicável.

### Landing page

> Leia o `AGENTS.md`, carregue `.agent-presets/base.md` e `.agent-presets/landing-page.md`. Crie a seção de preços da landing, mantendo SEO, acessibilidade e performance. Antes de alterar, inspecione os componentes existentes.

### Blog ou post

> Leia o `AGENTS.md`, carregue `.agent-presets/base.md` e `.agent-presets/blog.md`. Adicione um novo post seguindo a estrutura atual de conteúdo, validando slug, metadata e links internos.

### SaaS React

> Leia o `AGENTS.md`, carregue `.agent-presets/base.md` e `.agent-presets/saas-react.md`. Adicione o campo "Telefone" no perfil do usuário, reutilizando padrões existentes e tratando loading, erro e sucesso.

### Manutenção geral

> Leia o `AGENTS.md`, carregue `.agent-presets/base.md` e `.agent-presets/maintenance.md`. Investigue por que o filtro da tabela não atualiza corretamente, encontre a causa raiz, aplique a menor correção segura e valide o fluxo.

### Auditoria de release

> Leia o `AGENTS.md`, carregue `.agent-presets/base.md` e `.agent-presets/audit-release.md`. Faça uma auditoria antes do deploy e reporte bloqueadores, recomendações e validações executadas. Não corrija automaticamente sem autorização.

### Feature full-sdd

> Leia o `AGENTS.md`, carregue `.agent-presets/base.md` e o preset específico mais adequado. Esta é uma tarefa `full-sdd`: crie primeiro o documento de design técnico para revisão antes de implementar.
