# RF_005 - Menu de Seleção de Quizzes

## VISÃO GERAL

Esta funcionalidade descreve o Menu de Seleção de Quizzes, que é acessado a partir do Menu Principal. Esta tela organiza os diferentes desafios de perguntas e respostas sobre conhecimentos geográficos gerais, permitindo ao usuário escolher entre regiões geográficas específicas ou listas de temas globais.

## ÉPICO

Como usuário do aplicativo, quero navegar por categorias específicas de quizzes para testar meus conhecimentos teóricos sobre geografia em regiões de meu interesse.

## HISTÓRIA DE USUÁRIO

Como jogador recorrente, quero acessar uma tela dedicada ao modo de Quizzes que mantenha meu acesso ao perfil e forneça filtros por continentes e temas mundiais, para que eu possa selecionar e iniciar um teste de conhecimento de forma intuitiva.

## DETALHAMENTO DE CAMPOS E ELEMENTOS

Esta seção define as opções interativas e botões que compõem o layout do Menu de Seleção de Quizzes.

| Campo / Elemento | Tipo | Descrição / Comportamento esperado |
| :--- | :--- | :--- |
| **Foto do Perfil** | Imagem | Exibe o avatar. Ao clicar, abre o menu flutuante (dropdown) herdado do Menu Principal. |
| **Dropdown: Estatísticas** | Link | Localizado no dropdown de perfil. |
| **Dropdown: Progresso** | Link | Localizado no dropdown de perfil. |
| **Dropdown: Configurações** | Link | Localizado no dropdown de perfil. |
| **Botão: Favoritos** | Botão / Link | Leva ao submenu de quizzes marcados como favoritos pelo usuário. |
| **Botão: Mundo** | Botão / Link | Leva ao submenu de quizzes gerais envolvendo todos os continentes e países. |
| **Botão: América do Norte** | Botão / Link | Leva ao submenu de quizzes focados em países da América do Norte. |
| **Botão: América do Sul** | Botão / Link | Leva ao submenu de quizzes focados em países da América do Sul. |
| **Botão: África** | Botão / Link | Leva ao submenu de quizzes focados em países do continente africano. |
| **Botão: Europa** | Botão / Link | Leva ao submenu de quizzes focados em países do continente europeu. |
| **Botão: Ásia** | Botão / Link | Leva ao submenu de quizzes focados em países do continente asiático. |
| **Botão: Oceania** | Botão / Link | Leva ao submenu de quizzes focados em países do continente da Oceania. |
| **Botão: Ilhas** | Botão / Link | Leva ao submenu de quizzes focados em territórios insulares e ilhas independentes. |

## PRÉ-REQUISITOS

1. O usuário deve ter acessado o sistema e passado pelo Menu Principal (RF_002).
2. A sessão deve estar ativa.

## DEPENDÊNCIAS

- RF_002 - Menu Principal do Aplicativo (para acesso a esta tela).

## FORA DE ESCOPO

- Detalhamento dos submenus específicos de cada categoria de quiz.
- Lógica de correção das respostas ou pontuação final do quiz.

## COMPORTAMENTO ESPERADO

### Cenário 1: Navegação para Categorias de Quiz

**Dado que** o usuário está na tela de Menu de Seleção de Quizzes,
**Quando** clicar em qualquer um dos botões de categoria (ex: "África" ou "Mundo"),
**Então** o sistema deve realizar a transição para o submenu correspondente à categoria de quiz selecionada.

### Cenário 2: Acesso ao Dropdown de Perfil

**Dado que** o usuário está no Menu de Seleção de Quizzes,
**Quando** clicar na "Foto do Perfil",
**Then** o menu flutuante com as opções de "Estatísticas", "Progresso" e "Configurações" deve ser exibido, mantendo a consistência com o Menu Principal.

### Cenário 3: Retorno ao Menu Principal

**Dado que** o usuário deseja sair do menu de quizzes,
**Quando** acionar o comando de "Voltar" do dispositivo ou interface,
**Então** o sistema deve retornar o usuário para a tela do Menu Principal (RF_002).
