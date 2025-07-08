# NLW Agents Server

API REST desenvolvida com Fastify, TypeScript e PostgreSQL para o projeto NLW Agents.

## 🛠️ Tecnologias

- **Runtime**: Node.js com TypeScript
- **Framework**: Fastify
- **Database**: PostgreSQL com Drizzle ORM
- **Validação**: Zod
- **Linting/Formatting**: Biome + Ultracite
- **Containerização**: Docker Compose

## 📁 Estrutura do Projeto

```
src/
├── db/
│   ├── connection.ts
│   ├── migrations/
│   ├── schema/
│   └── seed.ts
├── http/
│   └── routes/
├── env.ts
└── server.ts
```

## 🚀 Setup

### Pré-requisitos

- Node.js 18+
- Docker e Docker Compose

### Instalação

1. **Clone o repositório**

```bash
git clone <repository-url>
cd server
```

2. **Instale as dependências**

```bash
npm install
```

3. **Configure as variáveis de ambiente**

```bash
cp .env.example .env
```

4. **Inicie o banco de dados**

```bash
docker-compose up -d
```

5. **Execute as migrações**

```bash
npm run db:seed
```

6. **Inicie o servidor**

```bash
# Desenvolvimento
npm run dev

# Produção
npm start
```

## 🔧 Scripts Disponíveis

- `npm run dev` - Inicia o servidor em modo desenvolvimento com hot reload
- `npm start` - Inicia o servidor em modo produção
- `npm run db:seed` - Executa o seed do banco de dados

## 📊 Banco de Dados

- **ORM**: Drizzle ORM
- **Dialect**: PostgreSQL
- **Migrations**: Automáticas via Drizzle Kit
- **Schema**: Definido em `src/db/schema/`

## 🔒 Variáveis de Ambiente

```env
PORT=3333
DATABASE_URL=postgresql://docker:docker@localhost:5432/agents
```

## 🏗️ Padrões de Projeto

- **Arquitetura**: REST API com Fastify
- **Validação**: Schema validation com Zod
- **Type Safety**: TypeScript com type providers
- **Database**: Type-safe queries com Drizzle ORM
- **Code Style**: Biome + Ultracite para linting e formatação

## 📡 Endpoints

- `GET /health` - Health check
- `GET /rooms` - Lista todas as salas

## 🐳 Docker

O projeto inclui configuração Docker para PostgreSQL com pgvector:

```bash
docker-compose up -d
```

Acesse o banco em: `postgresql://docker:docker@localhost:5432/agents`
