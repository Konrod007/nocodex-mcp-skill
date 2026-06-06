# NoCode-X Tutorial And Source Materials Index

This file records the non-private source/tutorial materials that were used as platform-learning inputs for this skill. Treat these as source navigation and implementation-example pointers, not as live MCP facts. Verify current behavior in the target NoCode-X workspace/application before making production claims.

## Source Folders

Original local source folder provided by the user:

```text
D:\cursor-prod\nocode-x\дополнение\nocode-x
```

A durable copy of the non-private tutorial/reference materials now lives inside this skill:

```text
C:\Users\admin\AppData\Local\hermes\skills\mcp\nocodex-mcp\references\source-materials
```

Copied into the skill:

```text
source-materials\SKILL.md
source-materials\NOCODE-X-FULL-ENCYCLOPEDIA.md
source-materials\NOCODE-X-FULL-ENCYCLOPEDIA.txt
source-materials\core\
source-materials\tutorials\
source-materials\guides\
source-materials\references\
```

Not copied intentionally:

```text
.sisyphus\
execution\
_temp_append.txt
backup files
```

Reason: those can contain local planning/execution artifacts or project-specific material. Do not copy private project details, app-specific business descriptions, or one-off migration plans into shared skill references. Only general platform methods and public/tutorial implementation patterns should be extracted.

## Main Source Indexes

- `SKILL.md` — original NoCode-X development skill/navigation file.
- `NOCODE-X-FULL-ENCYCLOPEDIA.md` — large merged encyclopedia compiled from the source materials.
- `tutorials/INDEX.md` — video tutorial index with links to detailed implementation guides.
- `guides/INDEX.md` — production and advanced guide index.
- `core/PLATFORM-OVERVIEW.md` — platform overview and core concepts.
- `core/QUICK-START.md` — quick start checklist.
- `core/ROCKET-MODE.md` — Rocket Mode guidance.
- `references/ui-design.md` — UI/template/layout reference.
- `references/data-logic.md` — database/action/logic reference.
- `references/state-and-lifecycle.md` — state, lifecycle, and security reference.
- `references/integrations.md` — integrations, external APIs, HTML/JavaScript, OIDC.
- `references/advanced-features.md` — advanced patterns such as vector database, payments, and SaaS-style features.

## Official Documentation Sources Added Later

These links were checked directly from the official NoCode-X documentation and may be used as source pointers in answers. Treat them as official documentation notes, but still verify live application behavior through MCP/browser when applying them to a concrete app.

- `https://docs.nocode-x.com/nocode-x-platform/users` — Users: workspace-linked users, rights/groups relationship, user creation fields, Temporary Password, Force OTP, Force WebAuthn, environment-specific users, destructive user deletion.

## Video Tutorial Series Present In Source Folder

### Mindshift Audio Series

Path pattern:

```text
tutorials/MINDSHIFT-AUDIO-PART-1.md
tutorials/MINDSHIFT-AUDIO-PART-2.md
tutorials/MINDSHIFT-AUDIO-PART-3.md
tutorials/MINDSHIFT-AUDIO-PART-4.md
```

According to `tutorials/INDEX.md`, this is a four-part mobile application tutorial covering:

- authentication and login pages;
- homepage and navigation;
- dynamic data and credits;
- n8n integration and AI chat.

Use these as implementation examples for:

- mobile-first page structure;
- authentication flow;
- navigation patterns;
- dynamic data loading;
- app credit/state logic;
- external workflow/AI chat integration.

### CRM Development Series

Path pattern:

```text
tutorials/CRM-PART-1-EMAIL.md
tutorials/CRM-PART-2-UPDATE.md
tutorials/CRM-PART-3-REFACTORING.md
tutorials/CRM-PART-4-CRUD.md
tutorials/CRM-PART-14-DASHBOARD.md
```

According to `tutorials/INDEX.md`, this series covers:

- AI email automation;
- update operations;
- UI refactoring;
- create/delete CRUD operations;
- AI-generated CRM dashboard.

Use these as implementation examples for:

- CRM-style data formats;
- CRUD actions;
- updating records;
- deleting records;
- AI-assisted email automation;
- dashboard layout;
- refactoring a visual application structure.

### Original Tutorial Series

Path pattern:

```text
tutorials/BONUS-RAPID-API.md
tutorials/PART-7-AUTHENTICATION.md
tutorials/PART-8-DATA-TABLES.md
tutorials/PART-9-OPENAI-CHATBOT.md
tutorials/PART-10-LLM-AUTOMATION.md
tutorials/PART-11-EMAIL-MAILJET.md
tutorials/PART-12-PINECONE.md
tutorials/PART-13-MAILCHIMP.md
```

According to `tutorials/INDEX.md`, these cover:

- secure backend for frontend / Rocket Mode-related flow;
- rapid API development;
- authentication and login;
- data tables;
- OpenAI chatbot;
- LLM automation;
- Mailjet email automation;
- Pinecone web crawler/vector workflow;
- Mailchimp email integration.

Use these as implementation examples for:

- custom API endpoints;
- authenticated flows;
- tabular data UI;
- chatbot UI/data flow;
- LLM automation actions;
- email integrations;
- vector/search workflows;
- external service integration patterns.

### Developer Update Videos

Path pattern:

```text
tutorials/MASSIVE-NOCODE-X-UPDATE-AI-OCR-MCP.md
tutorials/VIBECODING-AI-AGENTS-NOCODEX.md
```

User-provided transcript-derived notes from the developer video `Massive NoCode-X Update: Next-Gen AI Workflows, World-Class OCR & MCP Integration!` cover:

- LLM completion requests moving onto Rocket Mode's asynchronous/retry-capable generative-task infrastructure;
- updated model catalog across Claude, Llama, Mistral, GPT, and related families;
- optional custom API token vs fallback to NoCode-X account credits;
- generative-task observability for prompt, answer, model/status, and credit cost;
- image generation with generated files automatically stored in the media library;
- OCR over media-library files, page selection, and Markdown/HTML table output modes.

User-provided transcript-derived notes from `Vibecoding is Here: High-End Web Design + AI Automation with NoCode-X` cover:

- vibecoding / Rocket Mode conversational app building;
- Intent Canvas as an intent-description and validation surface;
- canvas nodes/edges for pages, data schemas, actions, agents, and their relationships;
- object-level intent for pages/tables/logic;
- switching between Rocket Mode and Visual Development Mode;
- canceling AI builds to control scope/credits;
- AI agents with name, daily budget, profile, avatar, goal, skills, and tools;
- external SaaS tools such as Gmail/Outlook/YouTube/Twitter/X;
- internal tools as NoCode-X Actions with inputs, outputs, and descriptions;
- scheduled agent tasks and custom cron expressions;
- Generative Task / Observability views for agent status, cost, conversations, tool calls, and outcomes.

Use this as source material for:

- AI workflow debugging;
- OCR/document-processing workflows;
- media-library-based generated asset workflows;
- prompt/model/cost observability checks;
- vibe-coding validation workflows;
- AI agent design, tool design, scheduled automation, and production hardening.

## Production And Advanced Guides Present In Source Folder

### Production Essentials

Path:

```text
guides/PHASE-1-FULL.md
```

According to `guides/INDEX.md`, this covers:

- jobs and scheduled automation;
- cron expressions and frequencies;
- groups and rights;
- authentication and authorization;
- auditability and data protection;
- publishing and DTAP release flow.

Use as source material for:

- production-readiness checklists;
- role/right modeling;
- job design;
- release/promotion guidance;
- security review.

### Advanced Features

Path:

```text
guides/PHASE-2-FULL.md
```

According to `guides/INDEX.md`, this covers:

- design system;
- colors and tokens;
- typography;
- dark/light mode;
- Hub, plugins, and integrations;
- installing and creating plugins;
- testing methods;
- debugging with logs;
- FAQ and platform philosophy.

Use as source material for:

- design-system implementation;
- plugin and Hub workflows;
- test/debug routines;
- platform capability explanations.

### AppSumo LTD Tier 3

Path:

```text
guides/APPSUMO-LTD-TIER-3.md
```

According to `guides/INDEX.md`, this covers resource limits and optimization strategies. Do not assume a target workspace uses this license unless confirmed by the user or account data.

## How To Use These Materials In Future Skill Updates

1. Prefer extracting reusable implementation recipes instead of copying whole tutorial transcripts.
2. Preserve references to the specific source tutorial when a pattern comes from a concrete video guide.
3. Do not extract private/local planning artifacts into shared references.
4. Mark source-derived claims as platform notes, not live app facts.
5. Verify with MCP/browser when applying a pattern to a real application.
6. Add missing practical recipes as separate reference files when they are substantial, for example:
   - `references/recipes-crud.md`;
   - `references/recipes-authentication.md`;
   - `references/recipes-data-tables.md`;
   - `references/recipes-jobs.md`;
   - `references/recipes-webhooks.md`;
   - `references/recipes-ai-chat.md`.

## Known Gap In Current Skill

The existing `platform-playbook.md` distills many ideas from these materials, but it does not yet preserve enough concrete, step-by-step implementation examples from the video tutorials. Future improvements should add recipe-level examples with source pointers, especially for CRUD, authentication, data tables, jobs, API/webhooks, AI chat, email automation, and dashboards.
