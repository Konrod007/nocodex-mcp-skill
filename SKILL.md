---
name: nocodex-mcp
description: "Use when working with NoCode-X applications through MCP: inspecting workspaces/apps, APIs, data schemas, actions, JavaScript logic, templates/pages, logs, jobs, issues, media library, and builder tasks; also use for debugging, app review, documentation, and preparing precise NoCode-X builder requests."
version: 1.1.0
author: NoCode-X / Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [nocode-x, nocodex, mcp, app-audit, no-code, debugging]
    related_skills: [native-mcp, hermes-agent]
---

# NoCode-X MCP

Use this skill as a senior NoCode-X application analyst. Prefer direct MCP facts over guesses and use the builder only after collecting enough context.

In Hermes, MCP tool names are registered with the server prefix. For a server named `nocodex-mcp`, tool calls appear as `mcp_nocodex_mcp_<tool_name>` even though this skill and its references use the short NoCode-X names like `get_current_application`.

## When To Use

- The user asks to inspect, debug, document, or review a NoCode-X app.
- The user provides a NoCode-X workspace/application URL or names a workspace/app.
- The user asks for a grounded product/UX/engineering audit of a NoCode-X application.
- The user asks to prepare a precise builder request for NoCode-X.
- The user asks for NoCode-X platform guidance: Rocket Mode prompts, UI/templates, data formats, actions, State/Scope, APIs, jobs, RBAC, plugins, testing, DTAP, or AppSumo LTD limits.
- The user asks whether a NoCode-X app has APIs, schemas, pages, actions, logs, jobs, or open issues.
- The user asks whether a UI-only area such as `Plugins API` is visible or configured.

Do not use this skill to speculate about UI that has not been inspected. If the rendered browser UI, environment name, reproduction steps, or target workspace/app are missing and cannot be discovered with MCP, ask the user for that missing input. Distinguish MCP facts from rendered-UI facts: for example, `list_all_apis: []` means the MCP application API list is empty, not that a sidebar section such as `Plugins API` is absent unless the UI has also been inspected.

## Core Operating Rules

1. Confirm context before analysis:
   - `get_current_workspace`
   - `get_current_application`
2. If context is wrong, find and switch:
   - workspace: `find_workspace` -> `switch_workspace`
   - application: `find_application` -> `switch_application`
3. Read before write:
   - inspect app facts with list/get/search/log tools first;
   - explain what is known and what is uncertain;
   - use `request_building_action` only after the target objects and likely impact are clear.
4. Treat builder requests as potentially mutating. If the user has not explicitly asked for a change, use read-only tools only.
5. After `request_building_action`, always call `check_building_status` until a terminal status is reached.
6. Do not read, expose, or summarize auth-token files such as `.env`, `mcp_auth.json`, access tokens, or refresh tokens.
7. If facts are unavailable from MCP, say `Unknown` and ask for the minimum missing data instead of extrapolating.
8. When the user works on real/private NoCode-X applications, product ideas, or migrations, do **not** add project names, business descriptions, URLs, app IDs, or implementation specifics to shared skill references/catalogs. Save only class-level methods/patterns. If a plan must be persisted, write it inside the user's project workspace (for example `.hermes/plans/...`) rather than under this skill.
9. When evaluating NoCode-X as a platform, distinguish between **platform capability** and **quality of available examples/plugins**. Weak, placeholder, broken, or deprecated examples are evidence about the example library, not proof that the platform itself is unsuitable. Frame conclusions around observed evidence and unknowns.

## Reference Navigation

- For exact tool arguments and usage: read `references/tools-reference.md`.
- For common operating recipes: read `references/workflows.md`.
- For NoCode-X platform concepts, Rocket Mode prompts, UI/data/action/job/security/testing patterns, read `references/platform-playbook.md`.
- For official NoCode-X documentation notes useful for platform understanding and application planning, read `references/official-docs-planning.md`.
- For preparing this skill or related NoCode-X research notes as a public English GitHub repository, including transcript-source notices, redaction, repo metadata, checks, commit, and push handling, read `references/public-github-release.md`.
- For the local source folder, tutorial/video indexes, and ingestion notes, read `references/platform-tutorial-sources.md`.

- For planning existing-service migration, bridge/control-plane designs, or durable long-running jobs before NoCode-X sync, read `references/bridge-durable-job-planning.md`.
- For planning production B2B/B2C SaaS account, organization, team, billing, roles, portal, and tenant-isolation structure inside a NoCode-X application, read `references/production-saas-template.md`.
- For evaluating the practical value and limits of GitHub/GitLab/repository-connected plugins, read `references/git-connected-plugin-value.md`.
- For plugin/platform defects that should be reported to NoCode-X developers, read `references/plugin-developer-issues.md`.
- If normal MCP tool calls fail but `hermes mcp test nocodex-mcp` succeeds, use `references/mcp-transport-fallback.md` for the direct registry-handler fallback pattern.
- For ingesting local NoCode-X docs/tutorials into durable skill knowledge, read `references/platform-source-ingestion.md`.
- For troubleshooting recipes: read `references/debugging-playbook.md`.
- For safety rules and known limitations: read `references/safety-and-limitations.md`.
- For future product/API gaps: read `references/vendor-roadmap.md`.
- For installing/updating this local skill in Hermes: read `references/hermes-installation.md`.

## Default Workflow

For app analysis:

1. Confirm current workspace/application.
2. Gather app structure:
   - `get_application_info`
   - `list_all_apis`
   - `list_all_dataschemas`
   - `get_actions`
   - `list_all_templates`
   - `list_all_jobs`
   - `list_all_issues`
3. Drill down with `get_api`, `get_dataschema`, `get_action_javascript`, `get_page_html`, and logs as needed.
4. Answer with evidence: name the API/schema/action/page/log source behind each major finding.
5. If the user asks about `Plugins API` or another visible UI section, verify both layers when possible:
   - MCP layer: confirm workspace/application and call the relevant list/get tools, but avoid over-interpreting empty lists.
   - UI layer: inspect the rendered app in an authenticated browser session or ask for a screenshot/video when browser auth is unavailable.
   - Report the two results separately (`MCP says...`, `UI visibility...`) so an empty MCP result is not mistaken for visual absence.

For debugging:

1. Identify the failing surface: page, action, API, schema, job, or general app.
2. Follow the relevant recipe in `debugging-playbook.md`.
3. Present a concise diagnosis, the evidence trail, and the safest next step.

For builder handoff:

1. Gather facts first.
2. Prepare a precise prompt naming target APIs, schemas, templates, actions, jobs, and known errors.
3. State expected impact and risks before invoking `request_building_action`.
4. Poll with `check_building_status`.
