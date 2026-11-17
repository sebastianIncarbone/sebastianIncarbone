# Hi, I'm Sebastián Incarbone 👋

Senior full-stack developer — **Angular / .NET** — focused on **AI engineering** and **financial systems**. Based in Argentina.

I like problems where correctness is non-negotiable: market data, money math, and AI systems that keep the human in control.

![Angular](https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Vue](https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white)
![Ionic](https://img.shields.io/badge/Ionic-3880FF?style=for-the-badge&logo=ionic&logoColor=white)
![.NET](https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white)

## Professional work

### [Control Comercio](https://controlcomercio.com/) — retail management SaaS

`Angular` `Ionic` `.NET 8` `Azure SQL` `SignalR`

Multi-tenant platform where **~4,000 active businesses** run their sales, stock, and electronic invoicing. One Angular + Ionic codebase ships to web, Android, and iOS, backed by a .NET 8 API with background jobs and real-time updates. The integrations are where the real complexity lives: AFIP e-invoicing, MercadoPago QR payments, MercadoLibre / TiendaNube sync, and AI-assisted purchase-invoice ingestion.

### [Gestión Cervecera](https://gestioncervecera.com/) — ERP for breweries and beverage distributors

`.NET 8` `SQL Server` `Vue + Ionic`

Commercial ERP covering production, stock, keg and tap tracking, and deliveries with signature-based proof of delivery — for businesses operating in **nine countries**. The hard part: one multi-tenant system honoring each country's fiscal rules (AFIP in Argentina, electronic dispatch guides in Chile, Facturapi in Mexico), plus e-commerce sync with Shopify and WooCommerce.

### [PetCloud Store](https://petcloud.com.ar) — public storefront for a real pet shop

`Next.js 16` `React 19` `TypeScript` `Supabase` `MercadoPago`

Server-rendered storefront for a working pet shop, on Vercel over the same Postgres the admin writes to — SSR is a requirement, not a preference, because a shop that does not rank on Google does not sell. The hard part is the order: it carries two independent state machines, fulfillment and payment, and they share token names that mean different things — a cancelled payment is not a cancelled order. A single typed boundary parses both raw strings into one order state, nothing downstream accepts a bare status, and that state projects into **13 customer-facing views** collapsed onto a **four-step** public tracker. Checkout runs through MercadoPago, and it is the approved payment — not the click — that turns a stock reservation into a real sale.

### PetCloud ERP — desktop admin behind the same shop

`Electron` `React 19` `PostgreSQL` `Supabase` `MercadoLibre`

The internal half the shop runs day to day: products, variants, suppliers, purchases, sales, orders, and reports. Its governing rule is that business logic lives in Postgres, not in the client — stock, reserved units, weighted average cost, and COGS are computed by triggers and the client is forbidden from sending them, while anti-oversell locks the row `FOR UPDATE` and raises `INSUFFICIENT_STOCK` before it writes. A typechecker cannot see a single line of SQL, so those invariants are covered by a pgTAP suite instead. The sharpest edge is the MercadoLibre sync: its API **deletes any variation missing from a PUT**, so pushing stock means reading the item's full variation array back first and returning it complete — and failing closed on any doubtful value, because sending a `0` for stock you merely could not read would unpublish inventory that actually exists. Software with actual users — the kind that call when something breaks.

## Side projects

### Mercurio — a local, multi-project AI software factory

`Node 24` `node:sqlite` `React` `Claude Code` `systemd` `GitHub Projects` `Slack`

One service on my machine reads each project's GitHub Project board and, for every card I queue, starts a Claude Code session with the harness that card's phase needs. The phases are fixed for every project — define, design, code, test — and each is a chain of stations with gates and a routed exit; a project only configures which skills each phase loads and which review lenses its pull requests get (code and security are mandatory, UI and UX optional). The machine is shared under hard limits: a cap on concurrent sessions, a monthly and daily USD budget per project, and systemd CPU and memory caps on every command a project runs.

**Degree of automation: semi-autonomous — the system proposes, a human approves.** I decide what enters the queue and I merge; definition, design, implementation, tests, multi-lens adversarial review and the pull request run without me, and a person is pulled in only when a gate escalates or an approval is owed, answered from Slack. The factory also improves itself through two separate loops — a retrospective that proposes changes to its own prompts, skills and model routing as a PR backed by a replay comparison, and a "dreaming" pass that proposes memory operations — and neither lands without my approval. Full autonomy is deliberately not the goal: autonomy is granted in proportion to what the gates can verify, and the harness, not the model, is where the reliability lives.

**[Read the full story — the theory, the factory flow, where the human enters and how it improves itself →](mercurio/index.html)**

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

Hardening Mercurio's feedback loops: closing its self-improvement loop on production runs, measuring every prompt and memory change by replay before it lands, and running several projects in parallel with no intervention beyond queueing and approvals.

## GitHub activity

> Most of my day-to-day work lives in private repositories and my employer's Azure DevOps, so it is not reflected in these graphs.

<picture>
  <img src="https://streak-stats.demolab.com/?user=sebastianIncarbone&theme=tokyonight&hide_border=true" alt="GitHub streak stats" height="170" />
</picture>

<picture>
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=sebastianIncarbone&theme=tokyo-night&hide_border=true&area=true" alt="Contribution activity graph" width="100%" />
</picture>
