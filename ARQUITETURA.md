# Documentação e Pilares do Projeto Geogok

Este documento guarda as definições de arquitetura, stack tecnológica e guias práticos do projeto Geogok.

## Stack Tecnológica Escolhida

- **Frontend / Mobile:** React Native
- **Backend:** NestJS (Framework Node.js com arquitetura baseada em módulos e injeção de dependência)
- **Banco de Dados:** PostgreSQL com a extensão **PostGIS** (Ideal para um app de Geografia, pois permite armazenar e realizar consultas complexas envolvendo coordenadas, polígonos, fronteiras e distâncias).
- **Infraestrutura Local:** Docker e Docker Compose (para orquestrar o banco de dados e possivelmente a API em ambiente de desenvolvimento).

## 📂 Estrutura de Pastas (Monorepo Simples)

Como teremos um aplicativo e uma API, a melhor abordagem de organização é manter ambos no mesmo repositório, separados por pastas. Isso facilita o controle de versão e a configuração do Docker Compose na raiz.

```text
Geogok/
│
├── backend/                  # Código-fonte da API em NestJS
│   ├── src/                  
│   ├── Dockerfile            # Imagem Docker para a API Node.js/Nest
│   └── package.json          
│
├── mobile/                   # Código-fonte do app em React Native
│   ├── src/                  
│   ├── app.json              
│   └── package.json          
│
├── docker-compose.yml        # Orquestrador local (irá subir o PostGIS e a API)
├── ARQUITETURA.md            # Este arquivo
├── README.md                 # Visão geral do projeto
└── .gitignore                # Ignora pastas como node_modules, build, etc.
```

## Docker - Plano de Ação

Como você já sabe o básico, vamos facilitar:

1. Utilizaremos uma imagem oficial do PostgreSQL que já vem com o PostGIS instalado (ex: `postgis/postgis`).
2. O `docker-compose.yml` raiz vai facilitar para que com um comando (`docker compose up -d`) você tenha o banco rodando, pronto para receber conexões das migrations do NestJS.
3. Não há necessidade de colocar o React Native em containers, o desenvolvimento mobile costuma ocorrer nativamente na máquina (com emuladores ou celular físico).
