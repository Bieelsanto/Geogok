# RF_006 - Menu de Jogos Customizados

## VISÃO GERAL

Esta funcionalidade descreve o Menu de Jogos Customizados, que é acessado a partir do Menu Principal. Esta tela centraliza a criação e o gerenciamento de modos de jogo personalizados pelo usuário, além de permitir o acesso a conteúdos criados pela comunidade ou marcados como favoritos.

## ÉPICO

Como usuário do aplicativo, quero gerenciar e criar meus próprios modos de jogo para ter uma experiência de aprendizado personalizada e desafiadora.

## HISTÓRIA DE USUÁRIO

Como jogador avançado, quero acessar uma tela dedicada a Jogos Customizados que me permita criar novos desafios, visualizar meus jogos salvos e explorar criações da comunidade, mantendo a facilidade de navegação e acesso ao meu perfil.

## DETALHAMENTO DE CAMPOS E ELEMENTOS

Esta seção define as opções interativas e botões que compõem o layout do Menu de Jogos Customizados.

| Campo / Elemento | Tipo | Descrição / Comportamento esperado |
| :--- | :--- | :--- |
| **Foto do Perfil** | Imagem | Exibe o avatar. Ao clicar, abre o menu flutuante (dropdown) herdado do Menu Principal. |
| **Dropdown: Estatísticas** | Link | Localizado no dropdown de perfil. |
| **Dropdown: Progresso** | Link | Localizado no dropdown de perfil. |
| **Dropdown: Configurações** | Link | Localizado no dropdown de perfil. |
| **Botão: Criar Novo Jogo** | Botão | Redireciona para o fluxo/tela de criação de novos modos de jogo (configuração de regras). |
| **Botão: Meus Jogos** | Botão / Link | Leva à lista de jogos customizados criados e salvos pelo próprio usuário. |
| **Botão: Favoritos** | Botão / Link | Leva à lista de jogos customizados (próprios ou da comunidade) favoritados. |
| **Botão: Comunidade** | Botão / Link | Leva à área de exploração de jogos customizados compartilhados por outros usuários. |
| **Botão: Recentes** | Botão / Link | Atalho para os últimos modos de jogo customizados que foram jogados. |

## PRÉ-REQUISITOS

1. O usuário deve estar logado no sistema para salvar e visualizar jogos customizados.
2. A sessão deve estar ativa.

## DEPENDÊNCIAS

- RF_002 - Menu Principal do Aplicativo (para acesso a esta tela).

## FORA DE ESCOPO

- Detalhamento do fluxo de criação de regras de jogo (ferramenta de criação).
- Mecânica de compartilhamento público de jogos customizados.

## COMPORTAMENTO ESPERADO

### Cenário 1: Início da Criação de Novo Jogo

**Dado que** o usuário está na tela de Menu de Jogos Customizados,
**Quando** clicar no botão "Criar Novo Jogo",
**Então** o sistema deve encaminhar o usuário para a interface de configuração de novas regras de jogo.

### Cenário 2: Acesso aos Jogos Salvos

**Dado que** o usuário possui jogos customizados previamente salvos,
**Quando** clicar em "Meus Jogos",
**Então** o sistema deve exibir uma lista organizada das criações do usuário para seleção.

### Cenário 3: Navegação Consistente do Perfil

**Dado que** o usuário está navegando no menu customizado,
**Quando** clicar na área da "Foto do Perfil",
**Então** o menu dropdown expandido deve oferecer as mesmas opções de progresso e configurações vistas no Menu Principal.

### Cenário 4: Retorno ao Menu Principal

**Dado que** o usuário deseja sair da área customizada,
**Quando** acionar o comando de "Voltar",
**Então** o sistema deve redirecioná-lo para a tela do Menu Principal (RF_002).
