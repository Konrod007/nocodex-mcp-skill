# NoCode-X Plugin Developer Issues

Use this document for platform/plugin defects or suspicious behavior that should be reported to NoCode-X/plugin developers. Keep entries evidence-based and redact secrets.

---

## 2026-06-05 — Google Spreadsheet API installs without Spreadsheet objects

Status: **ready to report**  
Severity: **medium/high for plugin usability**  
Plugin: `Google Spreadsheet API` / Google Sheets plugin  
Workspace observed: `[REDACTED_WORKSPACE]`  
Application observed: `Unnamed Application` (`[REDACTED_ID]`)

### Summary

User-confirmed install behavior: the `Google Spreadsheet API` plugin can be installed, but it does not create the expected Spreadsheet/Sheets capabilities in the application.

MCP verification after installation shows:

- `get_actions` → `[]`
- `search_actions("Google")` → `[]`
- `search_actions("Spreadsheet")` → `[]`
- `search_actions("Sheet")` → `[]`
- `list_all_apis` → `[]`
- `list_all_jobs` → `[]`
- `list_all_issues` → `[]`
- `search_dataschemas("Spreadsheet")` → `[]`
- `search_dataschemas("Sheet")` → `[]`

Only generic Google credential data schemas are present:

- `Google: Service user json` (`[REDACTED_ID]`)
- `Google: API Key json` (`[REDACTED_ID]`)

No Spreadsheet-specific actions, APIs, jobs, schemas, or validation issues were created/returned through MCP.

### Update After Installing `Google API integration`

The user then installed `Google API integration`. A fresh MCP fallback snapshot still showed no Spreadsheet/Sheets actions, APIs, jobs, or Spreadsheet-specific schemas.

`Google API integration` only confirmed/created the generic Google credential schemas:

- `Google: Service user json`
- `Google: API Key json`

This suggests `Google API integration` may be a credential dependency package, but it does not resolve the missing operational layer for `Google Spreadsheet API`.

### Update After Installing Another `Google Spreadsheet API` Version

The user later installed another version of `Google Spreadsheet API` and requested a retry. A fresh MCP fallback snapshot in the same application showed no Google/Spreadsheet/Sheets operational objects at all:

- `get_actions` → `[]`
- `list_all_dataschemas` → `[]`
- `list_all_apis` → `[]`
- `list_all_jobs` → `[]`
- `list_all_issues` → `[]`
- searches for `Google`, `Spreadsheet`, `Sheet`, `Sheets`, `spreadsheet`, `values`, `range`, and `append` returned empty results across actions, schemas, APIs, and jobs.

The app still had 21 templates, but those are existing baseline/Vanilla Heroes leftovers and not Google Sheets objects.

This strengthens the report: more than one installed version/package label for `Google Spreadsheet API` can leave the app with no MCP-visible Spreadsheet capability.

### Expected Behavior

A plugin named `Google Spreadsheet API` should create at least one usable Spreadsheet/Sheets action or API surface, for example:

- read values/range;
- append row(s);
- update values/range;
- clear values;
- spreadsheet metadata/read;
- optionally create spreadsheet/sheet or batchUpdate.

At minimum, if the plugin is only an auth dependency, the marketplace/install UI should make that explicit and not present it as a Spreadsheet API plugin.

### Actual Behavior

Installation leaves the app with only generic Google credential schemas and no operational Google Sheets objects.

### Evidence

Current app object inventory after installation:

- Actions: none.
- APIs: none.
- Jobs: none.
- Data schemas: two generic Google credential schemas only.
- Issues: none.
- Baseline templates only: vanilla error pages and `LottieFiles component`.

### Developer Questions

1. Is `Google Spreadsheet API` supposed to create Spreadsheet actions/APIs, or is it only an auth/config dependency package?
2. If it is supposed to create Spreadsheet actions, is the plugin package missing its action definitions during installation?
3. If another plugin depends on these generic Google credential schemas, should the marketplace label this package as `Google API credentials` instead of `Google Spreadsheet API`?
4. Should installation produce a validation issue/warning when expected plugin objects are missing?

### Secret Handling

No Google credentials, service account private keys, OAuth tokens, API keys, or user data were read or stored in this report.

---

## 2026-06-05 — Chat Logs plugin has stale references, deprecated methods, and duplicate baseline templates

Status: **ready to report / needs developer triage**  
Severity: **medium for plugin usability**  
Plugin: `Chat Logs`  
Workspace observed: `[REDACTED_WORKSPACE]`  
Application observed: `Unnamed Application` (`[REDACTED_ID]`)  
User note: plugin is marked as test.

### Summary

`Chat Logs` creates useful scaffold objects for a chat/LLM log viewer, but the installed package appears beta/test quality and has several validation issues.

Installed objects observed through MCP:

- Schema: `chatlogs` (`[REDACTED_ID]`)
- Actions:
  - `Hide empty instructions` (`[REDACTED_ID]`)
  - `Display chat log record` (`[REDACTED_ID]`)
  - `Show Logs` (`[REDACTED_ID]`)
- Template: `Chat log record` (`[REDACTED_ID]`)

No APIs or jobs were created.

### Issues Observed

Global `list_all_issues` returned 8 open BUG issues:

1. `UNEXISTING_DATA_FORMAT_USED`: `Fetch a list of data records` references `[REDACTED_ID]`, even though the visible schema `chatlogs` currently has that ID.
2. `UNEXISTING_DATA_FORMAT_USED`: `Fetch a list of data records` references missing data format `[REDACTED_ID]`.
3. `DEPRECATED_METHOD_USED`: `getfiltereddatav3`.
4. `DEPRECATED_METHOD_USED`: `createdate`.
5. `DEPRECATED_METHOD_USED`: `addtemplatecomponenttolistv2`.
6. Some deprecated-method issues appear duplicated.

### Duplicate Baseline Templates

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

This may indicate the plugin package includes/copies the vanilla error-page scaffold unnecessarily.

### API Inconsistency

`list_action_issues(actionId)` returned empty arrays for the actions, while global `list_all_issues` clearly linked issues to those same action IDs. This makes action-level troubleshooting unreliable.

### Expected Behavior

For a test plugin, warnings are acceptable, but the installed package should ideally:

- bind `Show Logs` to the current `chatlogs` schema without `UNEXISTING_DATA_FORMAT_USED`;
- avoid references to missing data formats;
- avoid deprecated platform methods or mark them as legacy/test explicitly;
- not duplicate vanilla error templates unless intentionally package-local;
- return consistent issue data between global and per-action issue APIs.

### Suggested Developer Checks

1. Rebind `Show Logs` → `Fetch a list of data records` to the installed `chatlogs` schema.
2. Locate/remove stale reference `[REDACTED_ID]`.
3. Replace deprecated invocations:
   - `getfiltereddatav3`
   - `createdate`
   - `addtemplatecomponenttolistv2`
4. Check why vanilla error templates are duplicated during plugin install.
5. Check issue API consistency for `list_action_issues` vs `list_all_issues`.

### Secret Handling

No secrets or chat-log records were read or stored in this report.

---

## 2026-06-05 — Atlassian Trello API plugin is partial and has naming/reference/auth issues

Status: **ready to report / needs developer triage**  
Severity: **medium for plugin usability**  
Plugin: `Atlassian Trello API`  
Workspace observed: `[REDACTED_WORKSPACE]`  
Application observed: `Unnamed Application` (`[REDACTED_ID]`)

### Summary

`Atlassian Trello API` installs a small set of board/list actions and schemas, but it does not cover the majority of common Trello operations. It also has several packaging/validation concerns.

Installed objects observed through MCP:

- Schema: `Atlassian Trello API configuration` (`[REDACTED_ID]`)
- Schema: `BoardResponse` (`[REDACTED_ID]`)
- Schema: `ListOnBoardResponse` (`[REDACTED_ID]`)
- Action: `Atlassian Trello: Create a Board` (`[REDACTED_ID]`)
- Action: `Atlassia Trello: Get Board by id` (`[REDACTED_ID]`)
- Action: `Atlassian Trello: Delete a Board` (`[REDACTED_ID]`)
- Action: `Atlassian Trello: Create a List on a Board` (`[REDACTED_ID]`)

No NoCode-X APIs, jobs, card/member/label/checklist/comment/attachment/webhook actions, or Trello-specific templates were observed.

### Issues Observed

Global `list_all_issues` returned 18 open BUG issues:

- 16 × `MISSING_REQUIRED_FIELD` for missing `Data format`, `Authentication method`, or `Text`.
- 2 × `UNEXISTING_DATA_FORMAT_USED`: actions reference `Atlassian Trello API configuration` (`[REDACTED_ID]`) as non-existing, even though that schema is visible through `list_all_dataschemas` and `get_dataschema`.

As with other plugins, some missing auth/data-format fields may be post-install setup debt. The `UNEXISTING_DATA_FORMAT_USED` against a visible schema is more suspicious and should be revalidated after refresh/setup.

### Naming Issue

Action name typo:

- `Atlassia Trello: Get Board by id`

Expected:

- `Atlassian Trello: Get Board by id`

### Possible Auth Mapping Concern

MCP-rendered JS suggests actions use:

- `AUTHENTICATION_METHOD:'BEARER'`
- `API_XXX_KEY: USER_SERVICE.payload.oauth_token_secret`
- Trello key/token also passed as query params from:
  - `Trello_API_KEY`
  - `Trello_access_token`

This may be harmless if NoCode-X ignores irrelevant auth fields or normalizes the call, but it should be verified because Trello REST examples commonly use key/token query parameters.

### Possible Endpoint Rendering Concern

MCP-rendered action JS showed malformed/truncated endpoint fragments around:

```text
TEXT:'https:let {RESPONSE...
```

This pattern has appeared in other unconfigured plugins, so it may be an MCP/action-JS rendering artifact. Still, developers should verify endpoint text in the action editor/package source.

### Product Coverage Concern

Given the broad plugin name `Atlassian Trello API`, expected user workflows usually include cards. The installed package currently lacks observed actions for:

- create/update/delete/archive card;
- move card between lists;
- list cards;
- card comments;
- labels;
- members;
- checklists;
- attachments;
- webhooks/sync.

If the plugin is intentionally only board/list operations, the marketplace description should make that narrower scope clear.

### Suggested Developer Checks

1. Fix typo: `Atlassia` → `Atlassian`.
2. Rebind actions to the installed config schema and re-run validation.
3. Verify endpoint strings in package source/action editor.
4. Verify intended auth method and whether key/token should be query params, bearer, OAuth 1.0, or another supported method.
5. Clarify marketplace description/scope or add core card operations.
6. Check issue API consistency if per-action issue calls remain empty while global issues point to action IDs.

### Secret Handling

No Trello keys, tokens, secrets, board data, or user data were read or stored in this report.

---

## 2026-06-05 — Plugin uninstall/cleanup leaves objects from removed plugins

Status: **ready to report / needs platform cleanup triage**  
Severity: **high for plugin lifecycle hygiene and auditability**  
Area: Plugin install/uninstall lifecycle, package cleanup, application inventory  
Workspace observed: `[REDACTED_WORKSPACE]`  
Application observed: `Unnamed Application` (`[REDACTED_ID]`)

### Summary

After studying and deleting plugins, the application still contains MCP-visible objects from plugins that should no longer be present. A removed plugin should not leave actions, data schemas, templates, or validation issues behind unless the user explicitly chooses to keep them.

This creates noisy inventories and makes later plugin audits unreliable because old plugin artifacts can be mistaken for newly installed plugin content.

### Current Evidence

A fresh MCP fallback snapshot of the current application returned:

```text
Folders:      2
APIs:         0
Data schemas: 2
Actions:      1
Jobs:         0
Templates:    21
Issues:       7
```

Objects still visible after plugin deletion/cleanup attempts:

#### Stripe | Payment Links API leftovers

```text
Action:
- Stripe | Payment Link: Create a payment link

Data schemas:
- Stripe API configuration
- PaymentLink

Issues:
- 7 open BUG issues attached to `Stripe | Payment Link: Create a payment link`
```

Issue breakdown:

```text
2 × missing "Text"
2 × missing "Authentication method"
2 × missing "Data format"
1 × UNEXISTING_DATA_FORMAT_USED
```

#### Vanilla Heroes leftovers

17 templates/components are still visible:

```text
Border hero with cropped image and shadows
Colored Border Button
Responsive left-aligned hero with image
Centered hero
Centered screenshot
Play Button component
heroes page
Black Border Play Button
White Background Button
Dark mode hero
Sign-up Form
White Border Play Button (Dark Mode)
Colored Background Button
Black Border Button
Play Button component (Dark Mode)
Vertically centered hero sign-up form
Colored Border Button (Dark Mode)
```

The associated Vanilla Heroes actions are no longer visible, which suggests partial cleanup:

```text
Sign up
Left button action
Execute left button action
Right button action
Play button action
Execute right button action
```

### Baseline Objects That Should Remain

The following templates are considered normal baseline/default application objects and should not be treated as plugin leftovers:

```text
Error: not authorized
Error: unknown error
Error: not found
LottieFiles component
```

### Expected Behavior

When a plugin is deleted/uninstalled, NoCode-X should either:

1. remove all objects created by that plugin package, including actions, data schemas, templates/pages, jobs, APIs, and related validation issues; or
2. show an explicit cleanup dialog listing package-created objects and asking whether the user wants to keep or remove them.

After cleanup, this application should return to roughly:

```text
Actions:      0
Data schemas: 0
APIs:         0
Jobs:         0
Templates:    baseline error/LottieFiles templates only
Issues:       0
```

### Actual Behavior

Plugin artifacts remain visible after deletion/cleanup attempts:

- Stripe Payment Links action and schemas remain.
- Stripe Payment Links validation issues remain.
- Vanilla Heroes templates remain while its actions appear to be removed.
- The app inventory therefore contains data from previously deleted plugins.

### Why This Matters

This breaks several important workflows:

- plugin audit and marketplace QA;
- clean-room plugin testing;
- DTAP promotion/reproducibility;
- application cleanup after experimentation;
- RBAC/audit trail expectations around plugin-created objects;
- user trust in plugin uninstall behavior.

It also makes it hard to distinguish current plugin state from orphaned historical artifacts.

### Suggested Developer Checks

1. Track plugin package ownership for every installed object: action, schema, template/page, API, job, media asset, issue, and folder.
2. On uninstall, remove or explicitly offer to remove all package-owned objects.
3. Recompute/clear validation issues for deleted objects.
4. Handle partial dependencies carefully: shared baseline templates should remain; plugin-specific copies/components should be removed.
5. Add a `Plugin cleanup` / `Remove orphaned plugin objects` maintenance command in the UI.
6. Expose package ownership and uninstall status through MCP so automated audits can distinguish current plugin content from leftovers.

### Secret Handling

No Stripe API keys, payment data, customer data, or other secrets were read or stored in this report.
