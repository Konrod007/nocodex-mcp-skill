# NoCode-X Plugin: Google API integration

Status: **observed through MCP**.

Observed in workspace `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`), application `Unnamed Application` (`[REDACTED_ID]`).

## Purpose

Generic Google credential data-format package for NoCode-X integrations that need Google API authentication material.

Based on the installed object set, this plugin currently looks like a **credential/schema dependency**, not a functional wrapper around a specific Google API such as Sheets, Drive, Gmail, Calendar, etc.

## Installed/Observed APIs

- None returned by `list_all_apis`.
- `search_apis("Google")` returned `[]`.

## Installed/Observed Actions

- None returned by `get_actions`.
- `search_actions("Google")` returned `[]`.
- `search_actions("API")` returned `[]`.
- `search_actions("Sheet")` returned `[]`.

## Installed/Observed Jobs

- None returned by `list_all_jobs`.

## Installed/Observed Issues

- None returned by `list_all_issues`.

## Installed/Observed Data Schemas

### `Google: Service user json`

- ID: `[REDACTED_ID]`
- Purpose: generic Google service-account JSON shape.
- Fields observed:
  - `type`
  - `project_id`
  - `private_key_id`
  - `private_key`
  - `client_email`
  - `client_id`
  - `auth_uri`
  - `token_uri`
  - `auth_provider_x509_cert_url`
  - `client_x509_cert_url`
- Classification: all observed fields are marked `SECRET` in schema metadata.
- Safety note: never copy actual service account JSON or private key material into docs, chat, logs, or examples.

### `Google: API Key json`

- ID: `[REDACTED_ID]`
- Description: `Dataformat used to specify an API key that can be used when communicating with Google APIs.`
- Required fields:
  - `api_key`
- Classification: `api_key` is marked `SECRET`.

## Interpretation

This plugin appears to install reusable Google auth/config data formats only.

It does **not** currently install:

- request/response schemas for a specific Google product;
- actions that call Google endpoints;
- NoCode-X APIs;
- scheduled jobs;
- UI templates/pages beyond baseline defaults.

This may be expected if `Google API integration` is intended as a dependency for other Google plugins. If the marketplace presents it as a standalone functional API integration, the name may be too broad/misleading because no executable integration surface is created.

## Relationship To `Google Spreadsheet API`

After `Google API integration` was installed, the application still had no Spreadsheet/Sheets actions, APIs, jobs, or Spreadsheet-specific schemas.

Therefore, the earlier `Google Spreadsheet API` issue remains: installing the credential dependency does not by itself produce usable Google Sheets operations.

## Recommended Use

Use this plugin as a credential/schema dependency for builder-created or manually authored Google API actions:

- service-account based server-to-server integrations;
- API-key based Google APIs where an API key is sufficient;
- downstream plugins/actions that reference the two credential data formats.

For Google Sheets specifically, additional actions still need to be created or provided by a separate functional plugin, such as:

- read values/range;
- append rows;
- update values/range;
- clear range;
- read spreadsheet metadata;
- batchUpdate.

## Safety Notes

- Treat every field in `Google: Service user json` as sensitive.
- Treat `Google: API Key json.api_key` as sensitive.
- Do not read/store real Google keys, service account private keys, OAuth tokens, or credentials.
- In examples, use placeholders such as `[REDACTED]` only.
