# Brev.ly – Web

Esta é a **SPA frontend** para o encurtador de URLs Brev.ly, construída com React, Vite e TailwindCSS.

## Índice

- [Visão Geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Requisitos](#requisitos)
- [Instalação](#instalação)
- [Configuração](#configuração)
- [Scripts](#scripts)

---

## Visão Geral

O aplicativo Brev.ly Web oferece:

- Um formulário para criar novos links curtos
- Lista em tempo real, exclusão e cópia de slugs
- Exportação CSV de todos os links
- Tela de redirecionamento dinâmica para slugs
- Layout responsivo, mobile-first, combinando com o mockup do Figma

---

## Funcionalidades

- **Criação de Links** com validação Zod
- **Listagem & Exclusão** de links
- **Copiar para a Área de Transferência** para URLs curtas
- **Exportação CSV** em uma nova aba
- **Página de Redirecionamento** em `/:shortUrl`
- **Tratamento de Erros** e estados de carregamento
- **Componentes Reutilizáveis** (Button, Input, Card, Header, etc.)

---

## Requisitos

- **Node.js** ≥ 18
- **pnpm** ≥ 6
- **Vite** ≥ 4
- **React** ≥ 19
- **TailwindCSS** ≥ 4

---

## Instalação

```bash
git clone https://github.com/grasielaGomes/brevly-app.git
cd brevly-app/web
pnpm install
```

## Configuração

Crie um .env em web/:

```bash
VITE_API_URL=http://localhost:3333
```

## Scripts

```bash
Dev: pnpm dev
Build: pnpm build
```
