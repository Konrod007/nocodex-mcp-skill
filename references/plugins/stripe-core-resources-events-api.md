# NoCode-X Plugin: Stripe | Core Resources | Events API

Status: **observed through MCP; partial Stripe Events read integration with setup/packaging issues**.

Observed in workspace `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`), application `Unnamed Application` (`[REDACTED_ID]`).

Normal MCP tool calls temporarily returned `ClosedResourceError`; data below was collected read-only through the documented Hermes MCP registry fallback after `hermes mcp test nocodex-mcp` confirmed the server was reachable.

## Purpose

Stripe Events API integration focused on reading Stripe events.

Despite the package name `Stripe | Core Resources | Events API`, the installed object set covers only two read operations:

- retrieve one event by ID;
- list events.

No webhook endpoint receiver, event persistence/sync job, event filtering UI, or broader Stripe resource actions were observed.

## Installed/Observed APIs

- None returned by `list_all_apis`.
- Keyword API searches for `stripe` and `event` returned no APIs.

## Installed/Observed Jobs

- None returned by `list_all_jobs`.
- Keyword job searches for `stripe` and `event` returned no jobs.

## Installed/Observed Templates

Only baseline/default templates were returned:

- `Error: not authorized`
- `Error: unknown error`
- `Error: not found`
- `LottieFiles component`

No Stripe/Event-specific UI templates were observed.

## Installed/Observed Folders

MCP returned only:

- `Plugins`
- `Root`

No nested Stripe package folder was visible through MCP. Rendered UI may still show plugin subfolders not exposed by current MCP folder listing.

## Installed/Observed Actions

### `Stripe Events: Retrieve an event`

- ID: `[REDACTED_ID]`
- Input signature observed: `main(eventId:string)`
- Intended method: `GET`
- Output schema reference: `Event` (`[REDACTED_ID]`)
- Uses configuration schema `Stripe API configuration` (`[REDACTED_ID]`) through `_getfirstfiltereddatav3`.
- Auth observed in JS: `BASIC_AUTH`
  - `USERNAME: USER_SERVICE.payload.Secret_key`
  - `PASSWORD: null`
- Expected Stripe endpoint, based on action purpose: likely `GET https://api.stripe.com/v1/events/{eventId}`.
- MCP-rendered JS endpoint fragment looked malformed/truncated: `TEXT:'https:let {RESPONSE...` rather than a clean URL.

### `Stripe Events: List all events`

- ID: `[REDACTED_ID]`
- Input signature observed: `main()`
- Intended method: `GET`
- Output schema reference: `EventsList` (`[REDACTED_ID]`)
- Uses configuration schema `Stripe API configuration` (`[REDACTED_ID]`) through `_getfirstfiltereddatav3`.
- Auth observed in JS: `BASIC_AUTH`
  - `USERNAME: USER_SERVICE.payload.Secret_key`
  - `PASSWORD: null`
- Expected Stripe endpoint, based on action purpose: likely `GET https://api.stripe.com/v1/events`.
- MCP-rendered JS endpoint fragment looked malformed/truncated: `ENDPOINT:'https:this._logline...` rather than a clean URL.
- No inputs were observed for common Stripe list-events query parameters such as `limit`, `starting_after`, `ending_before`, `created`, `type`, or `delivery_success`.

## Installed/Observed Data Schemas

### `Stripe API configuration`

- ID: `[REDACTED_ID]`
- Title in JSON schema: `UserService`
- Fields:
  - `Publishable_key` — `SECRET`
  - `Secret_key` — `SECRET`
- Required fields: none.

Security note: Treat Stripe keys as sensitive. Do not copy real values into docs/logs/chat. In practice the `Secret_key` should be a Stripe secret key (`sk_test_...` / `sk_live_...`), and `Publishable_key` is not needed for server-side Events API reads.

### `EventsList`

- ID: `[REDACTED_ID]`
- Top-level fields observed:
  - `object`
  - `url`
  - `has_more`
  - `data[]`
- `data[]` event fields include:
  - `id`
  - `object`
  - `api_version`
  - `created`
  - `data.object`
  - `livemode`
  - `pending_webhooks`
  - `request.id`
  - `request.idempotency_key`
  - `type`
- The nested `data.object` schema appears tailored around a SetupIntent-like object rather than generic Stripe event payloads. It includes fields such as `automatic_payment_methods`, `client_secret`, `payment_method_options`, `payment_method_types`, `status`, and `usage`.

### `Event`

- ID: `[REDACTED_ID]`
- Fields observed are broadly similar to `EventsList.data[]`:
  - `id`
  - `object`
  - `api_version`
  - `created`
  - `data.object`
  - `livemode`
  - `pending_webhooks`
  - `request.id`
  - `request.idempotency_key`
  - `type`
- As with `EventsList`, `data.object` appears modeled around a specific Stripe resource shape, not the polymorphic payloads that real Stripe events can contain.

## Capabilities Documented

Observed/expected capabilities from installed objects:

1. Store Stripe API configuration keys.
2. Retrieve one Stripe event by ID.
3. List Stripe events.
4. Log raw/mapped responses to application logs.

Not observed in this plugin snapshot:

- webhook endpoint receiver;
- webhook signature verification with endpoint secret;
- event ingestion/persistence table;
- scheduled polling/sync job;
- pagination controls for event listing;
- filters by event type/date/delivery success;
- replay/event processing workflow;
- event deduplication/idempotency handling;
- broader Stripe resources such as customers, subscriptions, payment intents, invoices, checkout sessions, products, prices, refunds, disputes, etc.

## Observed Issues / Validation Notes

Global `list_all_issues` returned 16 open BUG issues:

- `MISSING_REQUIRED_FIELD`: 14
  - missing `Text`
  - missing `Authentication method`
  - missing `Data format`
- `UNEXISTING_DATA_FORMAT_USED`: 2
  - actions reference `Stripe API configuration` (`[REDACTED_ID]`) as non-existing, even though the schema is visible via `list_all_dataschemas` and `get_dataschema`.

Per-action `list_action_issues` returned empty arrays for both actions, while the global issue list linked issues to both action IDs. Prefer global issue list as source of truth, as with other plugin audits.

Important interpretation:

- Missing auth/text/data-format fields may be normal post-install setup debt until credentials/action settings are configured.
- `UNEXISTING_DATA_FORMAT_USED` against a currently visible schema is suspicious and may indicate stale internal references, validation cache, or plugin packaging issue if it persists after refresh/setup.
- Malformed endpoint fragments in MCP-rendered JS are suspicious, but verify in the rendered action editor before classifying as a hard endpoint defect.

## JavaScript / Logic Notes

Observed JS pattern:

- `_start()`
- `_getfirstfiltereddatav3` reads first `Stripe API configuration` record.
- `_httpcall` invokes a Stripe endpoint with `BASIC_AUTH` using the secret key as username and `null` password.
- `_logline` logs the response.

Stripe accepts HTTP Basic auth with the secret key as username and an empty password, so the auth strategy can be valid in principle. However, action validation currently reports missing authentication method, and the MCP-rendered JS endpoint strings appear malformed/truncated.

## Setup/Test Flow

1. Create/fill one `Stripe API configuration` record.
2. Use a Stripe test-mode secret key first; never expose the real key in chat/log docs.
3. Open `Stripe Events: Retrieve an event` in the action editor first because it is read-only.
4. Confirm endpoint is exactly the Stripe Events retrieve URL and contains the `eventId` placeholder.
5. Confirm auth method is Basic Auth with `Secret_key` as username and empty/null password.
6. Test against a controlled Stripe test event ID.
7. Test `Stripe Events: List all events` with a low limit if query parameters are available; if not, note that pagination/filter controls are absent.
8. Re-run `list_all_issues`; persistent `UNEXISTING_DATA_FORMAT_USED` or malformed endpoint/auth issues should be reported.

## Usefulness Assessment

Useful as a small read-only starting scaffold for Stripe event inspection.

Not sufficient for production Stripe event processing because it lacks webhook receiver/signature verification, storage, deduplication, processing logic, retries, filtering, and pagination controls.

For real Stripe automation, the next missing pieces would be:

- webhook endpoint/API in NoCode-X;
- Stripe webhook signature verification using endpoint secret;
- persisted `StripeEvent` schema/table with event id, type, created, livemode, payload, processed status;
- idempotent event processing action;
- list/retrieve actions with pagination and filters;
- resource-specific actions for customers/subscriptions/payments/invoices depending on app use case.

## Developer Issue

A reportable issue should include:

- 16 open global BUG issues after installation;
- `UNEXISTING_DATA_FORMAT_USED` references visible `Stripe API configuration` schema;
- per-action issue calls return empty while global issue list links issues to actions;
- MCP-rendered JS endpoint fragments appear malformed/truncated;
- `EventsList`/`Event` schemas model `data.object` as a specific SetupIntent-like payload rather than generic polymorphic Stripe event payloads;
- plugin name suggests Events API but lacks webhook receiver/signature verification and practical event-processing workflow.
