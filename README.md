# Hi, I'm Sebastián Incarbone 👋

Senior full-stack developer — **Angular / .NET** — focused on **AI engineering** and **financial systems**. Based in Argentina.

I like problems where correctness is non-negotiable: market data, money math, and AI systems that keep the human in control.

![Angular](https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white)
![.NET](https://img.shields.io/badge/.NET%208-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

## Professional work

### [Control Comercio](https://controlcomercio.com/) — retail management SaaS

`Angular` `Ionic` `.NET 8` `Azure SQL` `SignalR`

Multi-tenant platform where **~4,000 active businesses** run their sales, stock, and electronic invoicing. One Angular + Ionic codebase ships to web, Android, and iOS, backed by a .NET 8 API with background jobs and real-time updates. The integrations are where the real complexity lives: AFIP e-invoicing, MercadoPago QR payments, MercadoLibre / TiendaNube sync, and AI-assisted purchase-invoice ingestion.

### [Gestión Cervecera](https://gestioncervecera.com/) — ERP for breweries and beverage distributors

`.NET 8` `SQL Server` `Vue + Ionic`

Commercial ERP covering production, stock, keg and tap tracking, and deliveries with signature-based proof of delivery — for businesses operating in **nine countries**. The hard part: one multi-tenant system honoring each country's fiscal rules (AFIP in Argentina, electronic dispatch guides in Chile, Facturapi in Mexico), plus e-commerce sync with Shopify and WooCommerce.

### [PetCloud](https://pet-cloud-beige.vercel.app/) — commerce platform for a real pet shop

`Electron` `React` `TypeScript` `Supabase`

Two applications over one Postgres with row-level security: an Electron ERP the shop runs day to day — products, suppliers, purchases, sales, reports — and a public storefront where customers follow their own orders. The hard part: an order carries two independent state machines, fulfillment and payment, and they share token names that mean different things — a cancelled payment is not a cancelled order. A single typed boundary parses both raw strings into one order state, nothing downstream accepts a bare status, and that state projects into **13 customer-facing views** collapsed onto a **four-step** tracker. Software with actual users — the kind that call when something breaks.

## Side projects

### [Otto](https://github.com/sebastianIncarbone/otto-dictation) — offline dictation for Windows

`.NET 10` `Avalonia` `Whisper.net` `Vulkan` `Local LLM`

Hold a key, talk, release — the text lands wherever the caret was, in any application, and nothing ever leaves the machine. It exists because Whisper flattens *voseo*: where you say *instalá* it writes *instala*. The hard part is a latency budget — transcription, Rioplatense correction, and text injection all have to fit inside **1.02 s** from releasing the key, and that budget does not grow with how much you dictate, because whisper.cpp processes a fixed **30-second** window either way. Without a GPU the same work runs **17× to 37×** slower, so Otto probes the hardware at startup, downloads a smaller speech model, and never offers the local correction model at all — a 3B model cannot answer inside the budget on CPU, so it does not pretend it can.

### [QueLePongo](https://quelepongo.vercel.app) — explained scoring for project names

`React 19` `TypeScript` `Vite` `Vercel Functions`

Takes a project name and returns a score across **six weighted axes** — registry availability, domain, search noise, transmissibility, shape, brand identity — on a radar that shows where every point came from. It is not an availability checker: availability is one input, the product is the justification. The hard part is that a source which fails is not a source that says yes, and a network error must never read as *the name is free*. Every check is a three-state value — `ok`, `error`, `skipped` — so there is no boolean to fall onto, and an axis with no evidence leaves the denominator instead of redistributing its weight, because inflating the score would lie about how much was actually measured. Scoring lives as pure functions under test, separate from fetching; the API only fans out and caches raw bundles for **24 hours** at the edge, behind a canonicalizing redirect that stops the **32** case permutations of a five-letter name from shredding that cache and burning GitHub's **30 requests per minute** search quota.

## Certifications

Verified [Bloomberg for Education](https://portal.bloombergforeducation.com/) credentials:

- [Bloomberg Market Concepts (BMC)](https://portal.bloombergforeducation.com/certificates/zp1pr8KzzEDrDX177PK55zXP) — 2026
- [Bloomberg Finance Fundamentals (BFF)](https://portal.bloombergforeducation.com/certificates/8gyMSz3D33wLZbMKy4xpqqdo) — 2026
- [Bloomberg Spreadsheet Analysis (BQL)](https://portal.bloombergforeducation.com/certificates/CdKBjP4mjECydGpicbT8h8R4) — 2026

## Currently

Building agentic developer workflows: spec-driven development and multi-agent adversarial code review.

## GitHub activity

> Most of my day-to-day work lives in private repositories and my employer's Azure DevOps, so it is not reflected in these graphs.

<picture>
  <img src="https://streak-stats.demolab.com/?user=sebastianIncarbone&theme=tokyonight&hide_border=true" alt="GitHub streak stats" height="170" />
</picture>

<picture>
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=sebastianIncarbone&theme=tokyo-night&hide_border=true&area=true" alt="Contribution activity graph" width="100%" />
</picture>
