# NoCode-X Plugin: Dropbox API

This reference documents the observed Dropbox API plugin installed in NoCode-X workspace `PF panel`, application `Unnamed Application` (`[REDACTED_ID]`).

Source of truth for this entry: NoCode-X MCP calls after OAuth authorization. The user reported that the rendered UI shows `Dropbox API` as a separate plugin under the `Plugins` area. MCP `list_all_folders` currently returns only top-level `Root` and `Plugins`, so nested UI folders are not fully visible through the folder-list tool.

## Executive Summary

The Dropbox API plugin installs a small Dropbox integration surface:

- OAuth/token actions:
  - `Dropbox: get access token`
  - `Dropbox: refresh token`
- Dropbox operation actions:
  - `Dropbox: Create Folder`
  - `Dropbox: List Folder`
  - `Dropbox: Create File Request`
- Data schemas for configuration, tokens, folder/list-folder request/response, and file requests.

No ordinary application APIs and no scheduled jobs were returned by MCP for the inspected application.

The plugin appears partially configured or internally inconsistent in the inspected app: `list_all_issues` returned 18 open BUG issues, including missing required fields and broken references to actions/data formats. Treat this plugin as needing setup/repair before production use.

## Observed Application Context

- Workspace: `PF panel`
- Workspace ID: `[REDACTED_ID]`
- Application: `Unnamed Application`
- Application ID: `[REDACTED_ID]`
- Top-level folders via MCP:
  - `Root`
  - `Plugins`
- APIs via MCP: none (`list_all_apis: []`)
- Jobs via MCP: none (`list_all_jobs: []`)

## Installed Objects

### Actions

| Action | ID | Purpose |
|---|---|---|
| `Dropbox: get access token` | `[REDACTED_ID]` | Exchange/get Dropbox access token from app config. |
| `Dropbox: refresh token` | `[REDACTED_ID]` | Refresh Dropbox access token. |
| `Dropbox: Create Folder` | `[REDACTED_ID]` | Create a Dropbox folder. |
| `Dropbox: List Folder` | `[REDACTED_ID]` | List contents of a Dropbox folder. |
| `Dropbox: Create File Request` | `[REDACTED_ID]` | Create a Dropbox file request. |

### Data Schemas

| Schema | ID | Role |
|---|---|---|
| `Dropbox API Configuration` | `[REDACTED_ID]` | App key/secret and token configuration record. |
| `AccessToken` | `[REDACTED_ID]` | Output of token actions. Contains secret fields. |
| `CreateFileRequest` | `[REDACTED_ID]` | Input payload for create file request. |
| `FileRequest` | `[REDACTED_ID]` | Output payload for created Dropbox file request. |
| `ListFolderRequest` | `[REDACTED_ID]` | Input payload for list folder. |
| `ListFolder` | `[REDACTED_ID]` | Expected response shape for Dropbox list-folder result. |
| `Folder` | `[REDACTED_ID]` | Folder metadata response shape. |

## Action Details

### `Dropbox: get access token`

Observed JS structure:

1. Calls `_start()`.
2. Writes a log line named `AUTHORIZATION CODE` with a placeholder/truncated URL (`https:` visible in MCP output only).
3. Calls `_getfirstfiltereddatav3` to fetch the first `Dropbox API Configuration` record.
4. Calls `_httpformpostv2` with:
   - `AUTHENTICATION_METHOD: 'BASIC_AUTH'`
   - `USERNAME: USER_SERVICE.payload.App_key`
   - `PASSWORD: USER_SERVICE.payload.App_secret`
   - output data format: `AccessToken`
5. Logs the response.

Required setup:

- One `Dropbox API Configuration` data record.
- `App_key` and `App_secret` filled in.
- An authorization-code step is likely required, but the full authorization URL/body was not recoverable from the MCP JavaScript output because endpoint strings were truncated/redacted in the tool result.

Security:

- Do not expose `App_secret`, `access_token`, or `refresh_token`.
- `AccessToken.access_token` and `AccessToken.refresh_token` are classified as `SECRET` in the observed schema.

### `Dropbox: refresh token`

Observed JS structure:

1. Calls `_start()`.
2. Fetches the first `Dropbox API Configuration` record with `_getfirstfiltereddatav3`.
3. Calls `_httpformpostv2` with `BASIC_AUTH` using `USER_SERVICE.payload.App_key` and `USER_SERVICE.payload.App_secret`.
4. Outputs an `AccessToken` data format.
5. Logs the response.

Required setup:

- Valid Dropbox app key/secret.
- Refresh token present in configuration or available through prior auth flow.

### `Dropbox: Create Folder`

Observed signature:

```ts
main(autorename: boolean, path: string)
```

Observed JS structure:

1. Calls `_start()`.
2. Invokes `Refresh Token` action with `ACTION: action_e6996e68_eeca_47c2_b3e6_e220ff57b345`.
3. Calls `_httpcall` with:
   - `AUTHENTICATION_METHOD: 'BEARER'`
   - `API_XXX_KEY: ACCESS_TOKEN.access_token`
   - output data format: `Folder`
4. Logs response.

Potential concern:

- The visible MCP JS snippet references `ACCESS_TOKEN.access_token`, but does not show an assignment from `_action(...)` outputs to `ACCESS_TOKEN`. In UI/runtime, verify whether NoCode-X binds action outputs into that variable. If not, runtime bearer auth will fail.

### `Dropbox: List Folder`

Observed input schema:

```ts
main(REQUEST: ListFolderRequestPayload)
```

Observed JS structure:

1. Calls `_start()`.
2. Invokes `Refresh Token` action.
3. Calls `_httpcall` with bearer auth using `ACCESS_TOKEN.access_token`.
4. Output data format visible in the JS snippet: `Folder` (`[REDACTED_ID]`).
5. Logs response.

Potential concern:

- The plugin also installs a richer `ListFolder` schema (`98821c9b-...`) with `cursor`, `entries`, and `has_more`, which looks more appropriate for Dropbox list-folder responses. If runtime validation fails or the output is incomplete, verify whether this action's output data format should be `ListFolder` instead of `Folder`.
- No `list_folder/continue` action was observed. Dropbox pagination requires continuation when `has_more` is true.

### `Dropbox: Create File Request`

Observed input schema:

```ts
main(REQUEST: CreateFileRequestPayload)
```

Observed JS structure:

1. Calls `_start()`.
2. Invokes `Refresh Token` action.
3. Calls `_httpcall` with bearer auth using `ACCESS_TOKEN.access_token`.
4. Output data format: `FileRequest`.
5. Logs response.

Required input:

- `destination`
- `open`
- `title`
- `deadline.deadline`

Optional/nullable input observed:

- `deadline.allow_late_uploads`: one of `none`, `one_day`, `three_days`, `seven_days`
- `created`
- `file_count`
- `url`

## Data Schema Details

### `Dropbox API Configuration`

Fields:

- `App_key`
- `App_secret`
- `authorization_code`
- `access_token`
- `refresh_token`

Notes:

- This schema is used by `get access token` and `refresh token` actions via `_getfirstfiltereddatav3`.
- It has no required fields in the observed JSON schema, but operationally the app key/secret and token/code fields are required for a working Dropbox integration.
- Treat `App_secret`, `access_token`, and `refresh_token` as sensitive even if all fields are not marked `SECRET` in schema metadata.

### `AccessToken`

Fields:

- `access_token`: string, classified `SECRET`
- `token_type`: string
- `expires_in`: integer
- `refresh_token`: string, classified `SECRET`

Use:

- Token action output.
- Later Dropbox operation actions expect an `ACCESS_TOKEN.access_token` value.

### `ListFolderRequest`

Required:

- `path`

Optional:

- `include_deleted`
- `include_has_explicit_shared_members`
- `include_media_info`
- `include_mounted_folders`
- `include_non_downloadable_files`
- `recursive`

Use:

- Input payload for `Dropbox: List Folder`.

### `ListFolder`

Key fields:

- `cursor`
- `entries[]`
- `has_more`

Entry fields:

- `.tag`: `file` or `folder`
- `id`
- `name`
- `path_display`
- `path_lower`
- `property_groups`
- `sharing_info`
- optional file metadata such as `client_modified`, `content_hash`, `server_modified`, `size`, `rev`.

Use:

- Expected response structure for Dropbox list folder.
- The observed action mapping may use `Folder` instead; verify in UI if list folder output behaves incorrectly.

### `Folder`

Required:

- `id`
- `name`
- `path_display`
- `sharing_info`

Optional/nullable:

- `path_lower`
- `property_groups`
- `sharing_info.no_access`
- `sharing_info.parent_shared_folder_id`
- `sharing_info.read_only`
- `sharing_info.traverse_only`

Use:

- Output of `Dropbox: Create Folder`.
- Also observed as output mapping for `Dropbox: List Folder`, but this may be an incorrect mapping.

### `CreateFileRequest`

Required:

- `destination`
- `open`
- `title`
- `deadline.deadline`

Optional/nullable:

- `deadline.allow_late_uploads`: `none`, `one_day`, `three_days`, `seven_days`
- `created`
- `file_count`
- `url`

Use:

- Input for `Dropbox: Create File Request`.

### `FileRequest`

Required:

- `created`
- `deadline`
- `destination`
- `file_count`
- `id`
- `is_open`
- `title`
- `url`

Optional/nullable:

- `description`

Use:

- Output of `Dropbox: Create File Request`.

## Observed Issues

`list_all_issues` returned 18 open BUG issues. Issue classes:

| Code | Meaning / observed pattern |
|---|---|
| `MISSING_REQUIRED_FIELD` | Missing `Text`, `Authentication method`, or `Data format` in generated invocations. |
| `UNEXISTING_ACTION_USED` | Invocation `Refresh Token` references an action ID that NoCode-X reports as non-existing. Reported IDs include both the current refresh token action ID and an older/deleted ID `[REDACTED_ID]`. |
| `UNEXISTING_DATA_FORMAT_USED` | Invocation `Get first from filtered data` references `Dropbox API Configuration` ID `9d91ef39-...`, while the schema currently exists in `list_all_dataschemas`. This may indicate stale/broken internal references or validator inconsistency. |

Important nuance:

- `list_action_issues` previously returned inconsistent results for some action IDs, while `list_all_issues` clearly linked issues to Dropbox actions. Prefer `list_all_issues` as the high-level validation source, then inspect action IDs manually.

## Recommended Repair / Validation Workflow

1. Confirm the plugin object set:
   - `get_actions`
   - `list_all_dataschemas`
   - `list_all_issues`
2. Confirm `Dropbox API Configuration` exists.
3. Ensure exactly one intended configuration record exists if the plugin uses “get first from filtered data”. Multiple records can cause unpredictable behavior.
4. Fill required Dropbox app credentials:
   - `App_key`
   - `App_secret`
5. Complete Dropbox OAuth authorization and populate required code/token fields.
6. Run/validate token actions first:
   - `Dropbox: get access token`
   - `Dropbox: refresh token`
7. Verify operation actions only after token actions work:
   - `Dropbox: Create Folder`
   - `Dropbox: List Folder`
   - `Dropbox: Create File Request`
8. Re-run `list_all_issues`.
9. If `UNEXISTING_ACTION_USED` remains:
   - open the affected action in UI;
   - remove/re-add the `Refresh Token` invocation;
   - ensure it points to the current `Dropbox: refresh token` action;
   - save/regenerate the action.
10. If `UNEXISTING_DATA_FORMAT_USED` remains:
   - open the `Get first from filtered data` invocation;
   - re-select `Dropbox API Configuration` as the data format;
   - save/regenerate the action.
11. If list-folder output is wrong:
   - verify whether `Dropbox: List Folder` should output `ListFolder` instead of `Folder`.

## Safe Test Inputs

For non-destructive validation after auth works:

### List folder

```json
{
  "path": "",
  "recursive": false,
  "include_deleted": false,
  "include_mounted_folders": true,
  "include_non_downloadable_files": true
}
```

### Create folder

Use only in a test account/path:

```json
{
  "path": "/nocodex-test",
  "autorename": true
}
```

### Create file request

Use only in a test account/path:

```json
{
  "destination": "/nocodex-file-requests",
  "open": true,
  "title": "NoCode-X test request",
  "deadline": {
    "deadline": "2026-12-31T23:59:59Z",
    "allow_late_uploads": "none"
  }
}
```

## Known Limitations Of Current MCP Evidence

- MCP JavaScript output truncates or redacts endpoint strings; exact Dropbox endpoint URLs and request bodies were not fully visible.
- MCP folder listing did not expose nested plugin UI packages; only top-level `Plugins` was visible.
- No runtime execution was performed against Dropbox; this document describes installed configuration/actions/schemas and validation issues, not successful API calls.
- No secrets or token values were read or stored.

## Recommendation For Future Plugin Research

Use `Dropbox API` as the template for future NoCode-X plugin documentation:

1. Identify plugin-local object names and IDs.
2. Map each action to inputs, outputs, auth mode, and dependent actions.
3. Document data schemas with required fields and sensitive fields.
4. Capture validation issues and likely repair workflow.
5. Keep plugin docs separate under `references/plugins/<plugin-name>.md` and link from `references/plugins-catalog.md`.
