# Brev.ly

Um aplicativo completo de encurtamento de URLs composto por:

- **Servidor** (`/server`): Fastify + Node.js + Prisma REST API
- **Web** (`/web`): SPA com React + Vite + TailwindCSS

## Funcionalidades

- Criação de slug personalizado com validação
- Redirecionamentos com contagem de acessos
- Listar, excluir e copiar links encurtados
- Exportação de todos os links em CSV para o Cloudflare R2
- Documentação OpenAPI interativa via Scalar UI

## Primeiros Passos

```bash
git clone https://github.com/grasielaGomes/brevly-app.git
cd brevly-app
```
