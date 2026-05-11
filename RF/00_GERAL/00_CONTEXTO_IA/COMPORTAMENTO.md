# Diretrizes de Comportamento - Geogok AI

> [!IMPORTANT]
> Estas instruções devem ser lidas e seguidas por toda instância de IA que atuar neste repositório.

## 1. Padrões de Edição de Documentação

- **Arquivos .md:** Sempre que for criar ou alterar um arquivo Markdown (especialmente Requisitos Funcionais - RFs), você **DEVE** seguir o padrão definido em: `.agents/rules/RF_builder.md`.
- **Carregamento sob demanda:** Não carregue o arquivo de regras `RF_builder.md` preventivamente. Faça a leitura apenas quando uma tarefa de edição/criação de Markdown for iniciada.

## 2. Reconhecimento de Terreno (Inicialização)

- No início de **toda nova conversa**, você deve executar um comando de listagem de diretórios (`list_dir` ou `ls`) para mapear a estrutura atual do projeto.
- Guarde em sua memória imediata a listagem simples de arquivos para evitar perguntar onde as coisas estão.

## 3. Manutenção do Estado (Checkpoint)

- **Obrigatoriedade:** Sempre que houver um avanço significativo, mudança de planos ou alteração na arquitetura, você deve lembrar o usuário de atualizar o arquivo: `RF/00_GERAL/00_CONTEXTO_IA/CHECKPOINT.md`.
- **Explicação:** Ao fazer o lembrete, explique brevemente que o `CHECKPOINT.md` é a "memória de transferência" entre sessões, garantindo que o progresso não seja perdido e que futuras IAs saibam exatamente onde o trabalho parou.

## 4. Estilo de Comunicação

- Seja conciso e técnico.
- Priorize a precisão sobre a polidez excessiva.
- Se uma instrução do usuário conflitar com estas diretrizes, aponte o conflito antes de agir.
