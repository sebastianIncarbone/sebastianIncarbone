# Hi, I'm Sebastián Incarbone 👋

Senior full-stack developer — **Angular / .NET** — focused on **AI engineering** and **financial systems**. Based in Argentina.

I like problems where correctness is non-negotiable: market data, money math, and AI systems that keep the human in control.

![Angular](https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white)
![.NET](https://img.shields.io/badge/.NET%208-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

## Professional work

### Control Comercio — retail management SaaS

`Angular` `Ionic` `.NET 8` `Azure SQL` `SignalR`

Multi-tenant platform where **~4,000 active businesses** run their sales, stock, and electronic invoicing. One Angular + Ionic codebase ships to web, Android, and iOS, backed by a .NET 8 API with background jobs and real-time updates. The integrations are where the real complexity lives: AFIP e-invoicing, MercadoPago QR payments, MercadoLibre / TiendaNube sync, and AI-assisted purchase-invoice ingestion.

### Gestión Cervecera — ERP for breweries and beverage distributors

`.NET 8` `SQL Server` `Vue + Ionic`

Commercial ERP covering production, stock, keg and tap tracking, and deliveries with signature-based proof of delivery — for businesses operating in **nine countries**. The hard part: one multi-tenant system honoring each country's fiscal rules (AFIP in Argentina, electronic dispatch guides in Chile, Facturapi in Mexico), plus e-commerce sync with Shopify and WooCommerce.

## Side projects

### Mercurio — market terminal for Argentine fixed income

`Angular` `.NET 8` `Clean Architecture`

Read-only market terminal built on a layered .NET 8 backend and a standalone-components Angular frontend. The interesting problem: **reconciling LECAP positions** — capitalization bills accrue daily, so a position's value is something you compute and verify, not a number you store.

### FinancialLurch — personal financial intelligence cockpit

`Python` `CI + coverage` `Read-only broker`

Portfolio analysis, decision simulation, and recommendations — with the broker integration read-only **by design**: the system analyzes and proposes, the human decides. Typed Python, CI with enforced coverage, built spec-first with TDD.

### oGoat — local-first voice study assistant

`Python` `FastAPI` `React` `Ollama` `Whisper`

Voice in, voice out: questions are transcribed (faster-whisper), answered by a local LLM (Ollama), and spoken back (Piper TTS), with vector search over past sessions (ChromaDB). Runs entirely on-device — no data leaves the machine — and degrades gracefully when an ML service is unavailable.

### PetCloud — desktop ERP for a real pet shop

`Electron` `React` `TypeScript` `Supabase`

Internal desktop app running a real business day to day: products, suppliers, purchases, sales, and reports, backed by Postgres with row-level security. Software with actual users — the kind that call when something breaks.

> These repositories are currently private — happy to walk through any of them.

## Currently

Building agentic developer workflows: spec-driven development and multi-agent adversarial code review.

## GitHub activity

<picture>
  <img src="https://github-readme-stats.vercel.app/api?username=sebastianIncarbone&show_icons=true&theme=tokyonight&hide_border=true&count_private=true&include_all_commits=true" alt="GitHub stats" height="170" />
</picture>

<picture>
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=sebastianIncarbone&theme=tokyo-night&hide_border=true&area=true" alt="Contribution activity graph" width="100%" />
</picture>
