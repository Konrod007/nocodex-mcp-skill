# NoCode-X Plugin: Typeform API

Status: **observed through MCP; partial Typeform workspace integration with setup/packaging issues and suspicious test artifact**.

Observed in workspace `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`), application `Unnamed Application` (`[REDACTED_ID]`).

## Purpose

Typeform API integration focused mostly on Typeform workspace operations.

Despite the broad name `Typeform API`, the installed object set is not a full Typeform API wrapper. It currently exposes workspace-related actions, includes schemas for form/theme creation, and has no observed NoCode-X APIs, jobs, or UI templates.

## Installed/Observed APIs

- None returned by `list_all_apis`.

## Installed/Observed Jobs

- None returned by `list_all_jobs`.

## Installed/Observed Templates

Only baseline/default templates were returned:

- `Error: not authorized`
- `Error: unknown error`
- `Error: not found`
- `LottieFiles component`

No Typeform-specific UI templates were observed.

## Installed/Observed Actions

### `Typeform: Create workspace`

- ID: `[REDACTED_ID]`
- Input signature observed: `main(REQUEST:CreateWorkspaceRequest)`
- Method observed: `POST`
- Auth observed in JS: `BEARER`
- Token source: `USER_SERVICE.payload.PERSONAL_ACCESS_TOKEN`
- Output schema reference: `CreateWorkspaceResponse` (`[REDACTED_ID]`)
- Uses `Typeform API configuration` through `_getfirstfiltereddatav3`.
- MCP-rendered endpoint fragment looked malformed/truncated: `TEXT:'https:let {RESPONSE...`.

### `Typeform: Retrieve workspaces`

- ID: `[REDACTED_ID]`
- Input signature observed: `main()`
- Method observed: `GET`
- Auth observed in JS: `BEARER`
- Token source: `USER_SERVICE.payload.PERSONAL_ACCESS_TOKEN`
- Output schema reference: `WorkspacesListResponse` (`[REDACTED_ID]`)
- Uses `Typeform API configuration` through `_getfirstfiltereddatav3`.
- MCP-rendered endpoint fragment looked malformed/truncated: `ENDPOINT:'https:this._logline...`.

### `Typeform: Retrieve account workspaces`

- ID: `[REDACTED_ID]`
- Input signature observed: `main(accountId:string)`
- Method observed: `GET`
- Auth observed in JS: `BEARER`
- Token source: `USER_SERVICE.payload.PERSONAL_ACCESS_TOKEN`
- Output schema reference: `WorkspacesListResponse` (`[REDACTED_ID]`)
- Uses `Typeform API configuration` through `_getfirstfiltereddatav3`.
- MCP-rendered endpoint fragment looked malformed/truncated: `TEXT:'https:let {RESPONSE...`.

### `Typeform: Create account workspace`

- ID: `[REDACTED_ID]`
- Input signature observed: `main(account_id:string, REQUEST:CreateWorkspaceRequest)`
- Method observed: `POST`
- Auth observed in JS: `BEARER`
- Token source: `USER_SERVICE.payload.PERSONAL_ACCESS_TOKEN`
- Output schema reference: `CreateWorkspaceResponse` (`[REDACTED_ID]`)
- Uses `Typeform API configuration` through `_getfirstfiltereddatav3`.
- MCP-rendered endpoint fragment looked malformed/truncated: `TEXT:'https:let {RESPONSE...`.

### `Typeform: Retrieve workspace`

- ID: `[REDACTED_ID]`
- Input signature observed: `main(workspaceId:string)`
- Method observed: `GET`
- Auth observed in JS: `BEARER`
- Token source: `USER_SERVICE.payload.PERSONAL_ACCESS_TOKEN`
- Output schema reference: `CreateWorkspaceResponse` (`[REDACTED_ID]`)
- Uses `Typeform API configuration` through `_getfirstfiltereddatav3`.
- MCP-rendered endpoint fragment looked malformed/truncated: `TEXT:'https:let {RESPONSE...`.

### `CreateThere TEST`

- ID: `[REDACTED_ID]`
- Suspicious test artifact.
- JS shape: starts, then calls `_action` referencing `action_d2e2c40c_aeee_4aeb_beb0_b8d2cbc3b236`.
- Global issue list includes `Required argument "Action" was empty` for this action.
- It is not returned by `search_actions("typeform")`, but it is present in `get_actions`, so it appears to be part of the installed application state.

## Installed/Observed Data Schemas

### `Typeform API configuration`

- ID: `[REDACTED_ID]`
- Fields:
  - `PERSONAL_ACCESS_TOKEN` — classified `SECRET`
- Required fields: none.

Security note: treat the personal access token as sensitive. Do not copy real values into docs/logs/chat.

### `CreateWorkspaceRequest`

- ID: `[REDACTED_ID]`
- Fields:
  - `name`
- Required fields: none.

### `CreateWorkspaceResponse`

- ID: `[REDACTED_ID]`
- Fields include:
  - `account_id`
  - `forms.count`
  - `forms.href`
  - `id`
  - `name`
  - `self.href`
  - `shared`
  - `members[]` with `email`, `name`, `role`

### `WorkspacesListResponse`

- ID: `[REDACTED_ID]`
- Fields include:
  - `items[]`
  - `page_count`
  - `total_items`
- `items[]` fields include:
  - `account_id`
  - `forms[]`
  - `shared`

Schema oddity:

- In the observed JSON schema, `items[].forms` is modeled as an array and some nested workspace fields appear under forms, which may not match Typeform's actual workspace-list response shape. Verify against Typeform docs before production use.

### `UpdateWorkspaceRequest`

- ID: `[REDACTED_ID]`
- Fields:
  - `items[]` with `op`, `path`, `value`
- Appears to model a JSON Patch request for workspace updates.
- No corresponding update workspace action was observed.

### `CreateFormRequest`

- ID: `[REDACTED_ID]`
- Description contains Typeform create form docs link:
  - `https://www.typeform.com/developers/create/reference/create-form/`
- Large schema covering Typeform form creation concepts:
  - `title`
  - `fields`
  - `hidden`
  - `logic`
  - `settings`
  - `thankyou_screens`
  - `theme`
  - `variables`
  - `welcome_screens`
  - CUI/settings/layout/validation/attachment structures
- No corresponding create form action was observed.

Schema issue:

- `fields` is modeled as an object, but Typeform create-form request normally expects `fields` as an array of field objects. Verify/correct before use.

### `CreateThemeRequest/Response`

- ID: `[REDACTED_ID]`
- Fields include:
  - `name`
  - `font`
  - `rounded_corners`
  - `has_transparent_button`
  - `background`
  - `colors`
  - `fields`
  - `screens`
  - `id`
  - `visibility`
- No corresponding theme create/retrieve/update action was observed.

## Capabilities Documented

Observed/expected capabilities from installed objects:

1. Store Typeform personal access token.
2. Create a workspace.
3. Retrieve all workspaces.
4. Retrieve workspaces for an account.
5. Create a workspace under an account.
6. Retrieve a workspace by ID.

Not observed in this plugin snapshot:

- create/retrieve/update/delete form action, despite `CreateFormRequest` schema;
- list forms;
- retrieve responses/submissions;
- webhooks;
- create/update theme action, despite `CreateThemeRequest/Response` schema;
- update/delete workspace action, despite `UpdateWorkspaceRequest` schema;
- OAuth flow;
- NoCode-X API endpoints;
- scheduled sync jobs;
- Typeform-specific UI templates/pages.

## Observed Issues / Validation Notes

Global `list_all_issues` returned 20 open BUG issues, all `MISSING_REQUIRED_FIELD`:

- missing `Text`: 9 occurrences;
- missing `Authentication method`: 5 occurrences;
- missing `Data format`: 5 occurrences;
- missing `Action`: 1 occurrence, linked to `CreateThere TEST`.

Per-action `list_action_issues` returned empty arrays for all six actions, while global `list_all_issues` linked issues to those action IDs. Prefer global issue list as source of truth.

Important interpretation:

- Missing auth/text/data-format fields may be normal post-install setup debt until credentials and action settings are configured.
- Missing `Text` aligns with malformed/truncated endpoint fragments in MCP-rendered JS.
- Missing `Action` plus the `CreateThere TEST` name strongly suggests a leftover test action or incomplete package content.

## JavaScript / Logic Notes

Observed JS pattern across Typeform HTTP actions:

- `_start()`
- `_getfirstfiltereddatav3` reads first `Typeform API configuration` record.
- `_replaceplaceholders` constructs endpoint for parameterized actions.
- `_httpcall` invokes Typeform endpoint with `AUTHENTICATION_METHOD:'BEARER'`.
- `API_XXX_KEY` is populated from `USER_SERVICE.payload.PERSONAL_ACCESS_TOKEN`.
- `_logline` logs the response.

Bearer token auth is appropriate for Typeform Personal Access Tokens in principle. However, action validation currently reports missing authentication method/data format/text, and MCP-rendered endpoint strings look malformed/truncated.

## Setup/Test Flow

1. Create/fill one `Typeform API configuration` record with a Typeform personal access token.
2. Treat the token as secret; do not paste real token values into docs/logs/chat.
3. Open `Typeform: Retrieve workspaces` in the action editor first because it is read-only.
4. Verify endpoint is a valid Typeform API URL, likely a `https://api.typeform.com/...` URL.
5. Confirm auth is Bearer token using `PERSONAL_ACCESS_TOKEN`.
6. Test `Retrieve workspaces`.
7. If read works, test `Retrieve workspace` with a controlled workspace ID.
8. Only after read actions work, test workspace creation actions.
9. Re-run `list_all_issues`; persistent missing `Text`, `Authentication method`, `Data format`, or `Action` should be reported.
10. Ignore or remove/fix `CreateThere TEST` before production use.

## Usefulness Assessment

Useful as a partial starting basis for Typeform workspace operations.

Not sufficient as a full Typeform integration because the major app-building workflows usually need forms, responses/submissions, and webhooks, which were not observed as actions.

For a practical Typeform integration, next missing actions would be:

- list forms;
- create form using `CreateFormRequest`;
- retrieve form;
- update/delete form;
- list responses/submissions;
- create/list/delete webhooks;
- create theme using `CreateThemeRequest/Response`;
- update workspace using `UpdateWorkspaceRequest`;
- pagination support for list endpoints.

## Developer Issue

A reportable issue should include:

- 20 open global BUG issues after installation;
- per-action issue calls return empty while global issues link to action IDs;
- MCP-rendered endpoint fragments appear malformed/truncated;
- suspicious `CreateThere TEST` action included in installed app state;
- schemas for Create Form, Create Theme, and Update Workspace exist without corresponding actions;
- `CreateFormRequest.fields` appears modeled as object rather than array;
- broad `Typeform API` name overstates observed coverage, which is mainly workspace actions.
