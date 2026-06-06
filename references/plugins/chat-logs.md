# NoCode-X Plugin: Chat Logs

Status: **observed through MCP; appears useful but test/beta-quality**.

Observed after user installed `Chat Logs` in workspace `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`), application `Unnamed Application` (`[REDACTED_ID]`).

User note: plugin is marked as test; user is not sure it is fully working.

## Purpose

The plugin appears to provide a small chat-log viewer/scaffold:

- a `chatlogs` data schema for storing prompt/response/session/instruction records;
- a reusable `Chat log record` template for rendering one log entry;
- actions to list logs, render a log record, and hide empty instruction blocks.

This can be useful as a reference pattern for building an internal LLM/chat audit UI in NoCode-X, but it should not be treated as production-ready until issues are resolved.

## Installed/Observed APIs

- None returned by `list_all_apis`.
- Keyword API searches for `Chat`, `Log`, `Logs`, `Message`, and `Conversation` returned no APIs.

## Installed/Observed Jobs

- None returned by `list_all_jobs`.

## Installed/Observed Data Schemas

### `chatlogs`

- ID: `[REDACTED_ID]`
- Fields:
  - `USER_REQUEST`: string or null
  - `AI_RESPONSE`: string or null
  - `SESSION_ID`: string or null
  - `INSTRUCTION`: string or null
- Required fields: none.

### Interpretation

The schema is minimal but useful for storing basic LLM/chat traces:

- what the user asked;
- what the AI returned;
- which session/conversation it belongs to;
- optional instructions/system context.

For production audit logs, additional fields would likely be needed:

- created timestamp;
- user/account/tenant ID;
- model/provider;
- status/error;
- token/cost metadata;
- tool-call trace or source document references;
- privacy/retention classification.

## Installed/Observed Templates

### `Chat log record`

- ID: `[REDACTED_ID]`
- Elements returned by MCP:
  - `VERTICAL_LIST_CODE`
  - `HORIZONTAL_LIST_CODE_INSTRUCTIONS`
  - `HORIZONTAL_LIST_CODE_AI`
  - `TEXT_PART_REQUEST`
  - `TEXT_PART_RESPONSE`
  - `TEMPLATE_CODE`
  - `TITLE_CODE`
  - duplicate `TEMPLATE_CODE` entry in MCP element list
- Parameters:
  - `DATE`
  - `REQUEST`
  - `RESPONSE`
  - `CONV_ID` with default `'No Conversation ID'`
  - `INSTRUCTIONS` with default `'No instructions'`

### Baseline Template Duplication

Before this plugin, the app had baseline/default templates only:

- `Error: not authorized`
- `Error: unknown error`
- `Error: not found`
- `LottieFiles component`

After installing `Chat Logs`, MCP returned additional duplicated baseline-style templates:

- `LottieFiles component_1`
- `Error: unknown error_1`
- `Error: not authorized_1`
- `Error: not found_1`

This looks like plugin installation may duplicate the standard vanilla error-page scaffold. Treat as suspicious and reportable unless the UI shows an intentional package-local copy.

## Installed/Observed Actions

### `Hide empty instructions`

- ID: `[REDACTED_ID]`
- Purpose: reads the instructions text field and hides a UI part if instructions are empty/default.
- Observed JS operations:
  - `_getansweroftextfield`
  - `_hidepartv2`
  - `_logline`
- Action-level issue call returned no issues.

### `Display chat log record`

- ID: `[REDACTED_ID]`
- Purpose: render one chat log entry into a vertical list using the `Chat log record` template.
- Observed JS operations:
  - `_formatDate`
  - `_createstringvariable`
  - `_addtemplatecomponenttolistv2`
- Action-level issue call returned no issues, but global issues include deprecated method problems linked to this action:
  - `DEPRECATED_METHOD_USED`: `addtemplatecomponenttolistv2`

### `Show Logs`

- ID: `[REDACTED_ID]`
- Purpose: fetch chat log records and render them, likely by invoking `Display chat log record` for each entry.
- Observed JS operations:
  - `_createdate`
  - `_getfiltereddatav3`
  - `_foreach`
  - `_addtemplatecomponenttolistv2`
  - `_logline`
- Action-level issue call returned no issues, but global issues include several problems linked to this action:
  - `UNEXISTING_DATA_FORMAT_USED`: references `[REDACTED_ID]` despite `chatlogs` schema existing with that ID.
  - `UNEXISTING_DATA_FORMAT_USED`: references non-existing data format `[REDACTED_ID]`.
  - `DEPRECATED_METHOD_USED`: `getfiltereddatav3`.
  - `DEPRECATED_METHOD_USED`: `createdate`.

## Observed Issues

Global `list_all_issues` returned 8 open BUG issues after installation:

- `UNEXISTING_DATA_FORMAT_USED`: `Fetch a list of data records` references `[REDACTED_ID]` even though `chatlogs` exists with this ID.
- `UNEXISTING_DATA_FORMAT_USED`: `Fetch a list of data records` references missing `[REDACTED_ID]`.
- `DEPRECATED_METHOD_USED`: `getfiltereddatav3`.
- `DEPRECATED_METHOD_USED`: `createdate`.
- `DEPRECATED_METHOD_USED`: `addtemplatecomponenttolistv2`.
- Some deprecated-method issues are duplicated in the issue list.

Important MCP caveat: per-action `list_action_issues` returned empty arrays for the actions, while global `list_all_issues` linked issues to those same action IDs. Prefer global issue list as source of truth.

## Usefulness Assessment

Useful as:

- a scaffold/reference for displaying chat logs;
- a minimal data model for LLM prompt/response history;
- a template/action example for rendering records into UI lists.

Not production-ready as-is because:

- one action references a genuinely missing data format ID;
- another issue claims the visible `chatlogs` schema is non-existing;
- several methods are deprecated;
- baseline error templates appear duplicated;
- no jobs/APIs are created for ingestion or persistence of chat logs.

## Recommended Next Steps

1. In the NoCode-X UI, verify whether `Show Logs` is attached to a page or button and whether it runs.
2. If it fails, inspect the `Fetch a list of data records` invocation and rebind it to the visible `chatlogs` schema.
3. Identify what `[REDACTED_ID]` was supposed to reference; replace/remove if stale.
4. Replace deprecated methods with current equivalents:
   - `getfiltereddatav3`
   - `createdate`
   - `addtemplatecomponenttolistv2`
5. Decide whether duplicated vanilla error templates should be removed from the app or reported as a packaging issue.
6. If useful, extend `chatlogs` with timestamp/user/model/status fields before using it for real audit logs.

## Developer Issue

A reportable issue has been recorded in `references/plugin-developer-issues.md` covering:

- broken/stale data-format references;
- deprecated methods;
- duplicated vanilla error templates;
- inconsistent issue attribution between global and per-action issue APIs.
