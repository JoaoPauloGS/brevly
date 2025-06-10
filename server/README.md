# Brev.ly - Servidor

Este é o repositório do **backend** (Servidor) do projeto Brev.ly, um aplicativo de encurtamento de URLs.
Fornece uma API RESTful para criar, listar, excluir, redirecionar URLs encurtadas e gerar relatórios CSV enviados para o Cloudflare R2.

## Índice

- [Visão Geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Requisitos](#requisitos)
- [Início Rápido](#início-rápido)
- [Configuração](#configuração)
- [Scripts](#scripts)
- [Docker](#docker)
- [Endpoints da API](#endpoints-da-api)

---

## Visão Geral

O Brev.ly Server gerencia:

- Criação, validação e verificação de duplicidade de URLs
- Exclusão de links e redirecionamento com incremento da contagem de acessos
- Listagem de todas as URLs armazenadas
- Geração de relatórios CSV e upload para o Cloudflare R2

Funciona perfeitamente com o frontend [Brev.ly Web](../web/README.md) para uma solução completa.

---

## Funcionalidades

- **Criar URL Encurtada**: Slugs personalizados, validação de formato, prevenção de duplicidade.
- **Excluir URL**: Remove links pelo slug.
- **Redirecionar**: Redirecionamento 302 para a URL original e rastreamento de acessos.
- **Listar URLs**: Recupera todos os links armazenados.
- **Exportar CSV**: Exportação em lote dos dados dos links para CSV, enviado ao R2.
- **Docs OpenAPI**: Documentação interativa em `/docs` via Scalar UI e openapi-zod.

---

## Requisitos

- Node.js v18+
- pnpm v7+
- PostgreSQL v14+
- Cloudflare R2 (ou compatível com S3) para armazenamento de CSV

---

## Início Rápido

1. **Clone** o repositório:
   ```bash
   git clone https://github.com/JoaoPauloGS/brevly.git
   cd server
   ```
2. **Configure** as variáveis de ambiente:
   ```bash
   cp .env.example .env
   # edite o .env com suas credenciais do BD e R2
   ```
3. **Desenvolvimento local**:
   ```bash
   pnpm install
   pnpm migrate
   pnpm dev
   ```
4. Acesse `http://localhost:3333/docs` para a documentação da API.

---

## Configuração

Variáveis de ambiente (veja `.env.example`):

```ini
DATABASE_URL=postgres://user:pass@db:5432/brevly
PORT=3333
CLOUDFLARE_ACCOUNT_ID=<seu-account-id>
CLOUDFLARE_ACCESS_KEY_ID=<key>
CLOUDFLARE_ACCESS_KEY_SECRET=<secret>
CLOUDFLARE_BUCKET=<nome-do-bucket>
PUBLIC_URL=https://<conta>.r2.cloudflarestorage.com
```

---

## Scripts

### Desenvolvimento Local

- **Instalar dependências**: `pnpm install`
- **Servidor de desenvolvimento**: `pnpm dev` (hot reload)
- **Gerar client**: `pnpm generate`
- **Migrar dev**: `pnpm migrate`
- **Rodar testes**: `pnpm test`

---

## Docker

Para rodar apenas o servidor:

```bash
docker build -t brevly-server .
docker run -p 3333:3333 --env-file .env brevly-server
```

---

### Docker Compose

```bash
# Build e inicia API + BD
docker compose up --build -d

# Ver logs
docker compose logs -f

# Parar e remover containers
docker compose down
```

Todas as etapas de build (instalação, geração do client, migrações) rodam automaticamente no CI ou Compose.

---

## Endpoints da API

| Método | Caminho             | Descrição                           |
| ------ | ------------------- | ----------------------------------- |
| POST   | `/links`            | Criar um novo link encurtado        |
| GET    | `/links`            | Listar todos os links               |
| GET    | `/links/:shortUrl`  | Redirecionar para a URL original    |
| DELETE | `/links/:shortUrl`  | Excluir um link pelo slug           |
| GET    | `/links/export`     | Exportar links em CSV (retorna URL) |

---
