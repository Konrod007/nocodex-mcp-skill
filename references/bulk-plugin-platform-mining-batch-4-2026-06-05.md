# Bulk Plugin Platform Mining — Batch 4 — 2026-06-05

Status: **after another plugin batch; analyzed for NoCode-X platform structure/patterns**.

## Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)
- Previous batch reference: `references/bulk-plugin-platform-mining-batch-3-2026-06-05.md`

## Counts After Batch 4

```text
APIs:         2
Data schemas: 81
Actions:      85
Jobs:         0
Templates:    32
Issues:       331
```

Delta vs Batch 3:

```text
APIs:       0
Schemas:    0
Actions:   +21
Jobs:       0
Templates: +11
Issues:    +48
```

## Main Action Groups

```text
Airtable:                    8 actions
Microsoft Outlook:           8 actions
Stripe Checkout:             5 actions
GitLab:                      5 actions
Reddit:                      5 actions
Google Tasks:                4 actions
Jotform:                     4 actions
Stripe | Products:           4 actions
Stripe:                      3 actions
Microsoft Planner:           3 actions
Vimeo:                       3 actions
Microsoft Contacts:          2 actions
Crunchbase:                  2 actions
```

Interesting generic/platform groups:

```text
Process
Test process
Create processor
Train processor
Get processor
Create bucket
Delete bucket
Create object
Delete object
Create folder
Delete folder
Get folder
Insert cards
Insert card
Display features
Add feature to card
Checkout Session Completed
```

## New Platform Primitives vs Known Map

Only two new primitive names appeared beyond the current known map:

```text
_filetobase64
_getvaluefromobjectv2
```

Examples:

```text
_filetobase64:
- Process

_getvaluefromobjectv2:
- Microsoft Outlook: List messages
```

Note: `_getvaluefromobjectv2` is flagged by validation as deprecated:

```text
Invocation "Get value from response" uses deprecated method "getvaluefromobjectv2"
```

## Current Primitive Counts

```text
_start                    85
_logline                  68
_getfirstfiltereddatav3   59
_httpcall                 59
_replaceplaceholders      48
_action                   21
_creategcpaccesstoken     15
_httpformpostv2           11
_createstringvariable      4
_downloadhttpcall          2
_loadmedia                 2
_addtemplatecomponenttohorizontallist 2
_addtemplatecomponenttolist 2
_createobjectfreev2        1
_filetobase64              1
_getvaluefromobjectv2      1
_uploadhttpfilev2          1
_createmedia               1
_settemplateargument       1
```

## Important Structural Lessons

### 1. Google service-account primitive is broader than Gmail

Batch 3 showed `_creategcpaccesstoken` for Gmail. Batch 4 shows it is used across more Google/API workflows:

```text
Google Tasks: Get Task List by id
Google Tasks: Update Task Lists
Google Tasks: Get Tasks List
Google Tasks: Insert Task List
Document/processor-like actions: Process, Create folder, Delete folder, Create object, etc.
```

This confirms `_creategcpaccesstoken` is a reusable platform primitive, not Gmail-specific.

### 2. Microsoft Outlook attachment workflow appears

Microsoft Outlook actions:

```text
Filter messages by Attachments
Get message attachment
Create draft message
Set message categories
List messages
Get message attachments
Filter messages since a certain date
Get message
```

Relevant primitives:

```text
_downloadhttpcall
_action
_getvaluefromobjectv2
```

This adds an email/attachment workflow pattern:

```text
list/filter messages
→ inspect attachments
→ download attachment
→ process/save externally or in media flow
```

### 3. File-to-base64 primitive appears

`_filetobase64` appears in `Process`.

This complements previous file/media primitives:

```text
_texttofile
_uploadhttpfilev2
_downloadhttpcall
_createmedia
_loadmedia
_encodebase64
_filetobase64
_deletemedia
_deleteallmedia
```

NoCode-X has a fairly rich file/media transformation surface.

### 4. Stripe webhook management appears, but not webhook receiver binding

New Stripe actions:

```text
Stripe: Retrieve a webhook endpoint
Stripe: create webhook
```

Current API object:

```text
Stripe: Get webhook
GET /[REDACTED_ID]
actionId: null
```

The platform/plugin can model external webhook endpoint creation/retrieval, but still no MCP-visible API→action binding or webhook signature verification flow.

### 5. Stripe Checkout flow appears

Stripe Checkout actions:

```text
Retrieve Checkout Session line items
List all Checkout Sessions
Retrieve a Session
Expire a Session
Create a Session
```

Plus:

```text
Checkout Session Completed
```

This adds a payment/checkout state pattern. However, it appears as HTTP wrapper + loose event action, not a complete verified webhook flow.

### 6. Form/submission pattern appears through Jotform

Jotform actions:

```text
get user
get form by id
create form
Get Form Submissions
```

Schemas include:

```text
FormSubmissions
FormRequest
```

This is useful for understanding form-submission integrations, though still via external HTTP wrappers.

### 7. Document AI / processor / bucket/object pattern appears

Generic actions observed:

```text
Create processor
Train processor
Get processor
Create bucket
Delete bucket
Create object
Delete object
Create folder
Delete folder
Get folder
Process
Test process
Upload file
test upload
```

Together with:

```text
_filetobase64
_uploadhttpfilev2
_loadmedia
_creategcpaccesstoken
```

This suggests a Google/Document-AI-like workflow:

```text
file/media
→ base64 or upload
→ processor
→ train/process document
→ object/bucket/folder storage
```

This should be treated as a platform pattern candidate, although exact attribution needs deeper inspection.

### 8. Simple card/list UI primitives reappeared but no major new UI mechanism

Templates/actions include:

```text
Cards Page
Display Cards
Feature
Subscription Item
Insert cards
Insert card
Add feature to card
Display features
Fetch prices
```

Primitives:

```text
_addtemplatecomponenttohorizontallist
_addtemplatecomponenttolist
_settemplateargument
```

This reinforces Batch 2's card/list rendering model but does not add a major new UI primitive.

## APIs

Current APIs:

```text
Stripe: Get webhook
- GET /[REDACTED_ID]
- actionId: null
- authenticatedAccess: false

Fetch website information
- GET /website-info
- actionId: null
- authenticatedAccess: false
```

No API with non-null `actionId` was found.

## Jobs

```text
Jobs: 0
```

Scheduled/background job pattern still not discovered.

## Auth / HTTP Summary

Auth methods:

```text
BASIC_AUTH: 73
BEARER:     47
NONE:        8
```

HTTP methods:

```text
GET:    61
POST:   12
DELETE:  4
PATCH:   2
PUT:     2
```

`API_TOKEN` did not appear in this snapshot even though it appeared in Batch 3; again, bulk state is not additive/monotonic.

## Validation / Issue Patterns

Total issues:

```text
331
```

Top issue classes:

```text
126 × Required argument "Text" was empty
70  × Required argument "Authentication method" was empty
52  × Required argument "Data format" was empty
23  × Required argument "Action" was empty
9   × Required output "Response format" was empty
5   × Required argument "Parameter" was empty
4   × Required argument "List ui element" was empty
```

Notable classes:

```text
Action references template that does not exist
Execute action references non-existing action
Google Tasks action references non-existing action
Required argument Endpoint was empty
Deprecated getvaluefromobjectv2
Deprecated addtemplatecomponenttolist
Non-existing data format references
```

This confirms the validation layer checks:

- missing action wiring;
- missing output contracts;
- missing endpoint fields;
- dangling template references;
- deprecated invocation methods.

## Security / Secret Classification Lessons

Correct SECRET examples include:

```text
Google: Service user json.private_key
Google: API Key json.api_key
GitLab Personal_access_tokens / Feed_token / Incoming_email_token
Google service user json variants
Microsoft client_id/client_secret/directory
Vimeo access_token / Personal_Access_Token / Client_secret
Document AI Config.apiKey
Stripe API configuration.api_key
Webhook.secret
Crunchbase Basic_API_Key
```

Review-needed fields not classified as SECRET/suspicious:

```text
AccessToken.access_token
AccessToken.refresh_token
Reddit API Configuration.secret
Reddit API Configuration.access_token
Reddit API Configuration.refresh_token
Jotform API Configuration.API_Key
MicrosoftResponseToken.access_token variants
CustomerSession.client_secret
```

Some false positives remain (`nextPageToken`, `changeKey`, `private_profile`, `resource_key`, price fields), so classification audits need manual filtering.

## Endpoint Rendering Concern

20 actions still show malformed endpoint fragments:

```text
ENDPOINT:'https:this._logline(...
```

Examples:

```text
Stripe: create webhook
Jotform: get user
GitLab: get project's list
Reddit: subreddits/search
Stripe Checkout: Create a Session
Reddit: refresh token
Reddit: get access token
Create bucket
```

## Recommendation

Batch 4 was moderately useful, but less breakthrough than Batch 2/3.

New useful additions:

- `_filetobase64` primitive;
- `_getvaluefromobjectv2` primitive and deprecation signal;
- broader Google service-account usage;
- Outlook email/attachment workflow;
- Stripe webhook management actions;
- Stripe Checkout flow;
- Jotform forms/submissions;
- Document-AI-like processor/bucket/object workflow.

Still missing:

- jobs;
- API endpoint with non-null `actionId`;
- real webhook receiver + signature verification;
- clearly attached template element actions;
- RBAC/permission primitives;
- transaction/relation primitives.

Continue at most one more batch if available, but if it only adds HTTP wrappers and no jobs/API bindings/webhook verification/template element bindings, consolidate the platform map instead.
