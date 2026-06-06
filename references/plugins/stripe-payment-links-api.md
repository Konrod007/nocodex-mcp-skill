# Observed Plugin: Stripe | Payment Links API

Status: **observed through MCP fallback; minimal create-payment-link scaffold with validation issues**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). Read-only MCP registry fallback returned application data.

## Current Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)

## Installed Objects

### Actions

- `Stripe | Payment Link: Create a payment link` (`[REDACTED_ID]`)

### Data Schemas

- `Stripe API configuration` (`[REDACTED_ID]`)
  - Contains secret-like `api_key` field classified as `SECRET`.
- `PaymentLink` (`[REDACTED_ID]`)

### APIs / Jobs / Templates

- No first-class NoCode-X API objects returned.
- No scheduled jobs returned.
- No Stripe Payment Links-specific UI templates returned. Existing templates belonged to baseline/default pages and previously installed Vanilla Heroes components.

## Observed Action Implementation Shape

The action signature is:

```text
main(REQUEST:dataformatType_5234433f_9a41_4d15_bdff_23d8e79d9b4fTypePayload)
```

Observed logic pattern:

1. `_start()`
2. Read first `Stripe API configuration` record via `_getfirstfiltereddatav3`.
3. Submit a form POST via `_httpformpostv2`.
4. Use `BASIC_AUTH` with `USERNAME: USER_SERVICE.payload.api_key` and empty/null password.
5. Map response to `PaymentLink` schema.
6. Log response.

MCP-rendered JS endpoint fragment is malformed/truncated:

```text
ENDPOINT:'https:
```

This should be verified in the rendered NoCode-X action editor before runtime use. The pattern matches other Stripe plugins where MCP-rendered endpoint fragments may be lossy or actual action fields may be malformed.

## PaymentLink Schema Summary

The `PaymentLink` schema is broad and includes many Stripe Payment Link fields, including:

- `id`
- `object`
- `active`
- `url`
- `line_items[]`
  - `price`
  - `quantity`
  - `adjustable_quantity`
- `after_completion`
  - `hosted_confirmation.custom_message`
  - `redirect.url`
  - `type`: `hosted_confirmation` / `redirect`
- `allow_promotion_codes`
- `application_fee_amount`
- `application_fee_percent`
- `automatic_tax`
- `billing_address_collection`: `auto` / `required`
- `consent_collection`
- `currency`: currently enum only `usd`
- `custom_fields[]`
- `custom_text`
- `customer_creation`: `always` / `if_required`
- `inactive_message`
- `invoice_creation`
- `livemode`
- `metadata`
- `on_behalf_of`
- `payment_intent_data`
- `payment_method_collection`: `always` / `if_required`
- `payment_method_types[]`
- `phone_number_collection`
- `restrictions.completed_sessions`
- `shipping_address_collection`
- `shipping_options[]`
- `submit_type`: `auto` / `book` / `donate`
- `subscription_data`
- `tax_id_collection`
- `transfer_data`

Quality note: some enums look incomplete or placeholder-like, e.g. `currency` only allows `usd`, and `shipping_address_collection.allowed_countries` enum is `Option1`, `Option2`, `Option3` rather than Stripe country codes.

## Issues

Global issue list returned 7 open BUG issues, all attached to `Stripe | Payment Link: Create a payment link`:

- 2 × missing `Text`
- 2 × missing `Authentication method`
- 2 × missing `Data format`
- 1 × `UNEXISTING_DATA_FORMAT_USED`

The `UNEXISTING_DATA_FORMAT_USED` issue references `Stripe API configuration` (`[REDACTED_ID]`) as non-existing even though the schema is visible. This matches the stale/internal-reference pattern observed in other NoCode-X plugin packages.

## Capability Assessment

Observed capability:

- Create a Stripe Payment Link from a `PaymentLink`-shaped request payload.

Not observed:

- Retrieve payment link.
- List payment links.
- Update/deactivate payment link.
- Retrieve/list line items for a payment link.
- Products/Prices helpers.
- Checkout session or payment intent post-processing.
- Webhook handling for `checkout.session.completed`, `payment_link.*`, etc.
- Signature verification.
- Local persistence of created links/orders.
- Public application API endpoint.
- UI template/page for generating or displaying payment links.
- Jobs or scheduled reconciliation.

## Verdict

Not empty, but extremely narrow. Useful as a starting scaffold for one create operation only. It has a broad response/request schema, but operational coverage is minimal and current validation issues block out-of-the-box reliability.
