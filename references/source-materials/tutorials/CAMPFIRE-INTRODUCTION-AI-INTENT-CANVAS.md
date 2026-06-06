# Campfire 02/03: Introduction To AI Intent Canvas

Source: user-provided transcript excerpt of `Campfire 02/03 - New features & bugfixed + Introduction to AI Intent canvas`, starting at timestamp `[19:31]`.

Video URL: `https://www.youtube.com/watch?v=KBZlC2r5jMY`

Treat this as transcript-derived platform knowledge. The demonstrated AI Intent Canvas and related AI agent capabilities are described as heavily in development in the transcript; verify current production availability before making product claims.

## Why This Video Matters

This campfire explains the product rationale behind AI Intent Canvas:

- code review does not scale when AI can generate thousands of lines of code per day;
- UI-only validation after large generated changes is too slow and too late;
- NoCode-X wants a non-code surface for comparing intended behavior against actual app structure;
- Intent Canvas is framed as the replacement/evolution of old Rocket Mode;
- it captures intent first, then later validates realization against that intent.

## 1. Problem: AI Code Acceptance Is Not Enough

The transcript contrasts two AI app-generator patterns.

Pattern 1: visual preview/testing loop:

- AI generates a large feature;
- user clicks through the app only after substantial work is done;
- failures are discovered late through manual UI testing;
- this is considered an inefficient way to build software.

Pattern 2: code-diff acceptance loop:

- user asks a chatbox to change code;
- generator asks whether to accept/reject the code;
- users often do not read the generated code and simply accept;
- if AI generates 10,000 lines/day, reading all code is unrealistic.

NoCode-X direction:

- users need a way to check whether generated reality matches the user's intent;
- the check should not require reading all code or manually clicking every flow.

## 2. Intent Canvas Purpose

Intent Canvas is described as a place to:

- describe what the application or automation is intended to be;
- compare intended behavior against current reality;
- validate both human-created and AI-created app structures;
- create guardrails/context for later AI generation.

Important framing:

- intent is not just a prompt;
- it is stored application context;
- AI uses it in later stages when creating pages, schemas, actions, jobs, APIs, and other artifacts.

## 3. Three Levels Of Intent Canvas

The transcript says the Intent Canvas has three levels.

### Level 1: Foundations / Application-Level Intent

Includes:

- application intent;
- vision statement;
- mission statement;
- functional/non-functional mission intents;
- look-and-feel intent;
- design-system preview and editable design parameters.

Example application intent prompt:

```text
This application will generate blog posts and social media posts based on an idea database.
It will have a human-in-the-loop flow where a marketeer checks and validates generated posts.
```

Level 1 use:

- capture high-level product purpose;
- define mission/functionality constraints;
- define visual direction;
- generate or refine design system before building.

### Level 2: Dynamics / Personas And Journeys

Includes:

- personas;
- customer/user journeys;
- actor descriptions;
- journey steps and UI/UX expectations.

Example persona prompt:

```text
Generate the persona 'marketeer' for this application.
This persona is the main actor for two flows:
adding/editing/viewing ideas and validating/publishing a new post.
```

Level 2 use:

- describe who uses the app;
- connect actors to journeys;
- give AI demographic/contextual UI/UX constraints.

### Level 3: Realization / Validation Graph

Includes current app reality:

- folders;
- design system;
- plugins such as default Vanilla error pages;
- pages/templates;
- data schemas;
- actions;
- APIs;
- jobs;
- edges showing relationships between artifacts.

Level 3 use:

- validate whether generated/human-created application structure honors the intent;
- inspect what the AI actually created;
- understand app flows without reading large generated code.

## 4. AI Enhancement Of Intent

Application intent and look-and-feel intent can be enhanced with AI.

Observed flow:

- user enters a short intent;
- clicks edit/enhance with AI;
- AI expands it into richer intent text;
- user can tweak the enhanced result before saving.

Example generated visual direction includes terms such as:

- modern;
- creative;
- energetic;
- flow state;
- human-centered;
- confident;
- electric teal;
- glassmorphism/fluid UI style language.

Practical use:

- use AI enhancement to get a richer draft;
- do not accept blindly;
- manually edit wording so it matches exact product intent;
- treat saved intent as guardrails for later generation.

## 5. Look-And-Feel And Design System Preview

The transcript shows a look-and-feel screen with:

- typography preview;
- design-system preview;
- visible app-preview changes when colors are changed;
- manual control over design variables.

Important caveat:

- at the time of transcript, AI was not yet created to manipulate every design-system detail automatically.

Practical use:

- verify visual intent through preview before generation;
- use design-system preview to catch wrong colors/typography early;
- preserve distinction between narrative look-and-feel intent and concrete design-system variables.

## 6. Personas As Actors Plus Demographic Context

The transcript clarifies that personas are similar to actors in use-case analysis, but richer.

Persona role:

- actor for customer journeys;
- demographic/contextual description of a typical actor;
- source of UI/UX constraints.

Examples:

- accountant vs teenager implies different UI/UX;
- age group, motivations, capabilities, and interaction requirements matter.

Practical use:

- treat personas as actor + UX context;
- use personas to steer navigation density, language, accessibility, and interaction model;
- when auditing generated apps, check whether UI/UX matches the declared personas.

## 7. Customer Journey Generation

The transcript shows AI generating a customer journey for the marketeer.

Observed concepts:

- dashboard opening;
- validation dashboard;
- side-by-side review view;
- generated graph/flow representation;
- manual editing of journey content.

Caveats:

- graph readability still needed work;
- graph refreshed while AI was still generating;
- performance/cost for journey generation still needed optimization.

Practical use:

- generated journeys are drafts, not final truth;
- manually edit steps and review flow clarity;
- use journeys as intent context for page/action generation.

## 8. New AI Agent vs Old Rocket Mode

The new AI is described as different from old Rocket Mode.

Old Rocket Mode:

- wizard-like;
- guided step-by-step;
- took user by the hand.

New AI Intent Canvas agent:

- actual chatbot with memory;
- responds to user questions;
- can generate/edit many app objects;
- delegates tasks to an intent agent;
- uses created intents as context.

Practical use:

- prompts can be more conversational;
- still specify exact targets for reliable generation;
- expect task lists/progress while agent works.

## 9. AI Agent Tool Scope Mentioned

The transcript lists current or intended tool capabilities of the AI agent:

- extract information from created intents;
- create folders;
- edit folders;
- edit design system;
- create/edit/delete/update data schemas;
- create/edit/update APIs;
- schedule jobs;
- create/edit pages;
- create/edit parts of pages;
- create/edit actions.

Caveat:

- some features still required fixes before release.

Practical use:

- when preparing builder prompts, name target artifact types explicitly;
- verify final app reality in Level 3 / realization graph;
- distinguish transcript-stated tool potential from live MCP/tool availability.

## 10. Example Generated Content Management App

The demo application idea:

- generate blog posts and social media posts from an idea database;
- include a human-in-the-loop marketer validation flow;
- manage ideas, drafts, validation, publishing.

Generated/observed artifacts include:

- `ideas_management` folder;
- `content_ideas` database;
- tags database / many-to-many relationship between content ideas and tags;
- parent layout template such as `ideas_layout`;
- dashboard/detail/search/capture pipeline planning.

Practical use:

- use this as a pattern for human-reviewed AI content pipelines;
- model ideas, generated drafts, tags, review states, and publishing actions explicitly;
- verify data schemas and relationships rather than relying on generated UI alone.

## 11. Realization Graph Edges Explain Behavior

The transcript explains that action nodes can show lines to data schemas.

Examples:

- action fetches all ideas from `content_ideas`;
- line label says the action fetches from a database;
- other labels can show rewriting/writing to a database.

Value:

- gives a quick glance of what generated actions do;
- more useful than reading thousands of lines of code;
- supports intent-vs-reality validation.

Practical use:

- inspect edges after AI generation;
- check whether every journey step has corresponding page/action/data edges;
- check whether actions read/write the intended schemas;
- use edge labels as first-pass behavior review, then test critical flows.

## 12. Observability Feedback Loop

The transcript says NoCode-X is heavily focusing on observability in 2026.

Observed/planned observability inputs:

- logs;
- audit logs;
- issues;
- future issue types;
- production unexpected errors.

Planned AI feedback loop:

- static/analysis detects possible null pointer exception;
- feed issue back to AI;
- AI fixes the generated action;
- production error occurs;
- feed production error/logs back to AI;
- AI creates a fix so the error does not happen again.

Practical use:

- when asking AI to debug, include logs/issues/audit evidence;
- treat observability as part of generation quality, not only monitoring;
- verify fixes with tests/log checks, not just AI summaries.

## 13. External LLMs, MCP, And Bring-Your-Own-Key

The transcript discusses using outside LLMs and external agent/code workflows.

MCP direction:

- NoCode-X AI tools can be exposed through an MCP server;
- external workflows such as Claude Code-like agents could call NoCode-X tools;
- example: build frontend in native React while backend is in NoCode-X.

Bring-your-own-key direction:

- NoCode-X has long wanted to allow user-provided AI API keys;
- the new architecture uses fewer AI models than old Rocket Mode;
- this should make BYO key more feasible.

Caveat:

- described as future/in-progress; verify current support.

Practical use:

- for hybrid projects, plan MCP boundaries explicitly;
- verify exact MCP tool list and authentication before relying on external agents;
- do not assume BYO key is available unless confirmed in the current environment.

## 14. AI Agents Inside Workflows And Tool Calling

The transcript previews AI agents that can run processes in NoCode-X.

Current-at-transcript capability:

- workflows can call AI, get a return, and use the result;
- chains of AI calls are possible.

Missing/in-progress capability:

- true tool-calling agent loop was not yet implemented;
- team waited because older models were not strong enough at tool calling;
- newer models were described as making tool calling viable.

Planned capability:

- real agent uses tools;
- loops through tool calls;
- outputs final result;
- can power an end-to-end AI content generation app.

Practical use:

- distinguish simple AI API-call workflows from true tool-calling agents;
- when auditing agentic apps, ask whether tools are actually invoked or whether it is only sequential completions;
- verify tool-call traces once available.

## 15. Product Communication And Release Caveats

The transcript notes:

- latest improvements page was not being updated at that moment;
- campfires were used to communicate active development;
- developer add/remove fix was expected sooner than Intent Canvas;
- Intent Canvas was not blocking unrelated bugfix releases.

Practical use:

- do not rely only on old update pages for current platform status;
- verify via current product/docs/support channels when timing matters.

## Skill Guidance Updates From This Source

This transcript supports these reusable patterns:

- Intent Canvas is an intent-vs-reality validation surface, not just a planning document.
- Use Level 1 for app/mission/look-and-feel/design intent.
- Use Level 2 for personas and customer journeys.
- Use Level 3 for realization inventory and graph validation.
- Use AI enhancement as a draft generator, then manually correct stored intent.
- Treat personas as actors plus demographic/UX constraints.
- Review generated graph edges instead of relying on code acceptance.
- Feed observability signals back into AI debugging and repair prompts.
- Distinguish simple AI-completion workflows from true tool-calling agents.
- Mark MCP/BYO-key/agent-tool-calling features as roadmap unless verified live.

## Verification Checklist For Live Apps

When applying this source to a current NoCode-X app, verify:

- whether Intent Canvas is available in the target environment;
- whether it has three levels or current equivalent structure;
- whether application/mission/look-and-feel/design intents are editable and AI-enhanceable;
- whether design-system preview and manual color/typography controls exist;
- whether personas and journeys can be AI-generated and manually edited;
- whether generated journeys are readable and stable during generation;
- whether Level 3 shows folders, plugins, design system, pages, schemas, actions, APIs, and jobs;
- whether default `Vanilla error pages` plugin appears as baseline in new apps;
- whether graph edges show page/action/data relationships with labels;
- whether generated action behavior can be inferred from graph edge labels;
- whether logs/audit logs/issues can be fed back to AI or are only manually visible;
- whether production errors can trigger or support AI repair workflows;
- whether NoCode-X MCP server exposes the stated tools;
- whether BYO AI API key is supported;
- whether true tool-calling agents exist or only sequential AI calls are available.
