# Implementação Geral e Arquitetura - Geogok

Este documento define a estratégia técnica, a stack tecnológica e a arquitetura de dados do projeto Geogok.

## 1. Stack Tecnológica

- **Frontend / Mobile:** React Native (Interface e lógica de jogo).
- **Backend:** NestJS (Node.js) para orquestração, autenticação e processamento geográfico.
- **Banco de Dados Central:** PostgreSQL + extensão **PostGIS** (Armazenamento de vetores e relações espaciais).
- **Banco de Dados Local (Mobile):** SQLite (via WatermelonDB ou similar) para persistência offline.
- **Infraestrutura de Dev:** Docker e Docker Compose (PostgreSQL/PostGIS + API).

## 2. Pré-requisitos e Dependências

- **Infraestrutura:** Docker configurado para rodar o banco geoespacial.
- **Dados:** Ingestão de datasets mundiais (ex: Natural Earth ou OpenStreetMap) via scripts de seed no backend.
- **Mobile:** SQLite local com suporte ao módulo R-Tree habilitado para buscas espaciais.
- **Conectividade:** Necessária apenas para o primeiro "Sync" e atualizações de ranking/progresso.

## 3. Estrutura do Projeto (Monorepo)

```text
Geogok/
├── backend/                  # API NestJS
│   ├── src/                  
│   └── Dockerfile            
├── mobile/                   # App React Native
│   ├── src/                  
│   └── package.json          
├── docker-compose.yml        # Orquestração do ambiente local
└── README.md                 
```

## 3. Arquitetura de Geodados

### 3.1. Processamento no Backend

Para garantir performance no mobile, os dados geográficos brutos (Natural Earth/OSM) são processados antes do envio:

- **Simplificação:** Uso de `ST_SimplifyPreserveTopology` para reduzir o número de vértices dos polígonos.
- **Compressão:** Dados transmitidos via GeoJSON com compressão Gzip/Brotli.
- **Paginação Espacial:** Suporte a consultas por BBOX (`Bounding Box`).

### 3.2. Armazenamento e Busca no Mobile

- **Schema Local:** Tabelas separadas para metadados (`Countries`) e geometria pesada (`Geometries`).
- **Busca Espacial:** Uso do módulo **R-Tree** do SQLite para detecção instantânea de polígonos ao clicar no mapa.

## 4. Fluxo de Dados e Sincronização

1. **Bootstrap (Seed):** No primeiro acesso, o mobile baixa um pacote SQLite pré-processado ou via API para popular o banco local.
2. **Operação Offline:** Todas as escritas de progresso são feitas no banco local com timestamps de versão.
3. **Sincronização (Push):** Quando online, o mobile envia os registros pendentes para o backend NestJS, que resolve conflitos baseados no histórico de versões.

## 5. Diretrizes de Desenvolvimento

- **TDD (Test Driven Development):** Obrigatório para lógica de jogo e processamento de dados.
- **Intercâmbio de Dados:** O formato padrão para dados geoespaciais é o **GeoJSON**.
- **Performance de UI:** Uso de `react-native-fast-image` para bandeiras e otimização de renderização de SVGs.

## 6. Riscos e Desafios Técnicos

- **Peso dos Dados Geográficos:** Polígonos complexos podem travar o mobile. *Solução:* Simplificação agressiva no backend (`ST_Simplify`).
- **Consistência Offline:** Conflitos de sincronização. *Solução:* Versionamento por timestamp em cada registro.
- **Renderização de Bandeiras:** Centenas de SVGs em listas. *Solução:* Cache e componentes de alto desempenho.
