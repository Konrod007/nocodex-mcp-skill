# NoCode-X Plugin: VIES VAT Validation

Status: **observed through MCP; minimal public VAT validation action with packaging/setup issues**.

Observed in workspace `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`), application `Unnamed Application` (`[REDACTED_ID]`).

## Purpose

VIES/VAT validation integration for checking whether a VAT number is valid for a country.

The installed object set is very small:

- one action to check VAT validity;
- one response schema.

No config schema, auth secrets, NoCode-X APIs, jobs, or UI templates were observed.

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

No VIES/VAT-specific UI templates were observed.

## Installed/Observed Actions

### `Vies: Check VAT Validity`

- ID: `[REDACTED_ID]`
- Input signature observed: `main(VAT:string,COUNTRY:string)`
- Method observed: `GET`
- Auth observed: `NONE`
- Output schema reference: `Vat Validity response` (`[REDACTED_ID]`)
- Uses `_replaceplaceholders` to construct endpoint.
- MCP-rendered JS endpoint fragment looked malformed/truncated: `TEXT:'https:let {RESPONSE...` rather than a clean URL.

Likely intended behavior:

- validate a VAT number (`VAT`) for a given country (`COUNTRY`) against a public VIES/VAT validation service.

Because the endpoint text was not recoverable from MCP-rendered JS, verify the real endpoint in the rendered action editor before relying on the action.

## Installed/Observed Data Schemas

### `Vat Validity response`

- ID: `[REDACTED_ID]`
- Fields observed:
  - `isValid` — boolean
  - `requestDate` — string
  - `userError` — string
  - `naem` — string
  - `address` — string
  - `originalVatNumber` — string
  - `vatNumber` — string
- Required fields: none.

Schema issue:

- Field `naem` appears to be a typo and likely should be `name`.

## Observed Issues / Validation Notes

Global `list_all_issues` returned 4 open BUG issues linked to `Vies: Check VAT Validity`:

- `MISSING_REQUIRED_FIELD`: missing `Text` — 2 occurrences.
- `MISSING_REQUIRED_FIELD`: missing `Authentication method` — 2 occurrences.

Per-action `list_action_issues` returned an empty array, while global issues linked issues to the action ID. Prefer global `list_all_issues` as source of truth.

Important interpretation:

- `Authentication method` missing is odd because the MCP-rendered JS shows `AUTHENTICATION_METHOD:'NONE'`.
- `Text` missing aligns with the malformed/truncated endpoint string observed in MCP-rendered JS.
- There were no `UNEXISTING_DATA_FORMAT_USED` issues for this plugin snapshot.

## JavaScript / Logic Notes

Observed JS pattern:

- `_start()`
- `_replaceplaceholders` builds endpoint from `VAT` and `COUNTRY` inputs.
- `_httpcall` runs `GET` with `AUTHENTICATION_METHOD:'NONE'`.
- Output format is `Vat Validity response`.

Unlike Stripe/Trello/Dropbox, this plugin does not need external credentials if it calls a public VIES endpoint or public validation wrapper.

## Setup/Test Flow

1. Open `Vies: Check VAT Validity` in the action editor.
2. Verify the endpoint is a valid URL and contains placeholders for country and VAT number.
3. Verify auth method is explicitly set to `NONE` if the service is public.
4. Test with a known valid EU VAT number and country code.
5. Test with an invalid VAT number.
6. Confirm response maps to `isValid`, `requestDate`, `userError`, `name`/`naem`, `address`, `originalVatNumber`, and `vatNumber`.
7. Re-run `list_all_issues`; persistent missing `Text` or `Authentication method` should be reported.

## Usefulness Assessment

Useful as a minimal scaffold for VAT number validation.

Not production-ready until endpoint/auth validation issues are resolved and the schema typo `naem` is clarified or fixed.

Missing production features:

- clean schema field name `name`;
- explicit error taxonomy for VIES downtime, invalid country, invalid VAT format, rate limits/timeouts;
- retry/timeout behavior;
- optional caching to avoid repeated checks;
- normalization of input VAT number/country code;
- audit logging of validation attempts if used for checkout/B2B tax flows.

## Developer Issue

A reportable issue should include:

- action has 4 global BUG issues after installation;
- global issues report missing `Text` and `Authentication method` even though action JS shows `AUTHENTICATION_METHOD:'NONE'`;
- MCP-rendered JS endpoint fragment appears malformed/truncated;
- response schema has typo field `naem`, likely intended `name`;
- per-action issue call returns empty while global issues link the action ID.
