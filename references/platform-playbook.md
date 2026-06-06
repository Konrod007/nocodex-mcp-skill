# NoCode-X Platform Playbook

This file distills the local source materials from `D:\cursor-prod\nocode-x\дополнение\nocode-x`. Treat these as platform notes, not as live MCP facts. When auditing a specific app, verify with MCP first and label unavailable items as `Unknown`.

## Core Platform Concepts

NoCode-X is described in the source materials and official docs as a visual development platform with AI assistance. It combines:

- **Workspace**: isolated container around applications, users, developers, SSO settings, cores/resources, and private marketplace; official docs state resources/units are attached to a workspace, not the overall account.
- **Application**: belongs to a workspace and can be a web app, mobile app, pure API, or automation; it contains templates, APIs, actions, jobs, groups, rights, data formats, data, media, design systems, and plugins.

- **Rocket Mode**: AI-assisted app foundation generation and logic generation.
- **Standard Page / Application Dashboard**: default visual-development landing page with application description, recent versions per environment, urgent issues, latest log lines, resource links, and navigation to edit, versions, issues, and logs.
- **UI / Template editor**: visual page builder, root/child templates, responsive layouts.
- **Logic / Actions**: chained functions with triggers, scope variables, branching, loops, logging, action tests, and page-level action parameter values.
- **Database / Data Formats**: custom tables with fields, relationships, data classifications, and advanced query features such as selected attributes, aggregations, grouping, filters on aggregations, joins, nested joins, distinct, and OR filters.
- **API**: custom endpoints and external integrations.
- **Jobs**: scheduled/background execution of actions.
- **Design System**: central color, typography, spacing and component tokens.
- **Hub / Plugins**: reusable templates, actions, APIs and data formats.
- **Authentication / RBAC**: identity provider, roles, rights, protected templates/APIs.
- **DTAP / Versioning**: Development -> Test -> Acceptance -> Production release pipeline.
- **MCP tools**: AI agents can inspect and help debug NoCode-X workspaces, applications, actions, templates, data schemas, APIs, jobs, issues, logs, and page elements; mutating builder requests are also possible and should be treated as changes.

## Workspace And Application Planning

Official docs source: `https://docs.nocode-x.com/nocode-x-platform/workspaces` and `https://docs.nocode-x.com/nocode-x-platform/applications`.

Workspace rules:

- A workspace is an isolated boundary around applications, users, developers, SSO settings, cores/resources, and a private marketplace.
- Official docs state units/resources are attached to a workspace, not the overall account.
- Use one workspace for one internal team or simple setup.
- Use multiple workspaces when customers, billing, access controls, regions, compliance, or operational isolation must be separated.
- Start simple unless isolation/compliance/billing requirements justify extra workspaces.

Application rules:

- Applications can be web applications, mobile applications, pure APIs, or automations.
- An application belongs to a workspace and contains templates, APIs, actions, jobs, groups, rights, data formats, data, media, design systems, and plugins.
- Plan these attributes early: name, description, icon, endpoint, custom domain, meta title, meta description, home page, favicon.
- Configure a home page before relying on Play/testing because the official testing docs say Play opens the home page in the selected environment.

Developer access rules:

- Developers are distinct from application end-users.
- Developer access is limited by assigned workspace cores; a developer can access multiple workspaces.
- Developers with `Manage users` can invite developers and manage permissions if cores permit.
- Use coarse-grained application-level developer access first; fine-grained access exists but should be used pragmatically to avoid unnecessary complexity.

## Recent Platform Update Notes

Source: user-provided transcript of `NoCode-X Just Got Massive! 5 New Game-Changing Features (Rocket Mode, MCP Tools & More)`. Detailed notes: `references/source-materials/tutorials/NOCODEX-MASSIVE-5-FEATURES-ROCKET-MCP.md`. Treat these as platform notes from the transcript; verify in the live app or official docs before making production claims.

### Standard Page / Application Dashboard

When entering visual development mode, NoCode-X now shows a standard dashboard page. The transcript says it includes:

- application description;
- recent application versions;
- which versions are deployed to which environments;
- three urgent issues to solve;
- latest application log lines, including visible errors;
- links/resources;
- buttons for editing the application, viewing versions, viewing issues, and opening logs;
- log filtering by query.

Practical use:

- Start debugging from this page: check urgent issues and latest log lines first.
- Use it as the first operational monitoring surface before drilling into Actions, Issues, Logs, or Versions.
- For app audits, include the dashboard state if rendered UI access is available; MCP-only inspection may not expose the dashboard exactly as shown.

### Advanced Built-In Database Queries

The update adds or demonstrates advanced query features in the new version of filtered data retrieval:

- selecting only needed attributes;
- aggregations such as SUM and AVERAGE;
- grouping by an attribute;
- distinct results;
- filters on aggregated values, equivalent in concept to filtering grouped totals;
- joins between data formats by matching local field to target field;
- filters on joined data;
- joins on joins;
- OR filters;
- combining joins, grouping, filters, and aggregations.

Practical use:

- Prefer database-level aggregation for dashboards and reports instead of fetching all rows and summing in Actions.
- Use grouping and aggregation for totals per product, customer, status, project, source, day, or role.
- Use joins when one data format stores another format's ID and the UI/report needs fields from both.
- Keep source-specific data separated even when joining; for position data, never collapse multiple sources into one global position unless a display rule explicitly chooses the source.
- Test advanced queries with small known datasets first, then add filters and joins step by step.

### DataTable performance and server-side paging

Transcript-derived notes from a developer campfire explain that older/current DataTable paging can be client-side: the page loads all rows and then paginates in the browser. This is slow for large datasets such as tens of thousands of records.

Practical use:

- For large tables, avoid loading all rows into the browser.
- Use server-side paging/filtering/sorting when available so each page retrieves only the needed rows, e.g. 20 records.
- Combine DataTable paging with selected attributes and database-level filters/aggregations.
- When diagnosing a slow table, check row count, query shape, selected attributes, joins, filters, and whether paging is client-side or server-side.
- Treat simple server-side DataTable paging as transcript-derived/roadmap unless verified in the current app's function picker.

### Page-Level Action Parameter Values

Actions linked from pages can now expose input fields for their defined parameters directly in the page/action binding settings. The transcript says:

- every action parameter becomes configurable where the action is called from the page;
- fixed values can be entered directly;
- placeholders and LiquidJS can be used;
- automatic inheritance from page parameters remains backward compatible if the field is left empty.

Practical use:

- Use explicit page-level parameter values when the same Action is reused by multiple buttons/templates with different constants.
- Use inherited page parameters when the parent page/template already supplies the value.
- Avoid duplicating Actions solely to hardcode small differences; parameterize one Action instead.
- For debugging, inspect the page binding as well as the Action signature: missing or wrong values may now live on the page-level action binding, not inside the Action itself.

### Rocket Mode Logic Improvements

The transcript says Rocket Mode has improved logic generation, especially generating end-to-end logic with the built-in database from a zero-shot prompt. No concrete app example or acceptance data was provided in the transcript.

Additional developer-campfire positioning:

- NoCode-X is intentionally not positioned as pure one-shot AI app generation;
- Rocket Mode should give a head start/scaffold that users refine through the no-code visual layer;
- current Rocket Mode was described as page-first: root page, other pages, then hidden/generated logic behind those pages;
- future `Vibe Mode` was described as conversational back-and-forth after Rocket Mode for incremental edits such as copy or style tweaks;
- future AI scope is expected to include jobs, APIs, and more, not only pages, but verify live availability before relying on it.

Practical use:

- Rocket Mode may now be more useful for generating database-backed logic, but verify generated data formats, actions, bindings, issues, and logs before trusting the result.
- Continue giving structured requirements: data model, pages, actions, roles, test data, and acceptance checks.
- Treat Rocket Mode output as a draft that must be inspected and tested, not as automatically production-ready.
- For builder prompts, include desired actions, jobs, APIs, data, rights, and test expectations instead of only visual pages.

### CodeGen-X direction

Transcript-derived developer notes describe the current model as a no-code/AI abstraction interpreted to serve the app in environments. `CodeGen-X` is the stated direction of generating a codebase from that abstraction.

Stated reasons:

- generated code should stay stable even after many NoCode-X platform upgrades;
- generated code can run on NoCode-X or potentially on user-owned servers;
- generated code unlocks broader use of libraries such as Tailwind and authentication libraries;
- generated apps can become leaner and faster;
- the visual no-code abstraction remains valuable and should not disappear.

Practical use:

- Treat CodeGen-X as strategic/roadmap context unless the target app/account has confirmed generated-code/export features.
- In export/plugin audits, distinguish current verified export capability from future generated-code direction.
- For production-risk discussions, CodeGen-X matters because it addresses platform-upgrade stability and performance concerns, but do not claim it is already available without evidence.

### MCP Tooling Expansion

The transcript confirms NoCode-X MCP usage from an AI agent for:

- listing workspaces and switching workspace/application;
- listing actions;
- inspecting an action and seeing a TypeScript-like visualization of action steps;
- checking issues for an action;
- listing and inspecting templates, including elements and parameters;
- listing and inspecting data schemas;
- accessing jobs and APIs;
- helping debug settings and page elements;
- requesting changes such as creating pages, databases, logic, or an application.

Practical use:

- For read-only debugging, inspect workspace, application, actions, templates, data schemas, APIs, jobs, issues, and logs before changing anything.
- For mutating requests, gather facts first and make a precise builder request naming target objects and desired changes.
- Remember that MCP facts and rendered UI facts can differ; label unavailable items as `Unknown` and verify important UI behavior in the browser/preview.

### Next-Gen AI Workflows, Image Generation, OCR, And Observability

Source: user-provided transcript of the developer video `Massive NoCode-X Update: Next-Gen AI Workflows, World-Class OCR & MCP Integration!`. Detailed notes: `references/source-materials/tutorials/MASSIVE-NOCODE-X-UPDATE-AI-OCR-MCP.md`.

The transcript says the existing `LLM completion request` now uses the same underlying infrastructure as Rocket Mode. It still supports user/assistant/system prompts, placeholder replacement, model selection, optional custom API tokens, and fallback to NoCode-X account credits. The practical platform change is more robust asynchronous generative-task execution, retry behavior, and centralized observability.

Observed AI workflow capabilities from the transcript:

- updated model catalog including newer Claude, Llama, Mistral, GPT, and related models;
- LLM observability showing request prompt, generated answer, model/status, and credit cost;
- image generation from a prompt, with placeholder support and optional file inputs;
- generated images are automatically stored in the NoCode-X media library;
- generated media can then be used in normal file workflows: display in UI, email, FTP/external upload, database storage, or downstream actions;
- OCR over media-library files, demonstrated with an invoice;
- OCR page selection through a page list/range-style input, with page zero used in the demo;
- table output mode can be Markdown for most uses or HTML when visual/table structure matters.

Practical use:

- Debug AI workflows through generative-task observability before guessing from action logs alone.
- For production AI flows, store business-relevant output and provenance in application data records: user, prompt, model, task/status, media ID, selected pages, OCR mode, and review/approval state.
- Use image generation for placeholders, marketing assets, illustrations, and user-specific visuals, but add approval/content-safety controls before end-user exposure.
- Use OCR as a first step in document-processing workflows: media file -> OCR Markdown/HTML -> LLM extraction/validation -> structured data -> review/approval -> external API/email/storage.
- Verify page numbering, table output mode, model availability, API-token behavior, credit cost, and exact UI labels in the live editor before writing production instructions.

### Vibecoding, Intent Canvas, And AI Agents

Source: user-provided transcript of the developer video `Vibecoding is Here: High-End Web Design + AI Automation with NoCode-X`. Detailed notes: `references/source-materials/tutorials/VIBECODING-AI-AGENTS-NOCODEX.md`.

The transcript demonstrates two related platform patterns:

- vibecoding/Rocket Mode conversational app building;
- AI agents that execute business workflows using skills, external tools, internal NoCode-X action tools, schedules, and observability.

Observed Intent Canvas behavior:

- helps describe build intent and validate whether AI honored it;
- level 3 is shown as a validation level;
- pages, data schemas/tables, actions/logic, and agents appear as nodes;
- edges show relationships such as page -> action trigger and action -> database write;
- object-level intent exists for pages, tables, and logic, and can be manually changed;
- canvas supports folders, refresh, zoom/scroll, minimap, and visible workspace credit tracking.

Practical use:

- Use Intent Canvas as a non-code validation layer, but still test generated pages/actions/data with real runs and stored records.
- Mix Rocket Mode and Visual Development Mode: use AI for scaffolding/broad changes and manual visual editing for precise UI polish.
- Cancel AI builds early if the output is going in the wrong direction to control credit spend.
- For generated landing pages, review generated media, labels, alignment, responsiveness, CTA behavior, and form usability before production.

Intent-first discovery/build notes from `Idea to App in 6 Questions` (`references/source-materials/tutorials/IDEA-TO-APP-6-QUESTIONS-INTENT-CANVAS.md`):

- The pre-build question flow is adaptive rather than hardcoded; the transcript says it usually asks about six to nine questions.
- Generated intent text is stored context. Read/edit application, mission, persona, journey, functional, non-functional, folder-structure, look-and-feel, and design-system intents before building.
- Edited intents are used by subsequent AI calls; if output is wrong, inspect whether an earlier intent contains the wrong assumption.
- Personas can encode accessibility, security, and interaction constraints such as minimum 18px typography, single-column layout, and limited top-level navigation.
- Customer journeys link personas to screen flows, validation steps, and conversion paths; the transcript shows an editable Mermaid/flow representation.
- New apps have default application, design/design-system, and folder-structure intents; overwrite these deliberately for serious builds.
- Folder-structure intent can steer single-page root organization or larger feature-based folders with pages/actions/database subareas.
- Design intent describes mood/copy-level direction; the design system holds hard variables used by CSS/generation.
- Level Three / Visual Development Mode can inventory generated databases, actions, components/pages, generated media, and form logic.
- Generated websites can be dynamic: e.g. services database loaded by a page-load action and contact requests stored by a submit action.
- QA generated apps for branding/name drift, stale journey assumptions after architecture changes, overbuilt sections, persona-avatar/UI bugs, data wiring, form validation, stored rows, Issues, logs, and accessibility constraints.

Practical Rocket/Rocket Mode building notes from `NoCode-X Campfire: Building with Rocket Mode` (`references/source-materials/tutorials/CAMPFIRE-BUILDING-WITH-ROCKET-MODE.md`):

- You can skip full canvas planning and build directly at realization level for prototypes, but serious builds still need post-generation canvas/app inspection.
- Broad prompts are acceptable for initial scaffolds; follow-up changes should be small, precise, and reference exact element/card/media/page/action names.
- Use selected-element scope as a guardrail: target the smallest relevant component for narrow changes, or the top-level container for page-wide changes.
- Generated UI may include standard editable NoCode-X components plus local CSS/JavaScript; inspect the component tree, local styles, and local JS after generation.
- CSS animations can run in the editor; JavaScript-driven behavior should be verified in live preview because JS is not executed in the editor.
- For media generation, prefer generate/place one image at a time, verify media-library creation, then verify rendered placement as a media component.
- Use the AI to-do/progress list, prompt reuse, cancel, and AI-change undo/versioning to control cost and blast radius.
- Treat before/after app versions and future branches as important safety primitives for AI blocks of changes.
- Use observability context — logs, Issues, tests, and job run logs — when asking AI to debug rather than relying on guesswork.
- Use the realization graph to trace pages, actions, and data formats: page -> action trigger, action -> data read/write/update/delete, and missing required arguments.
- Do not cite the login-flow portion as proof of a complete working AI-generated login flow; the demo was interrupted and partly manual.
- Mark the demonstrated advanced Rocket/MCP builder features as in-development unless verified in the current production environment.

Observed AI agent model:

- an agent has name, daily budget, profile, avatar/image, and goal;
- skills describe reusable procedures and can be shared across agents;
- external tools connect to SaaS providers such as Gmail/Outlook/YouTube/Twitter/X and require authentication;
- internal tools are NoCode-X Actions that can read/write data, use media library, call APIs, or perform other app logic;
- tool input descriptions and output names matter because they guide the agent;
- agents can be run manually through chat or through scheduled tasks such as daily/every 12 hours/every 6 hours/custom cron;
- Generative Task / Observability views show status, credit cost, conversation, generated outputs, tool calls, tool success/failure, timestamps, and multi-agent overviews.

Practical use:

- Design agent tools as narrow, typed, well-described NoCode-X Actions.
- Let skills explicitly name which tools to use and in what order.
- Persist business-critical state in data records, not only in agent summaries or observability logs.
- Verify actual side effects such as sent emails and updated records instead of trusting the final agent summary alone.
- Start with manual agent chat/test records, then enable scheduled tasks with conservative frequency and budgets.

Production hardening reminders:

- add idempotency so the same record is not handled twice;
- store reply text, sent timestamp, external message ID, agent run ID, error state, and handled/answered flags;
- add human review and escalation rules for sensitive domains;
- keep external tool permissions least-privilege;
- monitor generative-task cost and tool-call failures.

### Issues, Tests, Jobs, And 1000+ Agent Tools

Source: user-provided transcript of the developer video `1000+ AI Tools Connected: The Future of NoCode-X Agentic Workflows`. Detailed notes: `references/source-materials/tutorials/AI-TOOLS-AGENTIC-WORKFLOWS-NOCODEX.md`.

The transcript expands the agentic platform model with stronger observability and testing primitives.

Observed Issues / Observability behavior:

- Observability now includes an `Issues` area for action problems;
- examples include missing required arguments and unused/dead-code invocations;
- major/bug issues can close while retaining trace/history;
- smaller issues may disappear when fixed;
- AI checks issues after changing actions and attempts to repair them.

Observed action testing behavior:

- actions can have configured tests with parameter values;
- test runs show block execution order and per-block trace/error logs;
- action outputs are name-based and should match variables produced by action functions;
- assertions validate expected outputs;
- newer/coming `Side Effect Checks` validate how functions were invoked, useful for no-output actions that write data, call APIs, or send emails;
- an application-wide test overview can run all tests, one action's tests, or a single test;
- AI is expected to run tests after changes and fix failures.

Observed scheduled job behavior:

- jobs execute scheduled logic periodically;
- advanced custom cron uses six fields, not common five-field cron;
- application logs have filters for environment, log level, page, action, amount, and a timeline/bar;
- log-line lightning-bolt navigation opens the action that produced the log;
- scheduled job observability shows individual job runs, times, and durations;
- planned improvement: click a job run to see logs only for that exact run.

Observed AI/auth/page hierarchy notes:

- for login pages, prefer the dedicated `route to login` function rather than generic `route to page`, because login pages are special identity-provider pages;
- test login flows in incognito/unauthenticated state and verify failed/timeout/email-sent status handling;
- shared layout pages can act as parent pages for dashboard/profile/crew-style child pages with common side navigation.

Observed agent/tool model:

- NoCode-X claims 1000+ external tools/toolkits for agents;
- external tools can require authentication, e.g. Gmail OAuth-style connection;
- internal tools are NoCode-X Actions assigned to an agent;
- example: agent reads Gmail, summarizes last email, then calls internal `add email to database` action to persist an `Email` record;
- agent `Tasks`/Observability show conversation, tool search, external tool calls, internal tool calls, parameters, large outputs, and cost/credits;
- large tool outputs can inflate input tokens/cost, so tool outputs should be minimized.

Practical use:

- Treat Issues + tests + side-effect checks as guardrails for AI/Rocket Mode changes and agent tools.
- Test internal action tools before assigning them to agents.
- Use narrow, typed, well-described agent tools with minimal outputs.
- Verify actual side effects in data/logs/external systems instead of trusting agent summaries.
- Do not enable schedules until issues/tests/observability are clean.
- For app-health audits, inspect Issues, centralized tests, scheduled job runs, application logs, and generative task/tool-call traces together.

## Rocket Mode: Better Prompts

Use Rocket Mode for app foundations and broad changes, but provide structured requirements.

### Recommended 10-step input structure

1. Application name, tagline and feature list. Prefer action-oriented features: `Send email reminders`, not vague nouns like `Notifications`.
2. Customer journey per persona: trigger -> steps -> success.
3. Requirements prioritized with MoSCoW: Must / Should / Could.
4. Design System: palette, fonts, spacing, components and states.
5. Pages: one page = one job, with a single primary CTA.
6. Test users for each role.
7. Database: tables, fields, relationships and access rules.
8. Test data: realistic sample records.
9. Root page: build the visual shell first, then logic.
10. Other pages: repeat design -> logic per page.

### Prompt style

Good prompts:

- `Rename the app to EventPro and make the tone friendly and trustworthy.`
- `Keep booking, listing and email reminders as Must. Move analytics to Later.`
- `Add Attendance as a join table between Users and Events with user_id, event_id and status.`
- `Make Browse Events the primary CTA and add a three-step How it works section.`

Avoid vague prompts:

- `Make it better.`
- `Improve the design.`
- `Add notifications.`

## UI And Template Practices

### Template hierarchy

- **Root Template**: shared elements visible across pages, such as navigation, header, footer and global shell.
- **Child Templates**: page-specific content that inherits root elements.

Rule: put global elements only in the root. Put unique page content in child templates.

### Mobile-first layout

- Start with mobile view when the product is mobile-heavy.
- Use vertical lists for stacked forms and content.
- Use horizontal lists for row layouts such as checkbox + label or navigation items.
- Prefer `Fit to content` over rigid fixed pixels where possible.
- Use min-size and wrap behavior so components do not collapse on small screens.
- Test on real devices or browser preview, not only by reading template metadata.

### Navigation patterns

For mobile bottom navigation:

```text
Main vertical container
├─ Scrollable content area
└─ Fixed/non-scroll bottom menu as horizontal list
   ├─ Icon + label
   ├─ Icon + label
   └─ Icon + label
```

For SVG icons, prefer `currentColor` for `stroke`/`fill` so icons follow theme/text color.

For floating/sticky UI such as nav bars or chat launchers, the transcript-derived `position is fixed` style setting keeps an element visually in place while the page scrolls. Verify in Play/preview because the template editor may not fully demonstrate fixed-position behavior.

### Template placeholders and LiquidJS

Transcript-derived update notes say NoCode-X enhanced template placeholders with LiquidJS while keeping older pipe-based formatting backward compatible.

Useful implications:

- old placeholder pipes for formatting/fallbacks may still work;
- LiquidJS filters can format values, e.g. conceptually `{{ name | capitalize }}`;
- LiquidJS tags can support conditional/loop-like rendering in template text/title content;
- list element access by index is possible according to the transcript;
- dropdown choices can use placeholders, but replacement may occur in the rendered app rather than the template editor.

Use LiquidJS for display formatting, fallback display text, small conditional strings, and simple list rendering. Avoid hiding complex business logic inside placeholders when an Action, database query, or action test would be clearer. In audits, inspect placeholder text because template content may contain meaningful logic that is not visible from the rendered label alone.

### Dense layout editing

For pages with many tightly packed elements, visual drag/drop can be jittery. Transcript-derived workarounds and roadmap notes:

- use navigator/reorder controls when available instead of only the WYSIWYG canvas;
- reorder handles may work inside a horizontal/vertical list even when cross-list moves are harder;
- vertical/horizontal lists may grow while dragging over them to make dropping easier;
- element locking and keyboard movement were discussed as ideas, but treat them as unavailable unless verified in the current UI.

### Naming conventions

Clear names help both humans and AI tooling:

- Bad: `Title`, `button_3`, `email_input_1`.
- Good: `Title_Welcome_Name`, `signup_submit_button`, `login_email_field`.

## Data, Logic, Scope And State

### Data formats as contracts

Official docs source: `https://docs.nocode-x.com/building-concepts/data/Data formats/` and related creation pages.

Data formats define the contract for data used in NoCode-X, especially for actions and built-in database storage. Data stored in the built-in database must be valid according to its data format.

Data-format metadata includes name, description, tags, and icon. Properties/fields define types, required/optional status, validations, default values, and dependencies/relationships.

Data-format action triggers documented by official docs:

- After creation of data;
- After update of data;
- After removal of data.

Reserved field keys documented by official docs — do not use as user-defined field keys:

- `properties`;
- `items`;
- `noCodeXType`.

Creation methods documented:

- blank/manual data format;
- from CSV using generative AI;
- from JSON;
- from text/business description using generative AI.

CSV import checklist:

- consistent separators;
- unique header fields;
- required fields present;
- column data types match expectations;
- special characters escaped;
- consistent date formats.

JSON import notes:

- JSON must be valid;
- official docs mention JSON schema draft-07 compatibility;
- required fields become mandatory;
- field types and format validations such as email are mapped/preserved;
- multiple JSON schemas can create multiple data schemas.

Modeling rule:

- Use a consolidated nested data format only for small, naturally embedded data that is rarely filtered or updated independently.
- Prefer normalized linked formats for entities that need filtering, permissions, independent updates, history, reporting, joins, or analytics.

### Scope vs State

| Concept | Use | Lifetime |
|---|---|---|
| Scope | temporary data inside one Action chain | current action execution |
| State / Blackboard | global app state visible to templates/actions | while app is open |

Use Scope for intermediate action values. Use State for shared data such as theme, auth status, current role, balance or global filters.

### Global variables in Actions

Transcript-derived update notes say global variables can be accessed inside Actions by creating an Action parameter with exactly the same name as the global variable.

Conceptual pattern:

```text
Action A sets global variable:
name = "Tristan"

Action B defines parameter:
name

Action B can use/log/reason with:
name == "Tristan"
```

The transcript says this works for simple values and also nested objects/arrays.

Important precedence rule:

```text
explicit template/action parameter value wins over same-name global variable
```

Resolution order from the transcript:

1. if the page/template/action binding passes a parameter value, use that explicit value;
2. otherwise, look up the same-name global variable.

Debug checklist for wrong global/action values:

1. Confirm the Action parameter name exactly matches the global variable name.
2. Inspect page/template action-binding parameter values.
3. Inspect inherited parent-template parameters.
4. Inspect where the global variable is set.
5. Check action logs/tests for the value actually received.

Avoid generic global names such as `name`, `id`, `status`, or `value` when possible. Prefer namespaced conventions such as `auth.currentUser`, `ui.activeTab`, `filters.status`, or `cart.total`. Do not use global variables as a security boundary or durable database.

### Dynamic data population

Typical page init:

```text
Trigger: On Load
Action: Initialize Page
├─ Load current user / app config
├─ Replace placeholders
├─ Load list/table data
└─ Set State values needed by child components
```

`Current user` is described as globally available for common authenticated-user fields. Verify exact fields in the app/schema before relying on them.

### Branching and visibility

Use branching for role-specific UI and flow control:

```text
IF current_user.role == admin
  Show admin panel
ELSE
  Hide admin panel
```

For sensitive surfaces, UI hide/show is not sufficient. Enforce access through template/API/action permissions too.

### Loops and date comparisons

For date-based loops, normalize dates before comparison:

- Bad: compare full timestamps when only calendar date matters.
- Good: compare `YYYY-MM-DD` strings or date-only values.

Example pattern for activity/streak UI:

```text
For each day in range
├─ calculate target date
├─ search records for current user + date-only value
├─ render active or inactive day template
└─ append to list
```

### Action editor planning notes

Official docs source: `https://docs.nocode-x.com/nocode-x-platform/Action editor` and logic/analyzer docs.

Action editor concepts:

- Function picker: ready-to-use functions dragged into logic.
- Function instance: configured function call executed when reached.
- Function instance settings: name, description, icon, tags, parameters, and output.
- Start/action settings: action information, parameters, and output.
- Action canvas: visual execution path.
- Action-specific tools: zoom, automatic block layout, and tests.

Important rule: a function instance not reachable from the start block never executes and is effectively dead.

Transcript-derived note: `subflow` in Actions is primarily an organization/commenting tool unless current live behavior proves otherwise. It can group coherent parts of an action such as `read from database`, `process data`, and `write to database`, but the transcript says it does not execute anything by itself. Use it to document large actions; do not assume it is an executable container or collapsible block unless verified.

Action planning checklist:

- Define parameters and outputs before wiring complex logic.
- Add logs for important state transitions and errors.
- Use action tests before attaching the action to pages, APIs, jobs, or data triggers.
- Check built-in Issues/analyzers for null pointer, missing params/output, out-of-scope references, deprecated functions, missing required fields, invalid data-format references, secure data exposure, unused code, and accessibility contrast issues.

### Template editor planning notes

Official docs source: `https://docs.nocode-x.com/nocode-x-platform/Template editor`.

Template editor concepts:

- Element picker: ready-to-use UI elements.
- Element instance: configured UI element visualized in the application.
- Element instance settings: element settings, style settings, and action triggers.
- UI visualization: preview canvas with pan/zoom.
- Template-specific tools: screen type, zoom, grid, multilingual settings, page hierarchy, authentication/authorization, template settings, and UI testing.

Template planning checklist:

- Plan page hierarchy and root/child template split.
- Configure authentication/authorization on sensitive templates; hiding UI is not enough.
- Plan multilingual requirements early if needed.
- Test UI through the preview/play environment, not only by reading metadata.

## APIs And Integrations

### API creation and CRUD generation

Official docs source: `https://docs.nocode-x.com/building-concepts/api/` and `https://docs.nocode-x.com/building-concepts/api/CRUD from Data-format`.

NoCode-X APIs support data exchange, automation, and integration with external services. Official creation options include:

- blank API;
- full CRUD from Data Format;
- full CRUD from text;
- create/read/find/update/delete APIs from Data Format;
- create/read/find/update/delete APIs from text.

CRUD from Data Format creates APIs for:

- read a single item;
- read a list of items;
- create a single item;
- update a single item;
- delete a single item.

API planning rules:

- Define Data Formats first when APIs expose internal data.
- Treat generated CRUD APIs as scaffolding; inspect naming, authentication, authorization, validation, pagination, logs, and error handling before production use.
- Keep data layer and processing/action layer separated unless there is a clear reason to combine them.

### NoCode-X as backend

The source materials describe NoCode-X as usable as a backend for external frontends:

```text
External frontend -> OIDC login with NoCode-X -> protected NoCode-X API -> database/actions
```

Checklist:

- Create Data Format and test data.
- Create API endpoint.
- Test endpoint without auth only during development.
- Configure Authentication.
- Get Issuer ID / Client ID / redirect URL values from NoCode-X.
- Enable authentication on production API endpoints.
- Send `Authorization: Bearer ***` from the frontend.
- Handle 401/403 and token expiration.

Security notes:

- For SPAs, do not expose `client_secret` in browser code.
- Use PKCE-capable OIDC flows/libraries.
- Redirect URL must match exactly, including protocol, port and trailing slash.

### HTML components

Use HTML components for custom UI not available in standard widgets, such as charts, calendars, audio players, complex forms or embedded chat.

Rules:

- Pass environment-specific config via NoCode-X parameters or configuration tables.
- Do not hardcode secrets in HTML/JS.
- Mark API keys as Secret fields.
- Add input validation and error handling inside custom JavaScript.
- Keep custom components small enough to debug.

### External services

Source materials mention integrations via API/webhooks/CDNs, including n8n, OpenAI, Pinecone, MailJet/Mailchimp, Stripe, YooKassa, Telegram and Deepgram. Treat availability of a native integration as app/platform-version dependent; verify current docs or MCP/app objects before claiming it exists in a target app.

## Jobs And Automation

Official docs source: `https://docs.nocode-x.com/building-concepts/jobs/`.

Jobs execute logic periodically. Job configuration includes:

- Name;
- Description;
- Icon;
- Tags;
- Frequency;
- Execution: one or more actions to execute periodically.

Documented frequency options include: Paused, Advanced cron, every 5/10/30 minutes, every hour, every 2/6/12 hours, daily variants, monthly variants, and yearly variants.

Advanced cron format in the official docs is 6 fields:

```text
second minute hour day-of-month month day-of-week
```

Example:

```text
0 30 2 * * *   # daily at 02:30
```

Common patterns:

- Daily report generation.
- Data cleanup/archive.
- API polling/sync.
- Subscription/expiration checks.
- Alert evaluation.

Job design rules:

- Single responsibility per job.
- Appropriate frequency; avoid wasteful high-frequency jobs.
- Test the underlying action independently first.
- Add application logs and error handling.
- Monitor execution duration and failures.
- Avoid overlapping jobs that can race on the same records.

## Security, RBAC And Data Protection

### Users and workspace-level user management

Official docs source: `https://docs.nocode-x.com/nocode-x-platform/users`.

The official Users page describes a user as a person or machine using a NoCode-X application. Users can have rights and/or belong to groups. Users and their rights are managed in User Management. Users are linked to a workspace, enabling a single-sign-on style experience across applications built for a company/workspace in NoCode-X.

User creation fields documented on the official page:

- Email: used as the username.
- Password: initial password; documented minimum is 8 characters, at least 1 number, and at least 1 uppercase letter.
- Confirm Password: repeat the initial password.
- Temporary Password: boolean, ON by default; if enabled, the user must change the password on first login.
- Force OTP: boolean, OFF by default; if enabled, the user must set up an authenticator-app one-time password.
- Force WebAuthn: boolean, OFF by default; if enabled, the user must register a WebAuthn device such as a security key or biometric device.
- Firstname.
- Lastname.
- Choose Environment: development, test, acceptance, or production.

User management rules:

- Prefer Temporary Password ON for manually created users so admins do not retain knowledge of the user's real password.
- Use Force OTP for stronger two-factor authentication where appropriate.
- Use Force WebAuthn for phishing-resistant authentication where appropriate and supported by the user's device/browser.
- Create users in the correct environment; keep development/test/acceptance users separate from production users.
- Treat user deletion as destructive: the official page says deletion cannot be undone and also revokes memberships, permissions, and rights associated with the user.
- Before deleting a user in a production app, verify whether records, audit trails, ownership fields, or external integrations depend on that user. The docs page confirms permission revocation, but does not describe business-record reassignment behavior.

### RBAC model

- **Rights**: technical privileges, ideally named in `VERB_NOUN` form, e.g. `CREATE_ORDER`, `VIEW_REPORTS`.
- **Roles / Groups**: functional personas, e.g. `Customer`, `SalesManager`, `SystemAdmin`.
- Users receive roles; roles contain rights; rights are assigned to templates/APIs/actions as appropriate.

Workflow:

1. Identify personas.
2. Write user stories: `As a [role], I want to [action], so that [benefit]`.
3. Map app functions to technical rights.
4. Group rights into roles.
5. Assign roles to users.
6. Test access boundaries, including negative cases.
7. Test user creation/login per environment, including Temporary Password, OTP/WebAuthn enrollment, and negative access cases.

### Data classification

Source materials describe field classifications:

| Classification | Typical use |
|---|---|
| Public | non-sensitive profile/display data |
| Internal | internal IDs and system data |
| Confidential | restricted personal/business data |
| Secret | API keys, passwords and highly sensitive values |

Use Secret fields for API keys and credentials. Do not print secret values in logs or final answers.

### Security checklist

Official docs source: `https://docs.nocode-x.com/security/Securing your application`, `Authentication`, `Authorization`, `Auditability`, and `Backup`.

- Configure authentication through the embedded identity provider or SSO.
- SSO support documented: OpenID Connect 1.0 and OAuth 2.0.
- With external SSO, the external identity provider is responsible for authentication strength and credential lifecycle.
- Use least privilege and need-to-know authorization through groups/rights.
- If a group is defined on a resource, users outside the relevant group should have no access according to the Authorization docs.
- Classify sensitive data at attribute level.
- Enable/implement logging for create, update, delete, and sensitive reads.
- Official audit docs say updates/deletions/creations are logged by default, and sensitive labelled data has read access logged.
- Official audit docs state logs are retained for up to one year.
- Use write-audit-log/logging components in actions where needed.
- Enable AI guardrails when embedding AI into applications.
- Monitor the creator/dashboard security detections such as unauthenticated exposure of sensitive information.
- Use HTTPS for external calls/webhooks.
- Do not hardcode secrets.
- Do not print secret values in logs or final answers.
- Test backup/recovery and data export expectations before production claims.

Backup and residency notes from official docs:

- Managed-service backups are documented as twice daily at 00:00 and 12:00 CET, giving a stated RPO of 12 hours.
- Backups are described as out-of-band and isolated from runtime.
- Self-hosted backup configuration can be customized, but the customer owns operational responsibility.
- Managed-service data residency docs state processing/storage is restricted to Belgium and France; verify current contractual status before compliance commitments.


## Design System And Plugins

### Design System

Build semantic tokens first:

- Brand: `Primary`, `Primary Light`, `Primary Dark`, `Secondary`.
- Semantic: `Success`, `Warning`, `Error`, `Info`.
- Neutral: `Background`, `Surface`, `Text Primary`, `Text Secondary`, `Border`.

Avoid literal names like `Blue` or `Big Text`. Use tokens consistently so light/dark modes and brand changes can propagate.

### Hub / plugins

Plugins are described as reusable blueprints containing templates, actions, APIs and data formats. Use them for common patterns, but do not treat plugins as black boxes.

Checklist:

- Review README/documentation.
- Install/test in Development first.
- Inspect generated templates/actions/APIs/data formats.
- Customize intentionally.
- Document customizations.
- Remove unused plugins.

## Testing, Debugging And Release

### Testing surfaces

- Play/preview environment testing.
- Action Tester for step-by-step logic execution.
- Manual UI testing for buttons, forms, navigation, mobile behavior, loading/error states.
- Application Logs for action traces, variable values, errors and performance.
- Browser DevTools for rendered UI console/network errors.

### Common errors

| Symptom | Likely cause | First check |
|---|---|---|
| No homepage set | app has no configured start template | application settings -> homepage |
| Authentication required | template/API requires login or role | login, auth settings, role assignment |
| Value argument was null | missing action input/data binding; or page-level action parameter value is empty/wrong | action logs, action signature, page action binding parameter fields, inherited page/template parameters |
| Action not executing | trigger missing/disabled/condition false | trigger config, conditions, rights |
| API 401/403 | missing/expired token or auth misconfig | Authorization header and API auth settings |
| Slow app/query | inefficient query, missing pagination, too much data, or aggregation/join not pushed into the database query | logs, pagination, filters, selected attributes, aggregation/grouping/join settings |
| Global variable ignored in Action | explicit page/template/action parameter with same name overrides the global variable | action parameter names, page binding parameter values, global variable setter |

### Environment performance notes

Transcript-derived developer notes say Development can be slower because NoCode-X must show the current application state without fully recompiling. When promoting to Test, Acceptance, or Production, NoCode-X creates a version and applies optimizations.

Practical use:

- Do not judge final production performance only from Development preview.
- Still inspect app design: loading huge datasets, client-side DataTable paging, inefficient queries, or missing pagination can remain slow even in promoted environments.
- For performance demos or acceptance checks, test the relevant promoted environment when possible.

### DTAP release pattern

NoCode-X source materials describe a 4-stage release pipeline:

```text
Development -> Test -> Acceptance -> Production
```

Recommended release checklist:

- Test in lower environments before production.
- Create semantic version: `MAJOR.MINOR.PATCH`.
- Write version description.
- Promote sequentially.
- Have rollback plan.
- Monitor logs and user feedback after production deployment.

### Publishing, versioning and testing

Official docs sources: `https://docs.nocode-x.com/publishing/`, `https://docs.nocode-x.com/testing/`, and `https://docs.nocode-x.com/security/DTAP`.

Versions are specific application releases. Created versions can be promoted to environments or published on the Hub.

NoCode-X environments:

- Development: latest actively developed application; changes appear immediately.
- Test: development-team testing; not for real users.
- Acceptance: business/stakeholder testing; not for general users.
- Production: live version for end users.

Creating a version:

1. Click Publish.
2. Click Add version.
3. Name the version and describe changes.
4. Wait for NoCode-X to create/optimize the version.
5. Promote to Test, Acceptance, and/or Production.

Environment indicators documented:

- Green: production.
- Orange: acceptance.
- Yellow: test.
- Gray: not deployed anywhere.

Testing note: the Play button opens the application home page in Development, Test, Acceptance, or Production. Configure Home page before relying on Play/testing.

DTAP planning rules:

- Changes flow Development -> Test -> Acceptance -> Production.
- Do not reuse sensitive production data in lower environments.
- Generate synthetic test data when possible.
- Use roll-forward and roll-back versioning consciously.
- Treat version promotion as deployment, not just UI navigation.

## AppSumo LTD Tier 3 Resource Notes

The local materials state these Tier 3 limits:

| Resource | Limit |
|---|---:|
| Developers | 10 |
| CPU minutes | 5,000/month |
| Storage | 100 GB |
| Bandwidth | 100 GB/month |
| AI Credits | 50,000 one-time |

When the user is on this license, recommend:

- Pagination, caching and efficient filters.
- Avoiding frequent heavy jobs.
- Compressing images/assets.
- External storage for large files.
- Lazy loading and CDN/static asset optimization.
- BYOK or external AI providers where appropriate.
- Weekly/monthly usage reviews.

Do not assume the target workspace has this license unless the user says so or it is confirmed from platform/account data.
