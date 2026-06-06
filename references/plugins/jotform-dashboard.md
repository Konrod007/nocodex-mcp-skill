# NoCode-X Plugin: Jotform Dashboard

Status: **investigated through MCP; no plugin-created application objects observed in the current app**.

Observed in workspace `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`), application `Unnamed Application` (`[REDACTED_ID]`).

## Purpose

Unknown from MCP. The plugin name suggests a Jotform dashboard, likely for displaying form submissions or embedded Jotform-related data, but no executable, schema, API, page, job, or dashboard objects were visible in the inspected application.

## MCP Context Checked

- Current workspace: `[REDACTED_WORKSPACE]`
- Current application: `Unnamed Application`
- Application ID: `[REDACTED_ID]`

## Installed/Observed APIs

- None returned by `list_all_apis`.
- Keyword API searches for `jotform` and `dashboard` returned no APIs.

## Installed/Observed Actions

- None returned by `get_actions`.
- Keyword action searches for `jotform`, `form`, and `dashboard` returned no actions.

## Installed/Observed Data Schemas

- None returned by `list_all_dataschemas`.
- Keyword data-schema searches for `jotform` and `form` returned no schemas.

## Installed/Observed Jobs

- None returned by `list_all_jobs`.
- Keyword job search for `jotform` returned no jobs.

## Installed/Observed Templates

Only baseline/default templates were returned:

- `Error: not authorized`
- `Error: unknown error`
- `Error: not found`
- `LottieFiles component`

No Jotform Dashboard-specific page/template was observed.

## Installed/Observed Folders

MCP returned only:

- `Plugins`
- `Root`

No nested `Jotform Dashboard` folder/package was visible through MCP. Note: NoCode-X UI may expose nested plugin packages that current MCP folder listing does not show, so rendered UI evidence would be needed to make a visual/sidebar claim.

## Issues

- `list_all_issues` returned no issues.

## Search Results

- `find_application("Jotform")`: no matching app.
- `find_application("Dashboard")`: no matching app.
- `search_actions("jotform")`: no matches.
- `search_actions("form")`: no matches.
- `search_actions("dashboard")`: no matches.
- `search_dataschemas("jotform")`: no matches.
- `search_dataschemas("form")`: no matches.
- `search_apis("jotform")`: no matches.
- `search_apis("dashboard")`: no matches.
- `find_jobs("jotform")`: no matches.

## Interpretation

If the `Jotform Dashboard` plugin was installed into this current application, then it appears to add **no MCP-visible NoCode-X objects**:

- no APIs;
- no actions;
- no data schemas;
- no jobs;
- no dashboard/page template;
- no plugin-specific validation issues.

This makes it similar to `DATA PIPELINE` in the current plugin audit: the package may be empty, placeholder/coming-soon, failed to install content, or not exposed through MCP object tools.

## Caveats

- MCP does not currently expose marketplace/plugin package metadata directly.
- This result proves only that no corresponding application objects were observed in the selected app through MCP.
- If the rendered UI shows `Jotform Dashboard` as installed, inspect the UI/sidebar or ask NoCode-X to clarify whether it is intended to create objects.

## Usefulness Assessment

Current observed usefulness: **near zero** as an app-building plugin, because there are no visible objects to configure, display, call, schedule, or reuse.

Recommended developer report if UI confirms installation:

- Plugin `Jotform Dashboard` appears to install without creating any visible actions, schemas, APIs, jobs, templates/pages, dashboard objects, or issues.
- Clarify whether it is intended as a placeholder/coming-soon plugin or whether package contents failed to install.
