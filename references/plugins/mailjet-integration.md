# Plugin Investigation: Mailjet integration

Status: **no MCP-visible plugin-created objects observed**.

Observed through NoCode-X MCP in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`).

## Evidence

Current context:

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)

Searches for `mailjet` returned no results in:

- Actions
- Data schemas
- APIs
- Jobs

Full application inventory returned:

- APIs: none
- Data schemas: none
- Actions: none
- Jobs: none
- Issues: none
- Templates: only baseline/default templates:
  - `Error: not authorized`
  - `Error: unknown error`
  - `Error: not found`
  - `LottieFiles component`

## Interpretation

No Mailjet-specific objects are visible through MCP in the inspected application. If the rendered NoCode-X UI shows `Mailjet integration` as installed, treat it as likely empty, placeholder, failed-to-install, or UI-only until the plugin is reinstalled/inspected in the browser UI.

Do not infer that Mailjet sending, templates, contacts, campaigns, SMTP/API auth, webhooks, or inbound parsing are available unless future MCP/browser evidence shows corresponding actions, schemas, APIs, jobs, or templates.

## Recommended next checks

1. Confirm in rendered NoCode-X UI whether `Mailjet integration` is installed under Plugins.
2. If installed, inspect whether the plugin has a nested UI folder that MCP cannot expose.
3. If it is supposed to create objects, reinstall it in a clean app and diff before/after using:
   - `list_all_apis`
   - `list_all_dataschemas`
   - `get_actions`
   - `list_all_templates`
   - `list_all_jobs`
   - `list_all_issues`
4. Expected minimum useful Mailjet integration objects would be:
   - configuration schema for API key / secret key;
   - send email action;
   - optional template/send-template action;
   - response/error schemas;
   - possibly contact/list/campaign/webhook actions depending on the plugin promise.
