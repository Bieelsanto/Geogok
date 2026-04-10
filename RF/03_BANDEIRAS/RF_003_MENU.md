# RF_003 - Menu de Seleção de Bandeiras

## VISÃO GERAL

Esta funcionalidade descreve o Menu de Seleção de Bandeiras, que é acessado a partir do Menu Principal. Esta tela organiza os diferentes modos e categorias de desafios relacionados a bandeiras, permitindo ao usuário escolher entre regiões geográficas específicas ou listas personalizadas.

## ÉPICO

Como usuário do aplicativo, quero navegar por categorias específicas de bandeiras para focar meu estudo ou jogo em regiões de meu interesse.

## HISTÓRIA DE USUÁRIO

Como usuário interessado em geografia, quero acessar uma tela dedicada ao modo de Bandeiras que mantenha meu acesso ao perfil e ofereça opções claras de categorias (Continentes, Favoritos, Mundo), para que eu possa iniciar uma atividade de forma rápida e organizada.

## DETALHAMENTO DE CAMPOS E ELEMENTOS

Esta seção define as opções interativas e elementos que compõem o layout do Menu de Seleção de Bandeiras.

| Campo / Elemento | Tipo | Descrição / Comportamento esperado |
| :--- | :--- | :--- |
| **Foto do Perfil** | Imagem | Exibe o avatar. Ao clicar, abre o menu flutuante (dropdown) herdado do Menu Principal. |
| **Dropdown: Estatísticas** | Link | Localizado no dropdown de perfil. |
| **Dropdown: Progresso** | Link | Localizado no dropdown de perfil. |
| **Dropdown: Configurações** | Link | Localizado no dropdown de perfil. |
| **Label: Favoritos** | Label Expansível | Ao clicar, expande-se para listar os itens favoritos. Cada item possui um **botão de exclusão** no lado esquerdo. O nome segue o padrão "Região - Modo" (se houver modo) ou apenas "Região". |
| **Labels de Continente/Região** | Label Expansível | Itens: Mundo, América do Norte, América do Sul, África, Europa, Ásia, Oceania. Ao clicar, expandem-se para exibir botões de sub-região. |
| **Label: Ilhas** | Label Expansível | Ao clicar, expande-se exibindo especificamente apenas o botão "Tudo". |
| **Botões de Sub-região** | Botão | Localizados dentro das labels expansíveis. Itens previstos: Norte, Sul, Leste, Oeste, Centro e Tudo. Redirecionam para a **RF_003.1 (Escolha de Bandeiras)**. |

> [!NOTE]
> **Arquitetura de Dados:** O conteúdo interno das labels (sub-labels ou botões) deve ser estruturado de forma desacoplada no código, permitindo a adição ou remoção de sub-itens via configuração/data-provider sem necessidade de refatoração da UI.

## PRÉ-REQUISITOS

1. O usuário deve ter acessado o sistema e passado pelo Menu Principal (RF_002).
2. A sessão deve estar ativa.

## DEPENDÊNCIAS

- RF_002 - Menu Principal do Aplicativo (para acesso a esta tela).

## FORA DE ESCOPO

- Detalhamento fino da interface de expansão (animações de sanfona ou dropdown).
- Lógica de geração de quizzes específicos de sub-regiões (tratado na RF_003.1).

## COMPORTAMENTO ESPERADO

### Cenário 1: Expansão de Região e Seleção de Sub-item

**Dado que** o usuário está na tela de Menu de Seleção de Bandeiras,
**Quando** clicar em uma label de região (ex: "América do Sul"),
**Então** a label deve expandir exibindo os botões de sub-região (Norte, Sul, Tudo, etc.).
**E quando** o usuário clicar em um desses botões,
**Então** o sistema deve realizar a transição para a **RF_003.1 (Escolha de Bandeiras)** carregando o escopo selecionado.

### Cenário 2: Acesso ao Dropdown de Perfil

**Dado que** o usuário está no Menu de Seleção de Bandeiras,
**Quando** clicar na "Foto do Perfil",
**Então** o menu flutuante com as opções de "Estatísticas", "Progresso" e "Configurações" deve ser exibido, mantendo a consistência com o Menu Principal.

### Cenário 3: Retorno ao Menu Principal

**Dado que** o usuário deseja sair do menu de bandeiras,
**Quando** acionar o comando de "Voltar" do dispositivo ou interface,
**Então** o sistema deve retornar o usuário para a tela do Menu Principal (RF_002).

### Cenário 4: Clique em Favorito (Com Modo Definido)

**Dado que** o usuário possui um item favorito com modo configurado (ex: "Europa - Nome/Bandeira"),
**Quando** clicar no nome do item na lista de favoritos,
**Então** o sistema deve ignorar a RF_003.1 e iniciar imediatamente a partida na **RF_003.2**.

### Cenário 5: Clique em Favorito (Sem Modo Definido)

**Dado que** o usuário favoritou apenas a região (ex: "América do Sul"),
**Quando** clicar no nome do item na lista de favoritos,
**Então** o sistema deve abrir o popup da **RF_003.1** para que o usuário escolha o modo antes de jogar.

### Cenário 6: Exclusão de Favorito

**Dado que** o usuário possui itens na lista de favoritos,
**Quando** clicar no ícone de exclusão (lado esquerdo do item),
**Então** o sistema deve remover o item da lista de persistência e atualizar a interface imediatamente.
