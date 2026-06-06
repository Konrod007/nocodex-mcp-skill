# NoCode-X Plugin: DATA PIPELINE

Status: **investigated through MCP; no plugin-created application objects observed in the current app**.

Observed in workspace `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`), application `Unnamed Application` (`[REDACTED_ID]`).

## Purpose

Unknown from MCP. The plugin name suggests data-pipeline functionality, but no executable or structural objects were visible in the inspected application.

## MCP Context Checked

- Current workspace: `[REDACTED_WORKSPACE]`
- Current application: `Unnamed Application`
- Application ID: `[REDACTED_ID]`

## Installed/Observed APIs

- None returned by `list_all_apis`.
- Keyword API search for `pipeline` returned no APIs.

## Installed/Observed Actions

- None returned by `get_actions`.
- Keyword action search for `pipeline` returned no actions.

## Installed/Observed Data Schemas

- None returned by `list_all_dataschemas`.
- Keyword data-schema search for `pipeline` returned no schemas.

## Installed/Observed Jobs

- None returned by `list_all_jobs`.
- Keyword job search for `pipeline` returned no jobs.

## Installed/Observed Templates

Only baseline/default templates were returned:

- `Error: not authorized`
- `Error: unknown error`
- `Error: not found`
- `LottieFiles component`

No DATA PIPELINE-specific UI templates/pages were observed.

## Installed/Observed Folders

MCP returned only:

- `Plugins`
- `Root`

No nested DATA PIPELINE package/folder was visible through MCP. Note: NoCode-X UI may expose nested plugin packages that current MCP folder listing does not show, so rendered UI evidence would be needed to make a visual/sidebar claim.

## Issues

- `list_all_issues` returned no issues.

## Search Results

- `find_application("DATA PIPELINE")`: no matching app.
- `search_actions("pipeline")`: no matches.
- `search_dataschemas("pipeline")`: no matches.
- `search_apis("pipeline")`: no matches.
- `find_jobs("pipeline")`: no matches.

## Interpretation

If the DATA PIPELINE plugin was installed into this current application, then it appears to add **no MCP-visible NoCode-X objects**:

- no APIs;
- no data schemas;
- no actions;
- no jobs;
- no plugin-specific templates;
- no validation issues.

This differs from partially populated plugins such as Trello or Dropbox, which add actions/schemas even when setup is incomplete.

## Caveats

- MCP does not currently expose marketplace/plugin package metadata directly.
- The result proves only that no corresponding application objects were observed in the selected app through MCP.
- If the UI shows DATA PIPELINE as installed, then this is likely an empty package, a marketplace shell, or a plugin whose contents are not surfaced through the current MCP object tools.

## Usefulness Assessment

Current observed usefulness: **near zero** as an app-building plugin, because there are no visible objects to configure, call, schedule, or reuse.

Recommended developer report if UI confirms installation:

- Plugin `DATA PIPELINE` appears to install without creating any visible actions, schemas, APIs, jobs, templates, or issues.
- Clarify whether it is intended as a placeholder/coming-soon plugin or whether package contents failed to install.
