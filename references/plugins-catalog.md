# NoCode-X Plugins Catalog

Use this reference when the user asks to study, install, audit, or document NoCode-X plugins.

## Plugin Research Workflow

NoCode-X plugins are ready-made settings/templates that can be installed into an application and then used as building blocks. Treat plugin installation as a potentially mutating operation.

Preferred workflow:

1. **Inventory first**
   - Identify available plugins, categories, descriptions, and required auth/config.
   - Do not install everything at once unless the user explicitly accepts the cleanup/traceability risk.
2. **Baseline snapshot before each install**
   - Record current counts/lists for: folders, APIs, data schemas, actions, templates/pages, jobs, and issues.
3. **Install one plugin at a time**
   - After each install, diff the app structure.
   - Attribute newly created actions/schemas/templates/issues to that plugin before moving on.
4. **Prefer plugin-package boundaries over global folders**
   - If the UI shows nested plugin packages, e.g. `Plugins / Dropbox API`, treat that package as the unit of analysis.
   - Current MCP `list_all_folders` may return only top-level folders (`Root`, `Plugins`) and may not expose the same nested UI hierarchy the browser shows.
   - If MCP cannot see subfolders, infer plugin membership from naming, descriptions, action/schema references, and UI screenshots, and label that inference explicitly.
5. **Inspect generated objects**
   - For actions, read action JavaScript.
   - For templates, inspect elements, attached actions, parameters, and HTML.
   - For APIs/schemas/jobs, fetch detailed metadata.
6. **Capture common setup requirements and issues**
   - Auth methods, required secrets/OAuth, placeholder fields, broken references, missing data formats.
7. **Document findings in this reference**
   - Keep entries class-level and reusable: purpose, installed objects, required configuration, common issues, and notes.

## Pitfalls

- Installing many plugins at once makes it hard to know which plugin created which action, data schema, template, API, job, or issue.
- It is normal for installed plugins to contain placeholder actions/schemas and immediately create validation issues until plugin-specific authorization and configuration are completed after installation.
- Treat `MISSING_REQUIRED_FIELD` issues for fields such as `Authentication method`, `Text`, `Data format`, API keys, OAuth settings, or service configuration as expected setup debt first, not necessarily as evidence that plugin installation failed.
- Plugin-created objects may reference actions or data formats by ID; if those targets are missing or renamed, NoCode-X can report `UNEXISTING_ACTION_USED` or `UNEXISTING_DATA_FORMAT_USED` issues.
- `list_all_apis` returning an empty list does not prove there is no Plugins UI section; it only means the current application has no ordinary application APIs exposed through that MCP tool.
- The rendered UI may expose plugin subfolders that MCP folder listing does not currently return. Do not claim subfolders are absent unless the rendered UI has also been inspected.

---

## Baseline Default Plugin: Vanilla error pages

Status: **default/baseline**.

User-confirmed behavior: `Vanilla error pages` is standard for every new NoCode-X application and is installed by default. During plugin audits, treat it as part of the baseline application scaffold, not as a manually installed integration plugin.

### Purpose

Provides default error-page templates for common application error states.

### Audit Implication

When diffing plugins one-by-one, do not attribute default error templates/pages to the next installed plugin unless new evidence shows they were modified or recreated by that plugin.

Likely baseline templates/pages include common error surfaces such as:

- unauthorized / not authorized;
- not found;
- unknown/general error.

---

## Observed Plugin: Atlassian Trello API

Detailed reference: `references/plugins/atlassian-trello-api.md`.

Current status in inspected app: **observed through MCP; partial Trello board/list integration**.

Installed objects:

- Schemas:
  - `Atlassian Trello API configuration`
  - `BoardResponse`
  - `ListOnBoardResponse`
- Actions:
  - `Atlassian Trello: Create a Board`
  - `Atlassia Trello: Get Board by id` (typo in action name)
  - `Atlassian Trello: Delete a Board`
  - `Atlassian Trello: Create a List on a Board`

No APIs, jobs, Trello UI templates, card/member/label/checklist/webhook actions were returned by MCP. The plugin is useful only as a starting scaffold for board/list operations. It has 18 open BUG issues, mostly setup debt plus `UNEXISTING_DATA_FORMAT_USED` against a visible config schema. Developer-facing report recorded in `references/plugin-developer-issues.md`.

---

## Observed Plugin: Chat Logs

Detailed reference: `references/plugins/chat-logs.md`.

Current status in inspected app: **observed through MCP; useful but test/beta-quality**.

User note: plugin is marked as test.

Installed objects:

- Schema: `chatlogs`
- Actions:
  - `Hide empty instructions`
  - `Display chat log record`
  - `Show Logs`
- Template: `Chat log record`

No APIs or jobs were returned by MCP. The plugin appears useful as a scaffold for a chat/LLM log viewer, but it has 8 open BUG issues including stale/non-existing data-format references, deprecated methods, and duplicated baseline error templates. Developer-facing report recorded in `references/plugin-developer-issues.md`.

---

## Observed Plugin: Google API integration

Detailed reference: `references/plugins/google-api-integration.md`.

Current status in inspected app: **observed through MCP**.

The plugin creates generic Google credential data schemas only:

- `Google: Service user json`
- `Google: API Key json`

No actions, APIs, jobs, or validation issues were returned by MCP. Interpret this as a credential/schema dependency package unless the marketplace explicitly promises executable Google API operations.

---

## Investigation: Google Spreadsheet API

Detailed reference: `references/plugins/google-spreadsheet-api.md`.

Current status in inspected app: **installed but operational Spreadsheet objects not observed**.

User-confirmed behavior: `Google Spreadsheet API` installs, but MCP shows no Spreadsheet/Sheets actions, APIs, jobs, or Spreadsheet-specific schemas. The only Google objects currently present are generic credential schemas supplied/confirmed by `Google API integration`:

- `Google: Service user json`
- `Google: API Key json`

Installing `Google API integration` did not add Spreadsheet operations. This is likely a reportable plugin/package issue or a misleading package label for `Google Spreadsheet API`. Developer-facing report recorded in `references/plugin-developer-issues.md`.

---

## Observed Plugin: Mailchimp API

Detailed reference: `references/plugins/mailchimp-api.md`.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP found five actions and nine schemas. No first-class NoCode-X API objects were returned by `list_all_apis`.

### Purpose

Mailchimp/Mandrill-style transactional email integration. Although named `Mailchimp API`, the installed configuration field is `mandrill_api_key`, and capabilities focus on transactional messages/templates/user info rather than Mailchimp Marketing audiences/campaigns.

### Documented Capabilities

- Store Mailchimp Transactional/Mandrill API key as a secret plugin configuration value.
- Retrieve user/account status and sending stats.
- Send transactional emails directly.
- Send transactional emails via named templates.
- Create/publish message templates.
- Retrieve template metadata/content.
- Support advanced message options: tracking, merge vars, tags, subaccount, analytics campaign, attachments, inline images, recipient metadata, scheduling, async sending, and IP pool.

Not observed in the current installed object set: audience/list/subscriber CRUD, campaigns/newsletters, automations/journeys, Marketing API OAuth, webhooks, or first-class NoCode-X API objects.

### Actions

- `Mailchimp: Get user info`
- `Mailchimp: Send new message`
- `Mailchimp: Send using message template`
- `Mailchimp: Add template`
- `Mailchimp: Get template info`

### Setup Interpretation

Missing auth/text/data-format validation issues are expected immediately after plugin installation because authorization and setup happen post-install. `UNEXISTING_DATA_FORMAT_USED` against visible config schema should be revalidated after setup/refresh and may indicate stale internal references if it persists.

---

## Observed Plugin: Gmail Postmaster Tools API

Detailed reference: `references/plugins/gmail-postmaster-tools-api.md`.

Current status in inspected app: **observed through MCP fallback; partial read-only Gmail Postmaster scaffold with validation issues**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP fallback found three actions and five related schemas. No first-class NoCode-X API objects, scheduled jobs, or Gmail Postmaster-specific UI templates were returned.

Installed objects:

- Credential/dependency schemas:
  - `Google: Service user json`
  - `Google: API Key json`
- Gmail Postmaster schemas:
  - `DomainsList`
  - `Domain`
  - `TrafficStats List`
- Actions:
  - `Gmail Postmaster: Get Domains List`
  - `Gmail Postmaster: Get Domains TrafficStats List`
  - `Gmail Postmaster: Get Domain by Domain Name`

Observed implementation uses `Google: Service user json`, `_creategcpaccesstoken`, bearer auth, and a hard-coded delegated user `rafal@nocode-applications.com`. Global issue list returned 24 open BUG issues: missing `Text`, `Authentication method`, `Data format`, and `UNEXISTING_DATA_FORMAT_USED` against visible `Google: Service user json`. MCP-rendered endpoint/scope fragments are malformed/truncated, so verify in the rendered action editor before runtime use.

Usefulness: narrow read-only scaffold for Postmaster domains and traffic stats. Not a complete monitoring integration: no pagination/date-range controls, storage, scheduled sync, alerting, dashboard UI, OAuth flow, or first-class app APIs observed.

---

## Observed Plugin: Google Meet API

Detailed reference: `references/plugins/google-meet-api.md`.

Current status in inspected app: **observed through MCP; partial Google Meet Spaces / Conference Records integration with validation issues**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP found five actions and five related schemas. No first-class NoCode-X API objects or scheduled jobs were returned. Templates are only baseline error/LottieFiles templates, including duplicated `_1` variants.

Installed objects:

- Credential/dependency schemas:
  - `Google: Service user json`
  - `Google: API Key json`
- Google Meet schemas:
  - `Space`
  - `ConferenceRecord`
  - `Conference Records List`
- Actions:
  - `Google Meet: Get a meeting space`
  - `Google Meet: Create Space`
  - `Google Meet: End Active Conference`
  - `Google Meet: Get Conference Records`
  - `Google Meet: Get Conference Records List`

Observed implementation uses `Google: Service user json`, `_creategcpaccesstoken`, bearer auth, and a hard-coded delegated user `rafal@nocode-applications.com`. Global issue list returned 29 open BUG issues: missing `Text`, `Data format`, `Authentication method`, and `UNEXISTING_DATA_FORMAT_USED` against visible `Google: Service user json`. MCP-rendered endpoint/scope fragments are malformed/truncated, so verify in the rendered action editor before runtime use.

Usefulness: partial scaffold for Meet Spaces / Conference Records. Not a complete Google Meet/Calendar integration: no Calendar invites/events, participant/session artifacts, recordings/transcripts, webhooks, jobs, app APIs, or user-facing OAuth flow observed.

---

## Observed Plugin: Gemini AI API

Detailed reference: `references/plugins/gemini-ai-api.md`.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP found one action, `Gemini AI: API test`, and three schemas: `Gemini AI API configuration`, `APITestRequest`, and `APITestResponse`.

### Purpose

Gemini text-generation integration using a Gemini-style request body (`contents[].parts[].text`) and a simplified generated-text response mapping (`candidate_responses[].text`).

### Documented Capabilities

- Store Gemini API key as a secret plugin configuration value.
- Accept text prompts through `APITestRequest.contents[].parts[].text`.
- Send a Gemini-style text generation request.
- Return generated text through `APITestResponse.candidate_responses[].text`.
- Log raw/mapped response through application logs.

Not observed in the current installed object set: model selection, temperature/max-token controls, system instructions, multimodal inputs, streaming, embeddings, function calling, safety settings, or chat/session abstraction.

### Setup Interpretation

Missing auth/text/data-format validation issues are expected immediately after plugin installation because authorization and setup happen post-install. Re-check after configuration before classifying them as plugin defects. Internal-reference issues such as `UNEXISTING_DATA_FORMAT_USED` should be revalidated after setup and may indicate stale references/cache if they persist.

---

## Observed Plugin: VIES VAT Validation

Detailed reference: `references/plugins/vies-vat-validation.md`.

Current status in inspected app: **observed through MCP; minimal VAT validation action**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP found one action and one schema. No NoCode-X API objects, jobs, config schema, or VIES-specific templates were returned.

Installed objects:

- Schema:
  - `Vat Validity response`
- Action:
  - `Vies: Check VAT Validity`

The action signature is `main(VAT:string,COUNTRY:string)`, method `GET`, auth shown as `NONE`, and output schema is `Vat Validity response`. Global issue list returned 4 open BUG issues: missing `Text` and missing `Authentication method`. Per-action issues returned empty, so prefer global issues. MCP-rendered JS endpoint fragment looked malformed/truncated. Schema field `naem` appears to be a typo for `name`.

Usefulness: small scaffold for public VAT validation, but not production-ready until endpoint/auth validation and schema typo are fixed/verified.

---

## Observed Plugin: Perplexity API

Detailed reference: `references/plugins/perplexity-api.md`.

Current status in inspected app: **observed through MCP fallback; minimal chat-completions scaffold with security/quality concerns**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP fallback found one action and three schemas. No first-class NoCode-X API objects, scheduled jobs, or Perplexity-specific UI templates were returned.

Installed objects:

- Configuration schema:
  - `Perplexity API Configuration` with `api_key`
- Request/response schemas:
  - `ChatCompletionRequest`
  - `ChatCompletionResponse`
- Action:
  - `Perplexity: Chat Completions`

`ChatCompletionRequest` includes `model`, `messages[]`, `max_tokens`, `temperature`, `top_p`, `search_domain_filter`, `return_images`, `return_related_questions`, `search_recency_filter`, `top_k`, `stream`, `presence_penalty`, `frequency_penalty`, and `response_format`. `ChatCompletionResponse` includes `citations[]`, `choices[]`, and usage tokens.

Global issue list returned 0 open issues. However, observed concerns remain: `Perplexity API Configuration.api_key` was not classified as `SECRET`, MCP-rendered endpoint fragment looked malformed (`ENDPOINT:'https:this._logline...`), and JS extraction did not show an output `DATA_XXX_FORMAT` mapping despite the response schema existing. Verify in the action editor before runtime use.

Usefulness: minimal but real chat-completions starting point. Not a full Perplexity integration: no model defaults/presets, streaming handling, citation UI, conversation persistence, retry/rate-limit handling, app APIs, jobs, or templates.

---

## Observed Plugin: Slack API

Detailed reference: `references/plugins/slack-api.md`.

Current status in inspected app: **observed through MCP fallback; broad Slack Web API scaffold with validation issues**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP fallback found 11 Slack actions and 13 Slack-related schemas. No first-class NoCode-X API objects, scheduled jobs, or Slack-specific UI templates were returned.

Installed objects:

- Configuration schema:
  - `Slack API configuration` with secret `userOAuthToken`
- Actions:
  - `Slack: auth.test`
  - `Slack: conversations.list`
  - `Slack: conversations.create`
  - `Slack:  conversations.join`
  - `Slack: conversations.leave`
  - `Slack: conversations.invite`
  - `Slack: conversations.kick`
  - `Slack: conversations.history`
  - `Slack: conversations.replies`
  - `Slack: chat.postMessage`
  - `Slack: chat.meMessage`
- Response/input schemas include `OAuth test RESPONSE`, `ConvarsationsList`, `CreateConversation RESPONSE`, `ConversationHistory RESPONSE`, `ConversationReplies RESPONSE`, `SendMessage RESPONSE`, `ShareMeMessageToChat RESPONSE`, and `InviteUsers`.

Global issue list returned 42 open BUG issues: 20 missing `Text`, 11 missing `Authentication method`, and 11 missing `Data format`. No `UNEXISTING_DATA_FORMAT_USED` was observed for Slack in this snapshot. Quality notes: typo `ConvarsationsList`, extra space in `Slack:  conversations.join`, duplicated baseline error templates `_1`, and MCP-rendered endpoint/auth fragments should be verified in the action editor.

Usefulness: broader than many observed plugins for Slack conversations and messages, but still missing OAuth lifecycle, Events API/interactivity/slash commands, users/files/reactions APIs, pagination/rate-limit handling, webhook signature verification, persistence, UI templates, and app APIs.

---

## Observed Plugin: Stripe | Payment Links API

Detailed reference: `references/plugins/stripe-payment-links-api.md`.

Current status in inspected app: **observed through MCP fallback; minimal create-payment-link scaffold with validation issues**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP fallback found one action and two schemas. No first-class NoCode-X API objects, scheduled jobs, or Stripe Payment Links-specific UI templates were returned.

Installed objects:

- Schemas:
  - `Stripe API configuration`
  - `PaymentLink`
- Action:
  - `Stripe | Payment Link: Create a payment link`

Observed implementation reads first `Stripe API configuration`, then performs `_httpformpostv2` using `BASIC_AUTH` with `USERNAME: USER_SERVICE.payload.api_key` and maps output to `PaymentLink`. The `PaymentLink` schema is broad, but the plugin only exposes one create action. Global issue list returned 7 open BUG issues: missing `Text`, `Authentication method`, `Data format`, and `UNEXISTING_DATA_FORMAT_USED` against visible `Stripe API configuration`.

Usefulness: narrow starting scaffold for creating payment links. Not a complete Stripe Payment Links integration: no retrieve/list/update/deactivate actions, no line-item retrieval, no webhook/signature verification, no persistence, no UI template, no app API, and no reconciliation jobs observed.

---

## Observed Plugin: Stripe | Core Resources | Events API

Detailed reference: `references/plugins/stripe-core-resources-events-api.md`.

Current status in inspected app: **observed through MCP; partial read-only Stripe Events integration**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP found two actions and three schemas. No first-class NoCode-X API objects, scheduled jobs, or Stripe-specific templates were returned.

Installed objects:

- Schemas:
  - `Stripe API configuration`
  - `EventsList`
  - `Event`
- Actions:
  - `Stripe Events: Retrieve an event`
  - `Stripe Events: List all events`

Global issue list returned 16 open BUG issues: 14 `MISSING_REQUIRED_FIELD` and 2 `UNEXISTING_DATA_FORMAT_USED` against a visible config schema. Per-action issue calls returned empty arrays, so prefer global issues as source of truth. MCP-rendered JS endpoint fragments looked malformed/truncated and should be checked in the rendered action editor.

Usefulness: small read-only scaffold for event inspection, not a production Stripe event-processing integration. Missing webhook receiver, signature verification, persistence, deduplication, pagination/filter controls, and broader Stripe resource workflows.

---

## Observed Plugin: Typeform API

Detailed reference: `references/plugins/typeform-api.md`.

Current status in inspected app: **observed through MCP; partial Typeform workspace integration with packaging issues**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP found six actions and seven schemas. No NoCode-X API objects, scheduled jobs, or Typeform-specific templates were returned.

Installed objects:

- Configuration schema:
  - `Typeform API configuration` with secret `PERSONAL_ACCESS_TOKEN`
- Request/response schemas:
  - `CreateWorkspaceRequest`
  - `CreateWorkspaceResponse`
  - `WorkspacesListResponse`
  - `UpdateWorkspaceRequest`
  - `CreateFormRequest`
  - `CreateThemeRequest/Response`
- Actions:
  - `Typeform: Create workspace`
  - `Typeform: Retrieve workspaces`
  - `Typeform: Retrieve account workspaces`
  - `Typeform: Create account workspace`
  - `Typeform: Retrieve workspace`
  - `CreateThere TEST` — suspicious test artifact

Global issue list returned 20 open BUG issues, all `MISSING_REQUIRED_FIELD`: missing `Text`, `Authentication method`, `Data format`, and one missing `Action` for `CreateThere TEST`. Per-action issues returned empty arrays, so prefer global issues. MCP-rendered endpoint fragments looked malformed/truncated.

Usefulness: partial starting basis for Typeform workspace operations, not a full Typeform integration. Missing form actions, response/submission actions, webhooks, theme actions, jobs, and UI templates despite some related schemas being installed.

---

## Observed Plugin: Vanilla Heroes

Detailed reference: `references/plugins/vanilla-heroes.md`.

Current status in inspected app: **observed through MCP fallback; UI/template pack with placeholder actions and validation issues**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). Normal MCP tool channel temporarily returned `ClosedResourceError`, but `hermes mcp test nocodex-mcp` succeeded and read-only registry fallback returned application data.

MCP found 17 likely plugin templates/components beyond the default error/LottieFiles baseline, including `heroes page`, `Centered hero`, `Dark mode hero`, `Responsive left-aligned hero with image`, `Vertically centered hero sign-up form`, `Border hero with cropped image and shadows`, `Centered screenshot`, button components, play button components, and `Sign-up Form`.

Six actions were returned: `Sign up`, `Left button action`, `Execute left button action`, `Right button action`, `Play button action`, and `Execute right button action`. Direct actions only log placeholder messages. Execute actions accept action parameters and call `_action(...)`, but MCP-rendered signatures show null action parameters. No data schemas, APIs, or jobs were returned.

Global issue list returned 8 open BUG issues: four missing `Text` and four missing `Action`. Some default action parameter values reference action IDs that are not present in the installed action list. Treat this as a useful visual landing-page/hero scaffold, not a production-ready functional workflow.

---

## Investigation: Vanilla chatbot

Detailed reference: `references/plugins/vanilla-chatbot.md`.

Current status in inspected app: **no MCP-visible plugin-created objects observed**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). Normal MCP tool channel temporarily returned `ClosedResourceError`, but `hermes mcp test nocodex-mcp` succeeded and the read-only registry fallback returned application data.

Searches for `chatbot`, `chat`, `vanilla`, and `message` across relevant actions, data schemas, APIs, and jobs returned no results. Full app inventory returned no APIs, no data schemas, no actions, no jobs, and no issues. Templates were only the baseline/default error and LottieFiles templates.

If the rendered UI confirms that `Vanilla chatbot` is installed, treat it as likely empty, placeholder, failed-to-install, UI-only, or installed in a different application until rechecked in the browser UI or reinstalled in a clean app with before/after diffing.

---

## Investigation: Mailjet integration

Detailed reference: `references/plugins/mailjet-integration.md`.

Current status in inspected app: **no MCP-visible plugin-created objects observed**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). Searches for `mailjet` across actions, data schemas, APIs, and jobs returned no results. Full app inventory returned no APIs, no data schemas, no actions, no jobs, and no issues. Templates were only the baseline/default error and LottieFiles templates.

If the rendered UI confirms that `Mailjet integration` is installed, treat it as likely empty, placeholder, failed-to-install, or UI-only until rechecked in the browser UI or reinstalled in a clean app with before/after diffing.

---

## Investigation: Jotform Dashboard

Detailed reference: `references/plugins/jotform-dashboard.md`.

Current status in inspected app: **no MCP-visible plugin-created objects observed**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP returned no APIs, actions, data schemas, jobs, Jotform/dashboard-specific templates, or issues. Searches for `jotform`, `form`, and `dashboard` across actions, APIs, schemas, jobs, and apps also returned no relevant matches.

If the rendered UI confirms that `Jotform Dashboard` is installed, treat it as likely empty/placeholder/failed-content plugin until NoCode-X clarifies intended behavior.

---

## Investigation: DATA PIPELINE

Detailed reference: `references/plugins/data-pipeline.md`.

Current status in inspected app: **no MCP-visible plugin-created objects observed**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). MCP returned no APIs, actions, data schemas, jobs, plugin-specific templates, or issues. Searches for `pipeline` across actions, APIs, schemas, and jobs also returned no matches.

If the rendered UI confirms that `DATA PIPELINE` is installed, treat it as likely empty/placeholder/failed-content plugin until NoCode-X clarifies intended behavior.

---

## Observed Plugin: Dropbox API

Detailed reference: `references/plugins/dropbox-api.md`.

Observed in workspace `PF panel`, application `Unnamed Application` after MCP OAuth authorization. The rendered UI was reported by the user to show `Dropbox API` as a separate plugin under Plugins; MCP folder listing returned only `Root` and `Plugins`, so nested UI folder structure is not fully visible via `list_all_folders`.

### Purpose

Dropbox integration plugin for OAuth/access-token handling and Dropbox file/folder operations.

### Installed/Observed Folders

- `Plugins` (`list_all_folders`)
- Nested UI package `Dropbox API`: reported by user; not returned by current MCP folder list.

### Installed/Observed APIs

- None returned by `list_all_apis` for the inspected application.

### Installed/Observed Jobs

- None returned by `list_all_jobs` for the inspected application.

### Installed/Observed Templates

The application had generic/support templates, not clearly attributable to Dropbox from MCP alone:

- `Error: not authorized`
- `Error: not found`
- `Error: unknown error`
- `LottieFiles component`

### Actions

#### `Dropbox: get access token`

- ID: `[REDACTED_ID]`
- Purpose: exchanges/stores Dropbox access token using Dropbox app configuration.
- JavaScript shape observed:
  - `_start()`
  - logs an authorization URL/code placeholder (`AUTHORIZATION CODE` log line; full URL content not recoverable from MCP output)
  - `_getfirstfiltereddatav3` reads first `Dropbox API Configuration` record (`dataformat_9d91ef39-...`)
  - `_httpformpostv2` uses `BASIC_AUTH`
    - `USERNAME: USER_SERVICE.payload.App_key`
    - `PASSWORD: USER_SERVICE.payload.App_secret`
    - output format: `AccessToken`
  - logs response.
- Required configuration:
  - `Dropbox API Configuration.App_key`
  - `Dropbox API Configuration.App_secret`
  - likely `authorization_code`
- Security note: token-like fields should be treated as secrets; do not expose actual values.

#### `Dropbox: refresh token`

- ID: `[REDACTED_ID]`
- Purpose: refreshes Dropbox access token.
- JavaScript shape observed:
  - `_start()`
  - `_getfirstfiltereddatav3` reads first `Dropbox API Configuration` record
  - `_httpformpostv2` uses `BASIC_AUTH` with app key/secret
  - output format: `AccessToken`
  - logs response.
- Required configuration:
  - Dropbox app key/secret
  - refresh token in configuration or reachable token state.

#### `Dropbox: Create Folder`

- ID: `[REDACTED_ID]`
- Purpose: creates a Dropbox folder.
- Input signature observed: `main(autorename:boolean, path:string)`
- JavaScript shape observed:
  - `_start()`
  - invokes action named `Refresh Token`, referencing `Dropbox: refresh token` by ID
  - `_httpcall` with `AUTHENTICATION_METHOD: 'BEARER'`
  - bearer token expression: `ACCESS_TOKEN.access_token`
  - output format: `Folder`
  - logs response.
- Potential issue: the JS references `ACCESS_TOKEN.access_token` but the visible code snippet did not show where `ACCESS_TOKEN` is assigned from `_action` outputs; verify variable binding in UI if execution fails.

#### `Dropbox: List Folder`

- ID: `[REDACTED_ID]`
- Purpose: lists Dropbox folder contents.
- Input schema: `ListFolderRequest`
- JavaScript shape observed:
  - `_start()`
  - invokes `Refresh Token`
  - `_httpcall` with bearer auth using `ACCESS_TOKEN.access_token`
  - output format observed in JS snippet: `Folder` (`84b36e33-...`), although a separate `ListFolder` output schema exists. Verify mapping in UI; output may be incorrectly mapped or MCP snippet may be incomplete.
  - logs response.
- Dropbox behavior note: if response `has_more` is true, client should continue pagination with Dropbox list-folder-continue semantics; no continuation action was observed in this plugin snapshot.

#### `Dropbox: Create File Request`

- ID: `[REDACTED_ID]`
- Description: `Creates a file request for this user.`
- Input schema: `CreateFileRequest`
- JavaScript shape observed:
  - `_start()`
  - invokes `Refresh Token`
  - `_httpcall` with bearer auth using `ACCESS_TOKEN.access_token`
  - output format: `FileRequest`
  - logs response.

### Data Schemas

#### `AccessToken`

- ID: `[REDACTED_ID]`
- Fields:
  - `access_token` string, classified `SECRET`
  - `token_type` string
  - `expires_in` integer
  - `refresh_token` string, classified `SECRET`
- Use: output of get/refresh token actions.

#### `Dropbox API Configuration`

- ID: `[REDACTED_ID]`
- Fields:
  - `App_key`
  - `App_secret`
  - `authorization_code`
  - `access_token`
  - `refresh_token`
- Use: app-level configuration record consumed by token actions.
- Security note: `App_secret`, `access_token`, and `refresh_token` are sensitive even if the schema metadata did not classify every field as `SECRET`.

#### `CreateFileRequest`

- ID: `[REDACTED_ID]`
- Required fields:
  - `destination`
  - `open`
  - `title`
  - `deadline.deadline`
- Optional/nullable fields observed:
  - `deadline.allow_late_uploads`: enum `none`, `one_day`, `three_days`, `seven_days`
  - `created`
  - `file_count`
  - `url`
- Use: input to `Dropbox: Create File Request`.

#### `FileRequest`

- ID: `[REDACTED_ID]`
- Required output fields:
  - `created`
  - `deadline`
  - `destination`
  - `file_count`
  - `id`
  - `is_open`
  - `title`
  - `url`
- Use: output from create file request.

#### `ListFolderRequest`

- ID: `[REDACTED_ID]`
- Required fields:
  - `path`
- Optional flags:
  - `include_deleted`
  - `include_has_explicit_shared_members`
  - `include_media_info`
  - `include_mounted_folders`
  - `include_non_downloadable_files`
  - `recursive`
- Use: input to `Dropbox: List Folder`.

#### `ListFolder`

- ID: `[REDACTED_ID]`
- Required fields:
  - `cursor`
  - `entries`
- Entry fields include:
  - `.tag`: `file` or `folder`
  - `id`, `name`, `path_display`, `path_lower`
  - `property_groups`, `sharing_info`
  - file-related optional metadata: `client_modified`, `content_hash`, `file_lock_info`, `has_explicit_shared_members`, `is_downloadable`, `rev`, `server_modified`, `size`
- Use: expected output type for Dropbox list folder responses. In the observed JS, `Dropbox: List Folder` mapped output to `Folder`; verify/correct if runtime output validation fails.

#### `Folder`

- ID: `[REDACTED_ID]`
- Required fields:
  - `id`
  - `name`
  - `path_display`
  - `sharing_info`
- Optional/nullable fields:
  - `path_lower`
  - `property_groups`
  - sharing flags: `no_access`, `parent_shared_folder_id`, `read_only`, `traverse_only`
- Use: output for create-folder style operations; observed as output mapping for create/list folder actions.

### Observed Issues / Debugging Notes

High-level application issue list contained 18 open BUG issues after Dropbox plugin installation/partial configuration. Common classes:

- `MISSING_REQUIRED_FIELD`: missing `Text`
- `MISSING_REQUIRED_FIELD`: missing `Authentication method`
- `MISSING_REQUIRED_FIELD`: missing `Data format`
- `UNEXISTING_ACTION_USED`: invocation `Refresh Token` references missing action IDs, including older/deleted IDs and `[REDACTED_ID]`
- `UNEXISTING_DATA_FORMAT_USED`: invocation `Get first from filtered data` references `Dropbox API Configuration` (`9d91ef39-...`) as missing in at least one issue, even though the schema currently exists

Per-action issue calls had inconsistent attribution in the MCP output: some calls returned empty arrays while the global issue list clearly linked issues to Dropbox actions. Prefer `list_all_issues` as the source of truth for global validation state, then cross-check action IDs manually.

### Recommended Setup/Test Flow

1. Ensure one `Dropbox API Configuration` record exists.
2. Fill `App_key` and `App_secret`; treat both as sensitive.
3. Complete Dropbox authorization and store/enter `authorization_code` if the plugin requires manual OAuth exchange.
4. Run `Dropbox: get access token` and verify an `AccessToken` output is produced.
5. Run `Dropbox: refresh token` and verify access token refresh works.
6. Run `Dropbox: Create Folder` with a simple `path` and `autorename` boolean.
7. Run `Dropbox: List Folder` with `path` and optional include flags.
8. Run `Dropbox: Create File Request` with required `destination`, `open`, `title`, and `deadline.deadline`.
9. Re-check `list_all_issues`; remaining `UNEXISTING_*` issues usually indicate broken internal references rather than missing external credentials.

### Installation Strategy Implication

Do not install all plugins into a single research application at once unless the goal is only rough discovery. For reusable Hermes skill knowledge, install or inspect one plugin package at a time and record the plugin-local object set. If UI subfolders are visible but MCP only returns `Plugins`, ask the user for a screenshot or use rendered browser access to confirm the UI hierarchy.
