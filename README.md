# NLW Agents Server

API REST desenvolvida com Fastify, TypeScript e PostgreSQL para o projeto NLW Agents.

## 🛠️ Tecnologias

- **Runtime**: Node.js 18+ com TypeScript
- **Framework**: Fastify 5.4.0
- **Database**: PostgreSQL 17 com pgvector + Drizzle ORM
- **Validação**: Zod 3.25.76
- **Type Safety**: Fastify Type Provider Zod
- **AI Integration**: Google Generative AI (@google/genai)
- **File Upload**: Fastify Multipart
- **CORS**: Fastify CORS
- **Linting/Formatting**: Biome 2.0.6 + Ultracite 5.0.32
- **Containerização**: Docker Compose
- **Database Migrations**: Drizzle Kit

## 📁 Estrutura do Projeto

```
server/
├── docker/
│   └── setup.sql
├── src/
│   ├── db/
│   │   ├── connection.ts
│   │   ├── migrations/
│   │   │   ├── 0000_material_sasquatch.sql
│   │   │   ├── 0001_adorable_peter_quill.sql
│   │   │   ├── 0002_calm_madame_web.sql
│   │   │   └── meta/
│   │   ├── schema/
│   │   │   ├── index.ts
│   │   │   ├── audio-chunks.ts
│   │   │   ├── questions.ts
│   │   │   └── rooms.ts
│   │   └── seed.ts
│   ├── http/
│   │   ├── routes/
│   │   │   ├── create-question.ts
│   │   │   ├── create-room.ts
│   │   │   ├── get-room-questions.ts
│   │   │   ├── get-rooms.ts
│   │   │   └── upload-audio.ts
│   │   └── services/
│   │       └── gemini.ts
│   ├── env.ts
│   └── server.ts
├── biome.jsonc
├── drizzle.config.ts
├── docker-compose.yml
└── package.json
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
npm run db:migrate
```

6. **Execute o seed do banco de dados**

```bash
npm run db:seed
```

7. **Inicie o servidor**

```bash
# Desenvolvimento
npm run dev

# Produção
npm start
```

## 🔧 Scripts Disponíveis

- `npm run dev` - Inicia o servidor em modo desenvolvimento com hot reload
- `npm start` - Inicia o servidor em modo produção
- `npm run db:generate` - Gera novas migrações do banco de dados
- `npm run db:migrate` - Executa as migrações do banco de dados
- `npm run db:seed` - Executa o seed do banco de dados

## 📊 Banco de Dados

- **ORM**: Drizzle ORM 0.44.2
- **Dialect**: PostgreSQL 17 com pgvector
- **Migrations**: Automáticas via Drizzle Kit 0.31.4
- **Schema**: Definido em `src/db/schema/`
- **Vector Search**: Suporte a embeddings com pgvector

## 🔒 Variáveis de Ambiente

```env
PORT=3333
DATABASE_URL=postgresql://docker:docker@localhost:5432/agents
GOOGLE_GENERATIVE_AI_API_KEY=your_api_key_here
```

## 🏗️ Padrões de Projeto

- **Arquitetura**: REST API com Fastify
- **Validação**: Schema validation com Zod
- **Type Safety**: TypeScript com Fastify Type Provider Zod
- **Database**: Type-safe queries com Drizzle ORM
- **AI Integration**: Google Generative AI para processamento de áudio e texto
- **File Upload**: Suporte a upload de arquivos de áudio
- **Code Style**: Biome + Ultracite para linting e formatação

## 📡 Endpoints

### Rooms

- `POST /rooms` - Criar uma nova sala
- `GET /rooms` - Listar todas as salas

### Questions

- `POST /questions` - Criar uma nova pergunta
- `GET /rooms/:roomId/questions` - Listar perguntas de uma sala

### Audio

- `POST /audio/upload` - Upload de arquivo de áudio

## 🤖 Integração com IA

O projeto integra com Google Generative AI para:

- Processamento de áudio
- Geração de respostas baseadas em contexto
- Análise de conteúdo

## 🐳 Docker

O projeto inclui configuração Docker para PostgreSQL 17 com pgvector:

```bash
docker-compose up -d
```

Acesse o banco em: `postgresql://docker:docker@localhost:5432/agents`

## 📝 Desenvolvimento

### Estrutura de Rotas

As rotas seguem o padrão Fastify com validação Zod:

- Cada rota é um módulo separado em `src/http/routes/`
- Validação de entrada com schemas Zod
- Type safety com Fastify Type Provider Zod

### Serviços

Serviços externos ficam em `src/http/services/`:

- `gemini.ts` - Integração com Google Generative AI

### Banco de Dados

- Schemas definidos em `src/db/schema/`
- Migrações automáticas com Drizzle Kit
- Seed para dados iniciais
