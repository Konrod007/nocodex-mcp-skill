# Observed Plugin: Google Meet API

Status: **observed through MCP; partial Google Meet Spaces / Conference Records integration with validation issues**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`).

## Current Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)

## Installed Objects

### Actions

- `Google Meet: Get a meeting space` (`[REDACTED_ID]`)
- `Google Meet: Create Space` (`[REDACTED_ID]`)
- `Google Meet: End Active Conference` (`[REDACTED_ID]`)
- `Google Meet: Get Conference Records` (`[REDACTED_ID]`)
- `Google Meet: Get Conference Records List` (`[REDACTED_ID]`)

### Data Schemas

- `Space` (`[REDACTED_ID]`)
- `ConferenceRecord` (`[REDACTED_ID]`)
- `Conference Records List` (`[REDACTED_ID]`)
- `Google: Service user json` (`[REDACTED_ID]`)
- `Google: API Key json` (`[REDACTED_ID]`)

The two Google credential schemas may come from the separate `Google API integration` dependency package rather than this plugin itself.

### APIs / Jobs / Templates

- No first-class NoCode-X API objects returned by `list_all_apis`.
- No scheduled jobs returned by `list_all_jobs`.
- Templates are baseline/default error/LottieFiles templates only, with duplicated `_1` variants observed after installation:
  - `Error: not authorized`
  - `Error: unknown error`
  - `Error: not found`
  - `LottieFiles component`
  - `_1` duplicates of the same baseline templates

## Schema Summary

### `Space`

Fields:

- `name`
- `meetingUri`
- `meetingCode`
- `config.accessType` enum:
  - `ACCESS_TYPE_UNSPECIFIED`
  - `OPEN`
  - `TRUSTED`
  - `RESTRICTED`
- `config.entryPointAccess` enum:
  - `ENTRY_POINT_ACCESS_UNSPECIFIED`
  - `ALL`
  - `CREATOR_APP_ONLY`
- `activeConference.conferenceRecord`

### `ConferenceRecord`

Fields:

- `name`
- `startTime`
- `endTime`
- `expireTime`
- `space`

### `Conference Records List`

Fields:

- `conferenceRecords[]` with the same fields as `ConferenceRecord`
- `nextPageToken`

### Credential Schemas

`Google: Service user json` contains service-account style fields such as `token_uri`, `client_email`, `private_key`, `project_id`, `client_id`, etc., mostly classified as `SECRET`.

`Google: API Key json` contains secret `api_key`.

## Observed Action Implementation Shape

All observed Google Meet actions use roughly this pattern:

1. Read first `Google: Service user json` record with `_getfirstfiltereddatav3`.
2. Create GCP access token with `_creategcpaccesstoken`.
3. Use bearer auth (`AUTHENTICATION_METHOD: 'BEARER'`, `API_XXX_KEY: ACCESS_TOKEN`) for a Google Meet HTTP call.
4. Log the response or status.

Important observed hard-coded value:

- `DELEGATED_USERMAIL: 'rafal@nocode-applications.com'`

This is probably not reusable for other tenants and should be replaced/configured before production use.

MCP-rendered JS endpoint and scope fragments are truncated/malformed (`SCOPE:'https:`, `ENDPOINT:'https:`). This may be MCP rendering loss, but it aligns with validation issues about missing Text/Auth/Data format, so verify inside the rendered NoCode-X action editor.

## Issues

Global issue list returned 29 open BUG issues related to Google Meet actions:

- 10 × missing `Text`
- 8 × missing `Data format`
- 7 × missing `Authentication method`
- 4 × `UNEXISTING_DATA_FORMAT_USED`

The `UNEXISTING_DATA_FORMAT_USED` issues reference `Google: Service user json` (`[REDACTED_ID]`) as non-existing even though that schema is visible in the current data schema list. This resembles the stale/internal-reference issue observed in other NoCode-X plugins.

Issue distribution by action:

- `Google Meet: Get a meeting space`: 7
- `Google Meet: Create Space`: 7
- `Google Meet: Get Conference Records`: 9
- `Google Meet: Get Conference Records List`: 6
- `Google Meet: End Active Conference`: no global issue observed in the returned list, but its MCP-rendered JS is still truncated/malformed.

## Capability Assessment

Observed coverage is focused on Google Meet v2 Spaces and Conference Records:

- create a meeting space;
- get a meeting space;
- end active conference;
- get one conference record;
- list conference records.

Not observed:

- Calendar event creation/invites;
- Google OAuth user flow UI;
- dynamic delegated user configuration;
- participants/participant sessions;
- recordings/transcripts/artifacts;
- conference record pagination controls beyond `nextPageToken` schema;
- webhooks/watch/subscriptions;
- app-facing API endpoints;
- scheduled jobs;
- UI templates.

## Verdict

Useful as a partial scaffold for Google Meet Spaces / Conference Records, but not production-ready out of the box. The hard-coded delegated user, missing-field issues, and malformed/truncated endpoint/scope rendering need validation/fixing before runtime use.
