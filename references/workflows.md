# NoCode-X MCP Workflows

## Application Architecture Review

Use when the user asks what an app contains or whether it is well structured.

1. Confirm context with `get_current_workspace` and `get_current_application`.
2. Read `get_application_info`.
3. Read primary inventory:
   - `list_all_apis`
   - `list_all_dataschemas`
   - `get_actions`
   - `list_all_jobs`
   - `list_all_templates`
   - `list_all_issues`
4. Drill into important objects with `get_api`, `get_dataschema`, `get_action_javascript`, and `get_page_html`.
5. Summarize architecture by domain: data, APIs, UI/templates, actions, jobs, issues, risks.
6. For each major claim, cite the MCP source used (for example: `get_application_info`, `list_all_dataschemas`, `list_all_templates`, `list_all_issues`).
7. Separate `Confirmed`, `Likely`, and `Unknown` findings. Do not fill unknown gaps with assumptions.

## Senior Product / UX / Engineering Audit

Use when the user asks for a senior-level review, product critique, UX/UI improvement plan, or implementation roadmap.

1. Confirm workspace/application.
2. Gather the architecture inventory from the Application Architecture Review workflow.
3. Inspect page/template names, template parameters, element lists, and page HTML where available.
4. Inspect actions attached to core elements when auditing a specific user flow.
5. Check issues and, if the environment is known, recent logs.
6. Output findings in this shape:
   - **Confirmed evidence**: what MCP actually returned.
   - **Product purpose**: only from app metadata, schemas, pages, actions, and APIs.
   - **Current flow map**: pages/dialogs/actions in observed order.
   - **Gaps/risks**: missing APIs/jobs/actions, open issues, incomplete descriptions, missing logs, or unknown rendered UI.
   - **Recommendations**: problem -> impact -> recommendation -> engineering notes -> priority/effort.
   - **Questions**: only the minimum missing data needed for further analysis.
7. If rendered UI was not inspected in browser, explicitly state that UI visual quality, responsiveness, console errors, and accessibility are `Unknown`.

## Platform Guidance Or App-Building Advice

Use when the user asks how to build, improve, or structure a NoCode-X application rather than only inspect a specific current app.

1. Read `references/platform-playbook.md`.
2. If the question targets a specific existing app, also run the Application Architecture Review workflow and cite MCP evidence.
3. Separate platform best practices from app-specific facts:
   - **Platform note**: comes from local NoCode-X materials.
   - **Confirmed in app**: observed through MCP/browser/logs.
   - **Unknown**: not verified in current app.
4. Prefer practical checklists: Rocket Mode prompt structure, UI/template hierarchy, data schema, actions, jobs, RBAC, APIs, tests, DTAP release.
5. Do not claim license limits, native integrations, or rendered UI behavior unless verified or explicitly provided by the user.

## Broken Button Or Page Debugging

Use when a page interaction, button, form, or UI flow fails.

1. Identify or find the template with `list_all_templates`.
2. Inspect the page with `get_page_html`.
3. Inspect elements with `list_template_elements`.
4. Use `get_attached_actions_on_element` with `templateId` and `elementCode`.
5. For each attached action:
   - read `get_action_javascript`;
   - read `list_action_issues`;
   - read `read_action_logs` for the target environment.
6. Read `read_page_logs` for the template and environment.
7. Report the trace: page -> element -> action -> JavaScript -> logs/issues.

## API Debugging

Use when an endpoint fails, returns wrong data, or is misconfigured.

1. Locate the API with `search_apis` or `list_all_apis`.
2. Inspect details with `get_api`.
3. Identify related schemas with `list_all_dataschemas` or `search_dataschemas`.
4. Inspect related schema with `get_dataschema`.
5. Search actions that may call the API with `search_actions`.
6. Read `read_logs` for the target environment.
7. Report likely cause and what to inspect or change next.

## Action Or Workflow Debugging

Use when backend logic, workflow execution, or an action fails.

1. Locate action with `search_actions` or `get_actions`.
2. Inspect code with `get_action_javascript`.
3. Check known issues with `list_action_issues`.
4. Read recent logs with `read_action_logs`.
5. Identify dependencies: APIs, schemas, pages, jobs.
6. Provide a concise diagnosis and evidence.

## Data Model Review

Use when the user asks about database structure, missing fields, or entity design.

1. Read `list_all_dataschemas`.
2. Search for named entities with `search_dataschemas`.
3. Inspect target schemas with `get_dataschema`.
4. Cross-check APIs with `list_all_apis` / `get_api`.
5. Cross-check actions with `search_actions` / `get_action_javascript`.
6. Summarize fields, relationships, validation risks, and likely missing data.

## Pre-Builder Planning

Use before asking NoCode-X builder to implement a change.

1. Confirm context.
2. Gather current facts with read-only tools.
3. Identify exact target objects by ID/name.
4. Draft a builder prompt that names:
   - target APIs;
   - target schemas;
   - target templates/elements;
   - target actions/jobs;
   - known logs/issues;
   - constraints and non-goals.
5. Ask for user confirmation if the change was not already explicitly requested.
6. Call `request_building_action`.
7. Poll with `check_building_status`.

## Platform Source Ingestion / Skill Update

Use when the user provides local NoCode-X documentation/tutorial materials and asks to improve this skill.

1. Read `references/platform-source-ingestion.md`.
2. Distill class-level platform guidance; do not create one-session narrow skills.
3. Prefer updating `references/platform-playbook.md` or another existing umbrella reference.
4. Keep app-specific facts separate from platform notes and preserve the MCP-first evidence rules.
5. Add SKILL.md/workflow pointers for any new support file.

## Documentation Generation

Use when asked to document or explain an app.

1. Read app info, APIs, schemas, actions, jobs, templates, and issues.
2. Drill into core APIs/actions/schemas.
3. Output documentation:
   - overview;
   - data model;
   - API catalog;
   - action/workflow catalog;
   - page/template catalog;
   - scheduled jobs;
   - known issues and logs;
   - suggested next improvements.
