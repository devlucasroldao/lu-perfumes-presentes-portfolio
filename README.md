# 🌸 Lu Perfumes & Presentes

> E-commerce completo de perfumes, cosméticos e kits presenteáveis — desenvolvido para uma cliente real em Arroio do Sal, RS.

[![Site ao vivo](https://img.shields.io/badge/Site%20ao%20vivo-lu--perfumes--v2.vercel.app-6B3A3A?style=for-the-badge&logo=vercel&logoColor=white)](https://lu-perfumes-v2.vercel.app)
[![Next.js](https://img.shields.io/badge/Next.js%2014-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)](https://nextjs.org)
[![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com)
[![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://vercel.com)

> ⚠️ **Repositório de portfólio** — o código-fonte completo é privado.
> Screenshots, funcionalidades e arquitetura estão documentados abaixo.

---

## 📖 Sobre o Projeto

Este é um projeto **pessoal, real e de portfólio** que nasceu de uma necessidade genuína: minha mãe, Lu, revende perfumes e cosméticos há anos em Arroio do Sal — tudo no papel, sem organização, sem catálogo digital.

Decidi resolver isso de verdade. Não um projeto fictício para o portfólio. Um produto real, com cliente real, com problema real.

O resultado é um **mini e-commerce completo** com catálogo, kits personalizados, integração com WhatsApp, sistema de favoritos, histórico de pedidos e painel administrativo — tudo construído do zero com tecnologias modernas.

---

## 🖼️ Screenshots

> *Prints e GIFs serão adicionados em breve.*

<!-- Adicionar prints aqui:
![Home](./screenshots/home.png)
![Catálogo](./screenshots/catalogo.png)
![Produto](./screenshots/produto.png)
![Mobile](./screenshots/mobile.png)
![Admin](./screenshots/admin.png)
-->

---

## ✨ Funcionalidades

### Para a cliente (usuária final)
- 🏠 **Home** com carrossel de banners, categorias visuais, destaques e seção de kits
- 📦 **Catálogo completo** com filtros por categoria, linha, marca, tipo e busca em tempo real
- 🛍️ **Sacola** com envio automático formatado para o WhatsApp
- 🎁 **Kits personalizados** — kits prontos ou monte o seu com busca e filtro
- ❤️ **Favoritos** com login obrigatório e persistência no banco de dados
- 👤 **Autenticação** completa via Supabase Auth (cadastro, login, perfil com nome)
- 📋 **Histórico de pedidos** — pedidos enviados pelo WhatsApp salvos automaticamente
- 🔍 **Sistema de recomendações** — "Combina com esse produto" baseado em categoria, linha e marca
- 💫 **Splash Screen** animada com logo e identidade visual da marca
- 📱 **Mobile-first** — experiência otimizada para celular com bottom navigation estilo app

### Para a administradora (Lu)
- 🔐 **Painel admin** protegido por senha
- ✏️ **CRUD completo** de produtos com upload de fotos via Supabase Storage
- 🎛️ **Gestão de kits** — criar kits prontos com associação de produtos
- 🖼️ **Central de imagens** — trocar banners, logo e imagens institucionais sem abrir o código
- 📊 **Central de Catálogo** — visão Airtable/Notion de todos os produtos com edição inline
- 📥 **Importação de catálogo** — importar produtos via CSV ou lista de texto com classificação por IA
- 🎨 **Sistema de temas sazonais** — Natal, Dia das Mães, Namorados — ativar com um clique
- 💬 **Central WhatsApp** — cadastro de contatos e mensagens prontas para campanhas
- ⭐ **Depoimentos** — gerenciar avaliações exibidas no site

---

## 🛠️ Stack Tecnológica

| Camada | Tecnologia | Decisão |
|---|---|---|
| **Frontend** | Next.js 14 (Pages Router) | SSR nativo, deploy simples, ecossistema maduro |
| **Linguagem** | JavaScript puro | Sem overhead de TypeScript para projeto de escala atual |
| **Estilo** | CSS-in-JS (objetos inline) | Colocação garantida, sem conflitos de classe |
| **Banco de dados** | Supabase (PostgreSQL) | BaaS completo: auth, storage e DB em um só lugar |
| **Autenticação** | Supabase Auth | Integração nativa com o banco, sem configuração extra |
| **Storage** | Supabase Storage | Upload de imagens direto no ecossistema já usado |
| **Deploy** | Vercel | CI/CD automático via push no GitHub |
| **Análise** | Google Analytics | Monitoramento de tráfego e comportamento |

---

## 🏗️ Arquitetura

```
lu-perfumes-presentes/
├── pages/
│   ├── index.js          # Home com carrossel, categorias e destaques
│   ├── catalogo.js       # Catálogo com sidebar de filtros
│   ├── produto/[id].js   # Página de produto com recomendações
│   ├── kits.js           # Kits prontos + monte o seu
│   ├── sacola.js         # Sacola com integração WhatsApp
│   ├── favoritos.js      # Favoritos + histórico de pedidos
│   ├── sobre.js          # Página institucional
│   └── admin/
│       ├── index.js      # CRUD de produtos
│       ├── catalogo.js   # Central de catálogo (visão Airtable)
│       ├── importar.js   # Importação CSV + IA
│       ├── imagens.js    # Central de imagens
│       ├── temas.js      # Sistema de temas sazonais
│       ├── depoimentos.js
│       └── whatsapp.js   # Central de contatos e campanhas
├── components/
│   ├── Layout.js
│   ├── Navbar.js
│   ├── BottomNav.js      # Navegação mobile estilo app
│   ├── SplashScreen.js   # Splash animado
│   ├── CardProduto.js
│   ├── RecomendacoesBloco.js
│   └── ...
├── context/
│   └── SacolaContext.js  # Estado global da sacola
├── lib/
│   ├── supabase.js       # Cliente Supabase
│   ├── catalogo.js       # Engine de queries do catálogo
│   ├── recomendacoes.js  # Engine de recomendações híbrida
│   └── importacao.js     # Parser CSV + detecção de duplicatas
└── public/
    └── images/           # Assets estáticos
```

---

## 🗄️ Banco de Dados (Supabase / PostgreSQL)

```sql
produtos            -- catálogo principal com variantes
kits                -- kits prontos
kit_produtos        -- relação N:N produtos↔kits
favoritos           -- lista de desejos por usuário
pedidos             -- histórico de pedidos via WhatsApp
profiles            -- perfil do usuário (nome)
produto_relacionados -- recomendações manuais
catalogo_externo    -- produtos das marcas ainda não publicados
configuracoes       -- banners, logo, imagens configuráveis
temas               -- temas sazonais (Natal, Dia das Mães...)
depoimentos         -- avaliações gerenciadas pelo admin
contatos            -- lista de contatos para campanhas WhatsApp
mensagens_prontas   -- templates de mensagem para campanhas
importacoes         -- histórico de importações do catálogo
```

---

## 🤖 IA como Ferramenta de Desenvolvimento

Este projeto foi desenvolvido com uso intencional e estratégico de IA — especificamente **Claude (Anthropic)** e **ChatGPT (OpenAI)** — não como substituto do raciocínio técnico, mas como **par de programação**.

### Como a IA foi usada na prática:

- **Geração de prompts técnicos** — traduzi decisões de design e produto em instruções precisas para implementação
- **Revisão de arquitetura** — discussões sobre modelagem do banco, estrutura de componentes e decisões de stack
- **Debugging colaborativo** — análise de erros e sugestão de correções
- **Documentação** — geração de READMEs, guias e documentação técnica
- **Planejamento de features** — roadmap de funcionalidades e priorização

### O que aprendi sobre usar IA:

> Saber usar IA é uma habilidade técnica real. A diferença entre um desenvolvedor que usa IA bem e um que usa mal está em saber **o que perguntar**, **como estruturar o contexto** e **como validar a resposta**.

Cada decisão técnica neste projeto foi tomada por mim. A IA acelerou a execução — eu conduzi o raciocínio.

---

## 🚀 Evolução do Projeto

| Versão | O que mudou |
|---|---|
| **v1** | Catálogo básico + filtros + sacola + WhatsApp |
| **v2** | Login, favoritos, kits, admin, upload de fotos |
| **v3** | Sistema de recomendações, histórico de pedidos, perfil com nome |
| **v4** | Central de catálogo (Airtable-style), importação com IA, temas sazonais |
| **v5** | Migração visual (Com Carinho, Lu), splash screen, bottom nav, paleta rosê |

> A versão anterior do projeto está arquivada em
> [lu-perfumes (v1)](https://github.com/devlucasroldao/lu-perfumes)
> — mostrando a evolução real do código ao longo do tempo.

---

## 📚 Contexto Acadêmico

Paralelamente ao desenvolvimento do site, este projeto foi utilizado como base para um trabalho acadêmico onde foi criado um **protótipo interativo no Figma Make** — uma versão mobile-first do catálogo com identidade visual refinada.

Os aprendizados do protótipo foram incorporados ao site real, resultando na migração visual da v5: nova paleta de cores, layout de cards, bottom navigation e experiência geral do app.

---

## 👨‍💻 Sobre o Desenvolvedor

**Lucas Roldão** — Estudante de Programação em busca de estágio ou primeira oportunidade como desenvolvedor júnior.

Este projeto representa minha capacidade de:
- Desenvolver produtos reais do zero para clientes reais
- Tomar decisões técnicas de arquitetura e banco de dados
- Trabalhar com stack moderna (Next.js, Supabase, Vercel)
- Usar IA de forma estratégica e produtiva
- Entregar valor real, não apenas código bonito

📧 Aberto a oportunidades — entre em contato!

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/devlucasroldao/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/devlucasroldao)

---

<div align="center">
  <p>Feito com 💜 e muito carinho por Lucas Roldão</p>
  <p><em>"Porque presentear é um ato de amor"</em></p>
</div>
