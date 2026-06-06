# Plugin Investigation: Vanilla chatbot

Status: **no MCP-visible plugin-created objects observed**.

Observed through NoCode-X MCP fallback in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). Normal MCP tool channel temporarily returned `ClosedResourceError`, but `hermes mcp test nocodex-mcp` succeeded and the read-only registry fallback returned application data.

## Evidence

Current context:

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)

Searches returned no results for:

- `chatbot` in actions, schemas, APIs, jobs
- `chat` in actions, schemas, APIs, jobs
- `vanilla` in actions and schemas
- `message` in schemas

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

No `Vanilla chatbot`-specific objects are visible through MCP in the inspected application. If the rendered NoCode-X UI shows `Vanilla chatbot` as installed, treat it as likely empty, placeholder, failed-to-install, UI-only, or installed in a different application until verified in the browser UI or reinstalled in a clean app with before/after diffing.

Do not infer that chat UI, message storage, LLM actions, prompt configuration, chat logs, APIs, scheduled jobs, or model/provider configuration are available unless future evidence shows corresponding templates, elements, actions, schemas, APIs, or jobs.

## Expected Minimum Useful Objects

A useful chatbot plugin would normally create at least some of:

- A chat page/template with message input and message list elements.
- A message/log data schema, e.g. `ChatMessage`, `Conversation`, or `chatlogs`.
- An action to send a user prompt to an LLM/API.
- An action to persist user/assistant messages.
- Optional settings schema for model/provider/API key/system prompt.
- Optional public/private API endpoint for chat submission.

None of these were observed in this application snapshot.

## Recommended next checks

1. Confirm in the rendered NoCode-X UI whether `Vanilla chatbot` is installed in this exact app.
2. If installed, inspect whether it only creates nested UI objects that MCP does not expose.
3. Reinstall in a clean app and diff before/after with:
   - `list_all_apis`
   - `list_all_dataschemas`
   - `get_actions`
   - `list_all_templates`
   - `list_all_jobs`
   - `list_all_issues`
4. If still empty, report as plugin package issue or placeholder plugin.
