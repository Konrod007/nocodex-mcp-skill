# NoCode-X Plugin: Atlassian Trello API

Status: **observed through MCP; partial Trello board/list integration with setup debt and packaging issues**.

Observed in workspace `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`), application `Unnamed Application` (`[REDACTED_ID]`).

## Purpose

Trello integration focused on board-level operations and creating lists on boards.

Despite the broad name `Atlassian Trello API`, the installed object set is **not a full Trello API wrapper**. It currently covers only:

- create board;
- get board by ID;
- delete board;
- create list on board.

No card/member/label/checklist/comment/attachment/webhook operations were observed.

## Installed/Observed APIs

- None returned by `list_all_apis`.
- Keyword API searches for `Trello`, `Atlassian`, `Board`, `Card`, `List`, `Member`, `Label` returned no APIs.

## Installed/Observed Jobs

- None returned by `list_all_jobs`.

## Installed/Observed Templates

Only baseline/default templates were returned:

- `Error: not authorized`
- `Error: unknown error`
- `Error: not found`
- `LottieFiles component`

No Trello-specific UI templates were observed.

## Installed/Observed Actions

### `Atlassian Trello: Create a Board`

- ID: `[REDACTED_ID]`
- Input signature observed: `main(name:string)`
- Method: `POST`
- Uses configuration schema `Atlassian Trello API configuration` through `_getfirstfiltereddatav3`.
- Query parameters use values from:
  - `USER_SERVICE.payload.Trello_API_KEY`
  - `USER_SERVICE.payload.Trello_access_token`
- Observed auth method in JS: `BEARER`, with `API_XXX_KEY: USER_SERVICE.payload.oauth_token_secret`.
- Output schema was not clearly visible in the extracted JS snippet.

### `Atlassia Trello: Get Board by id`

- ID: `[REDACTED_ID]`
- Naming issue: action name is misspelled as `Atlassia Trello`, missing the `n` in `Atlassian`.
- Input signature observed: `main(id:string)`
- Method: `GET`
- Output schema reference: `BoardResponse` (`[REDACTED_ID]`)
- Uses configuration schema `Atlassian Trello API configuration` through `_getfirstfiltereddatav3`.
- Query parameters use values from:
  - `USER_SERVICE.payload.Trello_API_KEY`
  - `USER_SERVICE.payload.Trello_access_token`

### `Atlassian Trello: Delete a Board`

- ID: `[REDACTED_ID]`
- Input signature observed: `main(id:string)`
- Method: `DELETE`
- Uses configuration schema `Atlassian Trello API configuration` through `_getfirstfiltereddatav3`.
- Query parameters use values from:
  - `USER_SERVICE.payload.Trello_API_KEY`
  - `USER_SERVICE.payload.Trello_access_token`
- Logs HTTP status.

### `Atlassian Trello: Create a List on a Board`

- ID: `[REDACTED_ID]`
- Description includes developer links:
  - `https://developer.atlassian.com/cloud/trello/rest/api-group-boards/#api-boards-id-lists-post`
- Input signature observed: `main(id:string,name:string)`
  - likely `id`: board ID
  - likely `name`: list name
- Method: `POST`
- Output schema reference: `ListOnBoardResponse` (`[REDACTED_ID]`)
- Uses configuration schema `Atlassian Trello API configuration` through `_getfirstfiltereddatav3`.
- Query parameters use values from:
  - `USER_SERVICE.payload.Trello_API_KEY`
  - `USER_SERVICE.payload.Trello_access_token`

## Installed/Observed Data Schemas

### `Atlassian Trello API configuration`

- ID: `[REDACTED_ID]`
- Title in JSON schema: `UserService`
- Fields:
  - `App_ID`
  - `User_identity_API_authorization_URL`
  - `Client_ID`
  - `Secret` — marked `SECRET`
  - `Trello_API_KEY` — marked `SECRET`
  - `Trello_SECRET` — marked `SECRET`
  - `Trello_access_token` — marked `SECRET`
  - `oauth_token` — marked `SECRET`
  - `oauth_token_secret` — marked `SECRET`

Security note: treat every token/key/secret field as sensitive. Do not copy real values into docs/logs/chat.

### `BoardResponse`

- ID: `[REDACTED_ID]`
- Description includes Trello docs link:
  - `https://developer.atlassian.com/cloud/trello/rest/api-group-boards/#api-boards-id-get`
- Fields observed:
  - `id`
  - `name`
  - `desc`
  - `descData`
  - `closed`
  - `idMemberCreator`
  - `idOrganization`
  - `pinned`
  - `url`
  - `shortUrl`
- Required fields: none.

### `ListOnBoardResponse`

- ID: `[REDACTED_ID]`
- Fields observed:
  - `id`
  - `name`
  - `closed`
  - `pos`
  - `softLimit`
  - `idBoard`
  - `subscribed`
  - `limits.attachments.perBoard.status`
  - `limits.attachments.perBoard.disableAt`
  - `limits.attachments.perBoard.warnAt`
- Required fields: none.

## Capabilities Documented

Observed/expected capabilities from installed objects:

1. Store Trello/Atlassian app credentials and tokens.
2. Create a Trello board.
3. Get a Trello board by ID.
4. Delete a Trello board.
5. Create a list on a Trello board.

Not observed in this plugin snapshot:

- create/get/update/delete card;
- move card between lists;
- list cards on board/list;
- members;
- labels;
- checklists/check items;
- comments/actions;
- attachments;
- custom fields;
- webhooks;
- OAuth flow actions;
- NoCode-X API endpoints;
- scheduled sync jobs;
- UI templates.

## Observed Issues / Validation Notes

Global `list_all_issues` returned 18 open BUG issues:

- `MISSING_REQUIRED_FIELD`: missing `Data format`.
- `MISSING_REQUIRED_FIELD`: missing `Authentication method`.
- `MISSING_REQUIRED_FIELD`: missing `Text`.
- `UNEXISTING_DATA_FORMAT_USED`: actions reference `Atlassian Trello API configuration` (`[REDACTED_ID]`) as non-existing, even though the schema is visible via `list_all_dataschemas` and `get_dataschema`.

Counts observed:

- `MISSING_REQUIRED_FIELD`: 16
- `UNEXISTING_DATA_FORMAT_USED`: 2

Important interpretation:

- Missing auth/text/data-format fields may be normal post-install setup debt until credentials and action settings are configured.
- `UNEXISTING_DATA_FORMAT_USED` against a currently visible schema is suspicious and may indicate stale internal references, validation cache, or plugin packaging issue if it persists after refresh/setup.
- Per-action `list_action_issues` returned empty arrays, while global `list_all_issues` linked issues to Trello action IDs. Prefer global issue list as source of truth.

## JavaScript / Logic Notes

Observed JS pattern across actions:

- `_start()`
- `_getfirstfiltereddatav3` reads first `Atlassian Trello API configuration` record.
- `_replaceplaceholders` builds endpoint.
- `_httpcall` invokes Trello endpoint.
- `_logline` logs response/status.

MCP-rendered JS endpoint fragments looked malformed/truncated around `TEXT:'https:let {RESPONSE...`, a pattern also seen in other unconfigured plugins. Treat as suspicious but verify in rendered action editor before classifying as a hard endpoint defect.

Auth/query mapping looks potentially confused:

- JS uses `AUTHENTICATION_METHOD:'BEARER'`.
- `API_XXX_KEY` is populated from `oauth_token_secret`.
- Trello key/token are also passed as query parameters from `Trello_API_KEY` and `Trello_access_token`.

This may still work if NoCode-X ignores `API_XXX_KEY` for bearer auth or if UI configuration normalizes it, but it should be verified before production use.

## Setup/Test Flow

1. Create/fill one `Atlassian Trello API configuration` record.
2. Fill only non-sensitive placeholders in docs; actual fields must remain secret:
   - Trello API key
   - Trello access token
   - OAuth token/secret if required
3. Open `Atlassian Trello: Get Board by id` in the action editor first because it is read-only.
4. Confirm endpoint, query parameters, authentication method, and output data format.
5. Test `Get Board by id` against a controlled Trello board ID.
6. Only after read works, test `Create a Board` and `Create a List on a Board`.
7. Treat `Delete a Board` as destructive; test only against a throwaway board.
8. Re-run `list_all_issues`; persistent `UNEXISTING_DATA_FORMAT_USED` or malformed endpoint/auth issues should be reported.

## Usefulness Assessment

Useful as a starting scaffold for simple Trello board/list operations.

Not sufficient for a complete Trello integration because it lacks core card workflows, which are usually the main Trello use case.

For real project automation, the next missing actions would be:

- create card;
- update card;
- move card to list;
- list cards in list/board;
- add comment to card;
- add label/member/checklist;
- archive/delete card;
- webhook or polling sync.

## Developer Issue

A reportable issue has been recorded in `references/plugin-developer-issues.md` covering:

- typo in action name `Atlassia Trello: Get Board by id`;
- `UNEXISTING_DATA_FORMAT_USED` against visible config schema;
- possible malformed endpoint rendering in MCP JS;
- possible auth mapping confusion;
- incomplete coverage relative to broad `Atlassian Trello API` name.
