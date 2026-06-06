# Mailchimp API Plugin

Status: **observed through MCP**.

Observed in workspace `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`), application `Unnamed Application` (`[REDACTED_ID]`).

## Purpose

Mailchimp/Mandrill-style transactional email integration plugin.

Important naming note: although the plugin is named `Mailchimp API`, the installed configuration field is `mandrill_api_key`, and the schemas/actions focus on sending messages, templates, and user/account info. Treat this as closer to **Mailchimp Transactional / Mandrill** than Mailchimp Marketing audience/list management unless future evidence shows additional Marketing API objects.

## Installed/Observed APIs

- None returned by `list_all_apis`.
- `search_apis("Mailchimp")` returned `[]`.

Interpretation: plugin is represented by actions and data schemas, not as ordinary NoCode-X API objects in the current MCP surface.

## Installed/Observed Actions

### `Mailchimp: Get user info`

- ID: `[REDACTED_ID]`
- Purpose: fetch Mailchimp/Mandrill account/user information.
- Observed output schema reference: `User` (`[REDACTED_ID]`).
- Related input schema: `GetUserRequest` (`[REDACTED_ID]`).

Expected capability:

- retrieve username/public ID/reputation/quota/backlog;
- retrieve delivery stats for today, last 7/30/60/90 days, and all-time.

### `Mailchimp: Send new message`

- ID: `[REDACTED_ID]`
- Purpose: send a transactional email message without a stored template.
- Observed output schema reference: `Message` (`[REDACTED_ID]`).
- Related input schema: `MessageRequest` (`[REDACTED_ID]`).

Expected capability:

- send HTML/text email;
- configure subject, sender, recipients;
- set tracking options;
- use merge vars/tags/subaccount/metadata;
- include attachments and inline images;
- optionally schedule via `send_at`;
- optionally use `async` and `ip_pool`.

### `Mailchimp: Send using message template`

- ID: `[REDACTED_ID]`
- Purpose: send a transactional email using a stored template.
- Observed output schema reference: `Message` (`[REDACTED_ID]`).
- Related input schema: `MessageTemplate` (`[REDACTED_ID]`).

Expected capability:

- send by `template_name`;
- pass `template_content`;
- include the same message options as raw sends;
- schedule/async/send via IP pool.

### `Mailchimp: Add template`

- ID: `[REDACTED_ID]`
- Purpose: create/add a message template.
- Observed output schema reference: `Template` (`[REDACTED_ID]`).
- Related input schema: `TemplateRequest` (`[REDACTED_ID]`).

Expected capability:

- create template with name, subject, sender, HTML code, text version, labels, and publish flag.

### `Mailchimp: Get template info`

- ID: `[REDACTED_ID]`
- Purpose: retrieve stored template information.
- Observed output schema reference: `Template` (`[REDACTED_ID]`).
- Related schemas: `TemplateRequest`, `Template`, `TemplateContent`.

Expected capability:

- retrieve template metadata/content such as slug, name, labels, code, subject, sender, published fields, timestamps, and broken-template flag.

## Installed/Observed Data Schemas

### `Mailchimp API configuration`

- ID: `[REDACTED_ID]`
- Fields:
  - `mandrill_api_key`: string, `dataClassification: SECRET`

Setup note: this field must be configured after plugin installation. Never expose the actual value.

### `GetUserRequest`

- ID: `[REDACTED_ID]`
- Fields:
  - `key`: string

Likely request input for account/user info. The plugin also has central `mandrill_api_key` config; verify in UI whether `key` is populated manually or copied from config by action logic.

### `User`

- ID: `[REDACTED_ID]`
- Fields include:
  - `username`
  - `created_at`
  - `public_id`
  - `reputation`
  - `hourly_quota`
  - `backlog`
  - `stats.today.*`
  - `stats.last_7_days.*`
  - `stats.last_30_days.*`
  - `stats.last_60_days.*`
  - `stats.last_90_days.*`
  - `stats.all_time.*`

Stats fields include sent, hard/soft bounces, rejects, complaints, unsubs, opens, unique opens, clicks, and unique clicks.

### `MessageRequest`

- ID: `[REDACTED_ID]`
- Description: `Schema for a message request containing async status, IP pool, and scheduled sending time.`
- Required fields observed:
  - `key`
  - `async`
  - `ip_pool`
  - `send_at`
- Important nested fields:
  - `message.html`
  - `message.text`
  - `message.subject`
  - `message.from_email`
  - `message.from_name`
  - `message.to[].email`
  - `message.to[].name`
  - `message.to[].type`
  - `message.headers`
  - `message.important`
  - `message.track_opens`
  - `message.track_clicks`
  - `message.auto_text`
  - `message.auto_html`
  - `message.inline_css`
  - `message.url_strip_qs`
  - `message.preserve_recipients`
  - `message.view_content_link`
  - `message.bcc_address`
  - `message.tracking_domain`
  - `message.signing_domain`
  - `message.return_path_domain`
  - `message.merge`
  - `message.merge_language`
  - `message.global_merge_vars[].name/content`
  - `message.merge_vars[].rcpt/vars[]`
  - `message.tags[]`
  - `message.subaccount`
  - `message.google_analytics_domains[]`
  - `message.google_analytics_campaign`
  - `message.metadata`
  - `message.recipient_metadata[]`
  - `message.attachments[].type/name/content`
  - `message.images[].type/name/content`

### `MessageTemplate`

- ID: `[REDACTED_ID]`
- Description: `Schema representing a template for sending messages, including asynchronous sending options, IP pool assignment, and scheduled time for sending.`
- Required fields observed:
  - `key`
  - `template_name`
  - `template_content`
  - `message`
  - `async`
  - `ip_pool`
  - `send_at`
- Message object has broadly the same options as `MessageRequest`.

### `Message`

- ID: `[REDACTED_ID]`
- Description: `Schema representing the structure of a message containing information about email delivery status.`
- Fields:
  - `messages[].email`
  - `messages[].status`
  - `messages[].reject_reason`
  - `messages[].queued_reason`
  - `messages[]._id`

### `TemplateRequest`

- ID: `[REDACTED_ID]`
- Fields:
  - `key`
  - `name`
  - `from_email`
  - `from_name`
  - `subject`
  - `code`
  - `text`
  - `publish`
  - `labels[]`

### `Template`

- ID: `[REDACTED_ID]`
- Fields:
  - `slug`
  - `name`
  - `labels[]`
  - `code`
  - `subject`
  - `from_email`
  - `from_name`
  - `text`
  - `publish_name`
  - `publish_code`
  - `publish_subject`
  - `publish_from_email`
  - `publish_from_name`
  - `publish_text`
  - `published_at`
  - `created_at`
  - `updated_at`
  - `is_broken_template`

### `TemplateContent`

- ID: `[REDACTED_ID]`
- Fields:
  - `TemplateContent.name`
  - `TemplateContent.content`

## Capabilities Documented

Observed/expected capabilities from installed objects:

1. Store a Mailchimp Transactional/Mandrill API key as secret configuration.
2. Retrieve user/account status and sending statistics.
3. Send transactional emails directly.
4. Send transactional emails via named templates.
5. Create/publish templates.
6. Retrieve template metadata/content.
7. Support advanced email options: tracking, merge vars, tags, subaccount, analytics campaign, attachments, inline images, recipient metadata, scheduled sending, async sending, and IP pool.

Not observed in this plugin snapshot:

- Mailchimp Marketing audience/list management;
- subscriber CRUD;
- campaigns/newsletters;
- automations/journeys;
- segments/tags for audiences;
- webhooks;
- OAuth flow;
- first-class NoCode-X API objects.

## Post-Install Setup Requirements

Expected after installation:

1. Create or fill one `Mailchimp API configuration` record.
2. Set `mandrill_api_key`; treat it as secret.
3. Confirm whether action request schemas require `key` manually or whether the action pulls it from central configuration.
4. Configure action HTTP authentication/API-key binding if the UI requires manual setup.
5. Configure missing request/response data formats if validation issues remain.
6. Test `Mailchimp: Get user info` first because it is lower-risk than sending email.
7. Test `Mailchimp: Add template` / `Get template info` with a harmless template.
8. Test sending only to a controlled test address.

## Observed Issues / Validation Notes

Global issue list after installation included 19 open BUG issues linked to Mailchimp actions. Common classes:

- `MISSING_REQUIRED_FIELD`: `Authentication method`
- `MISSING_REQUIRED_FIELD`: `Data format`
- `MISSING_REQUIRED_FIELD`: `Text`
- `UNEXISTING_DATA_FORMAT_USED`: invocations referencing `Mailchimp API configuration` (`[REDACTED_ID]`) as non-existing despite the schema being visible via `list_all_dataschemas`

Important interpretation:

- Missing auth/text/data-format fields can be expected immediately after plugin installation because authorization and setup happen post-install.
- Persistent `UNEXISTING_DATA_FORMAT_USED` after configuration/refresh may indicate stale internal references, validation cache, or plugin packaging issue.

## JavaScript / Logic Notes

`get_action_javascript` for all five actions returned TypeScript-like generated bodies, but endpoint extraction showed malformed/truncated endpoint fragments like:

```text
ENDPOINT:'https:this._logline({NCX_NAME:
```

This same pattern has appeared in other unconfigured plugins. Treat it as suspicious but not conclusive until after post-install configuration and rendered action-editor inspection.

Observed JS pattern across actions:

- `_start()`
- `_getfirstfiltereddatav3` reading `Mailchimp API configuration`
- `_httpcall`
- `_logline`

## Security Notes

- Never expose actual Mailchimp/Mandrill API keys.
- Treat `mandrill_api_key` and any request `key` fields as secrets.
- Redact keys in docs/logs/screenshots as `[REDACTED]`.

## Recommended Test Flow

1. Fill `Mailchimp API configuration.mandrill_api_key`.
2. Open `Mailchimp: Get user info` in the action editor.
3. Confirm endpoint/auth/request data format.
4. Run `Get user info`; verify `User` output.
5. Add a harmless test template via `Mailchimp: Add template`.
6. Retrieve it via `Mailchimp: Get template info`.
7. Send a message to a controlled test inbox using `Mailchimp: Send new message`.
8. Send via template using `Mailchimp: Send using message template`.
9. Re-run `list_all_issues`; classify remaining `UNEXISTING_*` and malformed endpoint issues as potential plugin/platform defects.
