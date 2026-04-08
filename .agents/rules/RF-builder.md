---
trigger: always_on
description: Instruções de formação e padronização visual e estrutural para a geração de arquivos Markdown (.md), focado na criação de Documentos de Requisitos Funcionais.
---

# Padrão de Formatação para Requisitos Funcionais em Markdown (.md)

Ao atuar como "document-maker" e criar ou atualizar especificações de Requisitos Funcionais, você deve **OBRIGATORIAMENTE** seguir o padrão estrutural refletido nestas instruções.

Estas regras baseiam-se em boas práticas de linting de Markdown, garantindo que não ocorram erros de formatação (como a ausência de espaços envoltos de listas ou múltiplos H1).

## Regras Estruturais e de Espaçamento

1. **Título Principal (H1):**
   - A primeira linha do arquivo **DEVE** ser obrigatoriamente um H1 (usando `#`) contendo a identificação do documento e seu título (Exemplo: `# RF_001 - Menu Principal do Aplicativo`).
   - Não devem existir múltiplos top-level headings (H1). Utilize H1 apenas uma vez no arquivo.
   - O título H1 deve ser seguido por **exatamente 1 (uma) linha em branco** antes do texto ou do próximo título.

2. **Subtítulos e Seções (H2 e H3):**
   - Utilize H2 (`##`) para definir as seções principais do documento (Visão Geral, Épico, etc.).
   - Utilize H3 (`###`) estritamente para segmentar cenários dentro da seção de Comportamentos Esperados.
   - **Regra de Espaçamento de Títulos:** Todo título H2 ou H3 deve ter **obrigatória e exatamente 1 (uma) linha em branco de distância** em relação ao final do seu conteúdo anterior e 1 (uma) linha em branco de distância antes do início do seu próprio texto/conteúdo.

3. **Listas (Ordenadas e Não-Ordenadas):**
   - As listas (com `-` ou numéricas `1.`) só são consideradas devidamente formatadas se houver **1 (uma) linha em branco antes do primeiro item** da lista e **1 (uma) linha em branco após o último item**.

## Padrão para Criação de Tabelas

*(Frequentemente usada em "Detalhamento de Campos e Elementos")*

A estruturação textual das tabelas é estrita e deve seguir o padrão clássico do Markdown (GitHub Flavored), respeitando alinhamentos visuais estáticos:

- Mantenha **1 (uma) linha em branco** de distância separando o texto anterior do topo da tabela, e **1 (uma) linha em branco** no final da tabela.
- Na construção das colunas, é **obrigatório "pular a linha do cabeçalho", isto é, inserir a linha separadora/delimitadora** entre o cabeçalho textual e as linhas do corpo da tabela (Exemplo: `| :--- | :--- | :--- | :--- |`).
- Utilize pipes (`|`) alinhados perfeitamente com os espaçamentos das strings sempre que possível, facilitando a leitura de quem lê o texto puro (raw).
- O cabeçalho da tabela deve estar em evidência na primeira linha de pipes (ex: `| Campo / Elemento | Tipo | Obrigatoriedade | Descrição / Comportamento esperado |`), em seguida a linha divisória e por fim o corpo. Se um campo do corpo for o destaque, envolva-o em negrito (ex: `**Botão: Sair / Logout**`).

## Padrão BD para Comportamento Esperado (Gherkin/BDD)

Dentro da seção `## COMPORTAMENTO ESPERADO`, cada caso de uso deve ser subdividido como um cenário enumerado contendo H3.
O corpo do cenário deve apresentar as palavras-chave de ação explicitamente em negrito, mantendo-se na mesma estrutura:

- **Dado que** [condição de estado do sistema ou usuário]
- **Quando** [ação temporal ou gatilho for executada]
- **Então** [reação ou resultado explícito que o sistema deve apresentar]

## Estrutura de Seções Esperadas em Sequência

Você deve gerar as seções do documento mantendo a exata capitalização (todas em maiúsculas), ordem e contexto:

1. Primeira linha: `# RF_XXX - Nome da Funcionalidade`
2. `## VISÃO GERAL` (Propósito breve da funcionalidade).
3. `## ÉPICO` (No formato: Como usuário..., quero...).
4. `## HISTÓRIA DE USUÁRIO` (Formato expandido).
5. `## DETALHAMENTO DE CAMPOS E ELEMENTOS` (Tabela estruturada contendo as colunas e a linha separadora de cabeçalho).
6. `## PRÉ-REQUISITOS` (Lista com pré-condições exigidas).
7. `## DEPENDÊNCIAS` (Lista de relacionamento com outros módulos e fluxos).
8. `## FORA DE ESCOPO` (Lista demarcando pontos que não serão abordados aqui).
9. `## COMPORTAMENTO ESPERADO` (Subdividido em `### Cenário X...`, contendo **Dado que**, **Quando** e **Então**).

## Exemplo prático

Abaixo, segue um exemplo prático de aplicação dessas regras:

---

# RF_002 - Menu Principal do Aplicativo

## VISÃO GERAL

Esta funcionalidade descreve o Menu Principal do aplicativo, que atua como o ponto de partida na navegação para que os usuários possam acessar as principais áreas, recursos e ferramentas do sistema. O objetivo é garantir uma experiência de uso simples, fluida e intuitiva.

## ÉPICO

Como usuário do aplicativo, quero ter uma área de navegação central disponível para transitar facilmente pelas telas do sistema.

## HISTÓRIA DE USUÁRIO

Como usuário logado, quero acessar um menu principal com modos de jogo (Bandeiras, Mapas, Quiz, Customizada) e utilizar minha foto de perfil para abrir opções de estatísticas, progresso e configurações, para utilizar o ecossistema do app sem me perder na navegação.

## DETALHAMENTO DE CAMPOS E ELEMENTOS

Esta seção define as opções interativas, botões e informações que compõem o layout e os dados do Menu Principal.

| Campo / Elemento               | Tipo          | Obrigatoriedade | Descrição / Comportamento esperado                                                           |
| :----------------------------- | :------------ | :-------------- | :------------------------------------------------------------------------------------------- |
| **Foto do Perfil**             | Imagem        | Sim             | Exibe o avatar. Ao clicar, abre um menu flutuante (dropdown) contendo opções extras.         |
| **Dropdown: Estatísticas**     | Link          | Sim             | Localizado no dropdown, redireciona o usuário para o dashboard principal.                    |
| **Dropdown: Progresso**        | Link          | Sim             | Localizado no dropdown, encaminha para os relatórios de uso e conquistas do jogador.         |
| **Dropdown: Configurações**    | Link          | Sim             | Localizado no dropdown, abre a tela para ajustes gerais do App (tema, idiomas e afins).      |
| **Botão: Bandeiras**           | Botão / Link  | Sim             | Levará ao menu de opções de jogos focados no conhecimento de bandeiras.                      |
| **Botão: Mapas**               | Botão / Link  | Sim             | Levará ao menu de opções de jogos envolvendo desafios de conhecimento de mapas geográficos.  |
| **Botão: Quiz**                | Botão / Link  | Sim             | Levará ao menu com as opções de quizzes de perguntas e respostas.                            |
| **Botão: Customizada**         | Botão / Link  | Sim             | Levará ao menu de jogos customizados já salvos ou à opção de criar um novo modo de jogo.     |

## PRÉ-REQUISITOS

1. O usuário precisa estar devidamente autenticado.
2. A sessão deve estar válida e não pode ter expirado.

## DEPENDÊNCIAS

- Módulo e fluxo de Autenticação / Login.

## FORA DE ESCOPO

- Esta especificação não trata da parametrização fina (quem vê o que com qual permissão), ela considera por hora um perfil genérico acessando o App.
- Desenvolvimento das telas de destino de cada link (Isso será tratado em suas próprias RFs).

## COMPORTAMENTO ESPERADO

### Cenário 1: Acessando o Dropdown de Perfil

**Dado que** o usuário está na tela de Menu Principal,
**Quando** clicar na área interativa da "Foto do Perfil",
**Então** um menu flutuante (dropdown) será expandido exibindo os atalhos para as telas de "Estatísticas", "Progresso" e "Configurações".

### Cenário 2: Navegação para Modos de Jogo

**Dado que** o usuário está a visualizar o Menu Principal,
**Quando** clicar em um dos botões principais de jogo (Bandeiras, Mapas, Quiz ou Customizada),
**Então** o sistema fará a transição redirecionando o usuário para a respectiva tela de jogo.

### Cenário 3: Ausência de Dados da Foto de Perfil

**Dado que** o usuário que acessou o aplicativo não fez o upload de uma Foto de Perfil,
**Quando** a tela de Menu Principal for renderizada no dispositivo,
**Então** a área da foto deve usar um contorno padrão visualizando a inicial do nome do usuário no centro.
