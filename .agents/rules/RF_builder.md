---
trigger: manual
description: Instruções de formação e padronização visual e estrutural para a geração de arquivos Markdown (.md), focado na criação de Documentos de Requisitos Funcionais.
globs: ["**/RF*.md"]
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

# RF_001 - Autenticação e Entrada no Aplicativo (Login)

## VISÃO GERAL

Esta funcionalidade engloba as interfaces e regras de negócio para a identificação inicial do usuário no aplicativo. A estratégia do design preza por interfaces minimalistas e fluídas, impedindo a fricção e as barreira de entrada, garantindo que o usuário consiga interagir, se autenticar rapidamente ou até mesmo jogar de forma anônima com o mínimo de cliques.

## ÉPICO

Como usuário iniciante ou recorrente do aplicativo, quero ter diversas alternativas rápidas para me autenticar (ou acessar rapidamente e de forma isenta como visitante sem me cadastrar) para alcançar a tela de Menu Principal, consolidando os progressos das minhas contas no percurso.

## HISTÓRIA DE USUÁRIO

Como jogador do aplicativo, quero ser de preferência auto-autenticado pelo dispositivo via serviços de jogos, ou ter acessos rápidos via Google e E-mail, além de também ter a liberdade da opção para ignorar todos os cadastros e partir para a página principal. Quero que minhas escolhas de não-logar sejam armazenadas para agilizar todas as minhas próximas aberturas do aplicativo.

## DETALHAMENTO DE CAMPOS E ELEMENTOS

Tabela listando de forma minuciosa as ações presentes que constróem a tela de acesso.

| Campo / Elemento | Tipo | Descrição / Comportamento esperado |
| :--- | :--- | :--- |
| **Imagem de Fundo / Logo** | Imagem | Design estético central e minimalista apresentando a identidade que compõe o brand do app. |
| **Componente de Auth: Play Games** | Automação | Execução invisível. Caso ocorra em Androids logados, esta rotina é ativada por conta própria no *startup* da tela. |
| **Botão: Continuar com Google** | Botão | Aciona modal integrado do Google Account/OAuth na tela. |
| **Campo: Endereço de E-mail** | Input | Onde o usuário informa o e-mail durante opções explícitas manuais. |
| **Campo: Senha do E-mail** | Input | Onde descreve as senhas manuais. |
| **Botão: Entrar com E-mail e Senha** | Botão | Realiza a validação contra as credenciais e procede ao sucesso do pareamento de contas. |
| **Botão: Pular Login (Jogar agora)** | Botão / Link | Ação explícita de recusa ao login. Salva metadados localmente ativando a regra permanente *bypass* de RF_001. |
| **Link: Esqueci minha senha** | Link | Aciona recuperação assíncrona mandando links de substituição no e-mail do autor. |
| **Link: Cadastrar-se agora** | Link | Habilita os inputs para o registro limpo de uma nova credencial por E-Mail. |
| **Modal: Definir Nick Único** | Modal | Ativo obrigatoriamente logo após a validação que crie um registro 100% autêntico pela primeira vez (Novo Cadastro). |

## PRÉ-REQUISITOS

1. Conectividade com a internet deve estar atrelada e ativa caso o usuário opte expressamente pelas autenticações baseadas em nuvem (ou no uso do Google Play).
2. Para que o Login do *Google Play* se dispare em auto-run, o recurso equivalente do ecossistema do celular deve já estar conectado de segundo plano nas variáveis do smartphone correspondente.

## DEPENDÊNCIAS

- Todos os cenários (pular ou prosseguir) obrigatoriamente interagem fazendo navegações (push) no diretório visual tratado pela **RF_002 (Menu Principal)**.
- Dependência contígua com SDKs do Google.

## FORA DE ESCOPO

- Integração, por ora, com outros players OAuth que fogem da restrição primária de Google (Ex. Twitch, GitHub, conta Apple), podendo vir em documentações evolutivas (v2).
- Construção fina de disparo/gateway e provedor SMTP que vai executar a remessa do link de Esqueci a Senha (Isso será de competência da infraestrutura/serviços de backend).

## COMPORTAMENTO ESPERADO

### Cenário 1: Entrada Automática com o Google Play Games (Zero Fricção)

**Dado que** o usuário instale o app e mantenha contas do Play Games ou serviço integrador local logada no próprio smartphone,
**Quando** o app for inicializado mostrando o esqueleto construtivo da tela principal de login por poucos milissegundos,
**Então** o sistema conectará proativamente essas credenciais e jogará o usuário automaticamente dentro do **RF_002 (Menu Principal)**.

### Cenário 2: Escolha de Bypass Definitivo ("Pular Login")

**Dado que** o acesso falhe na recuperação pelo Google Play ou o usuário venha num ecossistema limpo sem auto-login,
**Quando** o usuário clicar no elemento tátil de "Pular Login",
**Então** o sistema irá gravar localmente (cookies ou storage) essa escolha explícita do "Visitante" e enviará para a **RF_002**, e em subsequentes reaberturas do App este armazenamento indicará para ignorar integralmente a RF_001 futuramente sem atritos de paradas.

### Cenário 3: Cadastrando Credenciais e Nome Único Inédito

**Dado que** o usuário passe um registro manual pelo Google Auth Padrão ou pelo cadastro direto de "E-Mail e Senha" e isto se torne um sucesso real validado,
**Quando** não tiver nenhum apelido na respectiva tabela do banco de usuários atrelado ao *token* retornado,
**Então** a aplicação exibirá interativamente um elemento minimalista pedindo um "Nome de Usuário Único" limitador em relação ao banco, obrigando a resposta correta para depois encaminhá-lo para a **RF_002**.

### Cenário 4: Requisição de Recuperação de Senha

**Dado que** o usuário possua login com contas manuais baseado em inputs diretos e deseje utilizar isso,
**Quando** clicar na propriedade de "Esqueci minha senha" ativando interações,
**Então** o sistema disponibiliza o disparo de links para a sua caixa de entrada validando a alteração futura de senhas por aquele meio.
