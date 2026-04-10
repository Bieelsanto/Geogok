# RF_004 - Menu de Seleção de Mapas

## VISÃO GERAL

Esta funcionalidade descreve o Menu de Seleção de Mapas, acessado a partir do Menu Principal. Esta tela organiza os diferentes modos e categorias de desafios de identificação e conhecimento de mapas geográficos, permitindo ao usuário escolher entre regiões globais ou listas personalizadas.

## ÉPICO

Como usuário do aplicativo, quero navegar por categorias específicas de mapas para testar meu conhecimento geográfico em regiões selecionadas.

## HISTÓRIA DE USUÁRIO

Como usuário interessado em cartografia e geografia, quero acessar uma tela dedicada ao modo de Mapas que mantenha meu acesso ao perfil e forneça botões para diferentes regiões do globo, para visualizar e iniciar desafios de mapas de forma intuitiva.

## DETALHAMENTO DE CAMPOS E ELEMENTOS

Esta seção define as opções interativas e elementos que compõem o layout do Menu de Seleção de Mapas.

| Campo / Elemento | Tipo | Descrição / Comportamento esperado |
| :--- | :--- | :--- |
| **Foto do Perfil** | Imagem | Exibe o avatar. Ao clicar, abre o menu flutuante (dropdown) herdado do Menu Principal. |
| **Dropdown: Estatísticas** | Link | Localizado no dropdown de perfil. |
| **Dropdown: Progresso** | Link | Localizado no dropdown de perfil. |
| **Dropdown: Configurações** | Link | Localizado no dropdown de perfil. |
| **Label: Favoritos** | Label Expansível | Ao clicar, expande-se para exibir atalhos de sub-regiões ou filtros marcados como favoritos pelo usuário. |
| **Labels de Continente/Região** | Label Expansível | Itens: Mundo, América do Norte, América do Sul, África, Europa, Ásia, Oceania. Ao clicar, expandem-se para exibir botões de sub-região. |
| **Label: Ilhas** | Label Expansível | Ao clicar, expande-se exibindo especificamente apenas o botão "Todos". |
| **Botões de Sub-região** | Botão | Localizados dentro das labels expansíveis. Itens previstos: Norte, Sul, Leste, Oeste, Centro e Todos. Redirecionam para a **RF_008 (Escolha de Mapas)**. |

> [!NOTE]
> **Arquitetura de Dados:** O conteúdo interno das labels (sub-labels ou botões) deve ser estruturado de forma desacoplada no código, permitindo a adição ou remoção de sub-itens via configuração/data-provider sem necessidade de refatoração da UI.

## PRÉ-REQUISITOS

1. O usuário deve ter acessado o sistema e passado pelo Menu Principal (RF_002).
2. A sessão deve estar ativa.

## DEPENDÊNCIAS

- RF_002 - Menu Principal do Aplicativo (para acesso a esta tela).

## FORA DE ESCOPO

- Detalhamento dos submenus específicos de cada categoria de mapa.
- Lógica de interação com os mapas (zoom, pan, cliques em regiões).

## COMPORTAMENTO ESPERADO

### Cenário 1: Expansão de Região e Seleção de Sub-item

**Dado que** o usuário está na tela de Menu de Seleção de Mapas,
**Quando** clicar em uma label de região (ex: "Ásia"),
**Então** a label deve expandir exibindo os botões de sub-região (Norte, Sul, Todos, etc.).
**E quando** o usuário clicar em um desses botões,
**Então** o sistema deve realizar a transição para a **RF_007 (Escolha de Bandeiras)** carregando o escopo selecionado.

### Cenário 2: Acesso ao Dropdown de Perfil

**Dado que** o usuário está no Menu de Seleção de Mapas,
**Quando** clicar na "Foto do Perfil",
**Então** o menu flutuante com as opções de "Estatísticas", "Progresso" e "Configurações" deve ser exibido, mantendo a consistência com o Menu Principal.

### Cenário 3: Retorno ao Menu Principal

**Dado que** o usuário deseja sair do menu de mapas,
**Quando** acionar o comando de "Voltar" do dispositivo ou interface,
**Então** o sistema deve retornar o usuário para a tela do Menu Principal (RF_002).
