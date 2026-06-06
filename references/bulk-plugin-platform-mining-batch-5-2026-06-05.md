# Bulk Plugin Platform Mining — Batch 5 — 2026-06-05

Status: **after another plugin batch; analyzed for NoCode-X platform structure/patterns**.

## Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)
- Previous batch reference: `references/bulk-plugin-platform-mining-batch-4-2026-06-05.md`

## Counts After Batch 5

```text
APIs:         2
Data schemas: 142
Actions:      148
Jobs:         0
Templates:    31
Issues:       557
```

Delta vs Batch 4:

```text
APIs:       0
Schemas:   +61
Actions:   +63
Jobs:       0
Templates:  -1
Issues:   +226
```

This is the largest current snapshot by actions/schemas/issues.

## Main Action Groups

```text
Open AI:                    15 actions
ScrapingBee:                 7 actions
Google Docs:                 6 actions
Microsoft To-do task list:   6 actions
Create scrape:               6 actions
Delete all:                  5 actions
Bitbucket:                   5 actions
Google Photos:               5 actions
Google Calendar Event:       4 actions
Microsoft OneNote:           4 actions
Microsoft List:              4 actions
SendGrid:                    4 actions
Google Calendar:             4 actions
GitHub:                      4 actions
Microsoft Bookings:          4 actions
TOPdesk incidents:           4 actions
SurveyMonkey:                3 actions
Upload file:                 3 actions
Mollie:                      3 actions
Microsoft Teams:             3 actions
Google Forms/forms:          4 actions combined
PDFMonkey:                   2 actions
EmailIt:                     2 actions
Google Drive:                2 actions
Google Contact:              2 actions
Microsoft Site:              2 actions
Search/Chat assistant:       2 actions
Fetch website assistant:     2 actions
```

## New Platform Primitives vs Known Map

Batch 5 added the following previously unseen primitive names:

```text
_clearform
_getfirstfiltereddatav2
_mapformdatatoobject
_round
_setanswerofinputfield
_showsnackbar
```

Examples:

```text
_clearform:
- Clear form: EmailIt API Configuration

_mapformdatatoobject:
- Save form: EmailIt API Configuration

_setanswerofinputfield:
- Load form: EmailIt API Configuration

_showsnackbar:
- Save form: EmailIt API Configuration

_getfirstfiltereddatav2:
- Open AI: Create chat completion

_round:
- Mollie: List payments
```

## Current Primitive Counts

```text
_start                    148
_getfirstfiltereddatav3   110
_logline                  109
_httpcall                  96
_replaceplaceholders       78
_action                    41
_creategcpaccesstoken      28
_createobjectdata          11
_downloadhttpcall           8
_httpformpostv2             7
_uploadhttpfilev2           5
_getbaseurl                 5
_createstringvariable       5
_createmedia                4
_updatedata                 4
_updateobjectfreev2         4
_createobjectfreev2         4
_stripanchorsfromurl        4
_deletedatabydataformatid   3
_scrape                     3
_selectlinksfromhtml        3
_loadmedia                  3
_deleteallmedia             2
_getdatav2                  2
_htmltomarkdown             2
_objecttojson               2
_texttofile                 2
_wait                       2
_getfiltereddatav3          2
_getdataformatjsonschema    2
_getobjectfromlist          2
_objecttostring             2
_setanswerofinputfield      1
_mapformdatatoobject        1
_showsnackbar               1
_clearform                  1
_getfirstfiltereddatav2     1
_getvaluefromobject         1
_round                      1
```

## Important Structural Lessons

### 1. Native form/configuration UI primitives finally appeared

This is the most important Batch 5 novelty.

Actions:

```text
Load form: EmailIt API Configuration
Save form: EmailIt API Configuration
Clear form: EmailIt API Configuration
```

Primitives:

```text
_setanswerofinputfield
_mapformdatatoobject
_showsnackbar
_clearform
_getdatav2
_updatedata
```

This reveals a NoCode-X pattern for configuration forms:

```text
Load existing config record
→ set input field answers
→ user edits form
→ map form data to object
→ create/update data record
→ show snackbar feedback
→ clear form if needed
```

This is a major missing piece in the platform map. It explains how settings/config pages may be wired to data schemas.

### 2. OpenAI vector-store/file API surface appears extensively

OpenAI actions:

```text
Retrieve vector store
Modify vector store
Create vector store
List vector stores
Delete vector store
Create vector store file
List vector store files
Delete vector store file
Upload file
Retrieve file
Retrieve file content
List files
Delete file
Create chat completion
```

This is stronger than the earlier Pinecone-only assistant flow. It shows a direct OpenAI vector-store/file lifecycle pattern:

```text
media/file
→ upload to OpenAI
→ vector store
→ vector store file
→ retrieve/list/delete
→ chat completion
```

### 3. Scraping pipeline repeats and deepens

Groups:

```text
ScrapingBee: scroll/screenshot/html/google search/cookies-xhr/ajax
Create scrape request(s)
Scrape URL
Fetch website information from assistant
Create file in vector store
Search/Chat with assistant
```

Primitives:

```text
_scrape
_selectlinksfromhtml
_stripanchorsfromurl
_htmltomarkdown
_texttofile
_getbaseurl
_getdataformatjsonschema
_objecttojson
_objecttostring
```

This confirms the web ingestion/RAG pattern is not incidental; it appears repeatedly across batches.

### 4. Google Workspace coverage expands greatly

Google groups:

```text
Google Docs
Google Forms/forms
Google Photos
Google Calendar
Google Calendar Event
Google Drive
Google Contact
```

Common primitive:

```text
_creategcpaccesstoken
```

This confirms service-account/GCP token is a broad platform integration pattern for Google APIs.

### 5. Microsoft Graph coverage expands

Microsoft groups:

```text
Microsoft To-do task list
Microsoft OneNote
Microsoft List
Microsoft Bookings
Microsoft Teams
Microsoft Site
```

Together with prior Outlook/Planner/Contacts, this shows Microsoft Graph integrations are modeled as many small HTTP wrapper actions with shared token config schemas and `_action` composition.

### 6. Email/contact/campaign patterns appear

Actions:

```text
SendGrid: Create an Event Webhook
SendGrid: Retrieve all bounces
SendGrid: Send single email
SendGrid: Add or Update a Contact
EmailIt: Send Emails
EmailIt: Create an Audience
Get Campaignlist / Get Campaign
```

This adds practical email-marketing patterns:

```text
send email
manage contacts/audiences
fetch campaigns/bounces
create external event webhook
```

Still no NoCode-X webhook receiver/signature verification binding.

### 7. External webhook creation appears again, but receiver binding still absent

SendGrid exposes:

```text
SendGrid: Create an Event Webhook
```

But APIs are still:

```text
Fetch website information
Fetch website information_1
both GET /website-info
actionId: null
```

So the platform/package can create webhook endpoints in external services, but the NoCode-X API objects still do not expose action binding through MCP.

### 8. RBAC/permissions appear only as external API data, not platform permissions

Mentions include `permission` and actions like:

```text
Google drive: Share file
```

But this is external Google Drive permission management, not NoCode-X RBAC. No native RBAC/role primitive was found.

### 9. Finance/payment patterns expand

Actions:

```text
Mollie: Create payment
Mollie: Get payment
Mollie: List payments
```

`_round` appears in `Mollie: List payments`, likely numeric/currency formatting.

This complements previous Stripe Checkout patterns.

## APIs

Current APIs:

```text
Fetch website information
- GET /website-info
- actionId: null
- authenticatedAccess: false

Fetch website information_1
- GET /website-info
- actionId: null
- authenticatedAccess: false
```

Still no API with non-null `actionId`.

## Jobs

```text
Jobs: 0
```

Scheduled/background jobs are still absent after five bulk batches.

## Auth / HTTP Summary

Auth methods:

```text
BASIC_AUTH: 115
BEARER:      89
NONE:        20
```

HTTP methods:

```text
GET:    104
POST:    22
PUT:      8
DELETE:   3
PATCH:    1
```

## Validation / Issue Patterns

Total issues:

```text
557
```

Top issue classes:

```text
212 × Required argument "Text" was empty
126 × Required argument "Authentication method" was empty
96  × Required argument "Data format" was empty
40  × Required argument "Action" was empty
14  × Required output "Response format" was empty
5   × Required argument "Data-format" was empty
3   × deprecated createobjectdata
3   × FOUND_DATA may be null without null-check
3   × Required argument "Id" was empty
2   × Required argument "File" was empty
2   × deprecated getvaluefromobject
2   × Required argument "UI element" was empty
```

Notable issue types:

```text
non-existing data format references
non-existing action references
missing output RESPONSE
Data-format to jsonschema references non-existing data format
Delete all data of a data-format references non-existing data format
unused API call invocation
missing UI element
```

This further confirms validation coverage for:

- action wiring;
- data schema references;
- UI element references;
- output contracts;
- null-safety;
- deprecated methods;
- unused invocations.

## Security / Secret Classification Lessons

Correct SECRET examples include:

```text
OpenAI config.api_token
Assistant Config.apiKey / Personal_access_token
Google service-user private_key/client fields in several variants
Google API keys
SendGrid API_Key
Microsoft client_id/client_secret
Scrape Config.apiKey
Pinecone apiKey
Woodpecker apiKey
PDFMonkey API_Secret_key
Topdesk Password
Giphy API_Key
Mollie Live_API_key / Test_API_key
```

Review-needed / suspicious not SECRET examples:

```text
MicrosoftResponseToken.access_token variants
UserService_1.private_key / private_key_id / token_uri
CreateWebhookRequest.oauth_client_secret
Assistant config.apiKey
UserService_2.Personal_access_token
RafalPrivateEmailService.client_secret
EmailIt API Configuration.apiKey
AccessToken.access_token / refresh_token
Repository.temp_clone_token
```

False positives remain common:

```text
nextPageToken
nextSyncToken
private flags on repositories/users/events
resourceKey
accessRole
```

Manual filtering is required for security reports.

## Endpoint Rendering Concern

30 actions still show malformed endpoint fragments like:

```text
ENDPOINT:'https:this._logline(...
```

Examples:

```text
Bitbucket: List workspaces for user
Google Photos: Media Items Batch Create
SendGrid: Create an Event Webhook
PDFMonkey: Generate a Document
SurveyMonkey: surveys list
Mollie: Create payment
EmailIt: Send Emails
Open AI: List files_1
GitHub: create repository
Google Forms: create form
```

This remains a major MCP/export/editor verification concern.

## Recommendation

Batch 5 was useful because it finally exposed configuration form primitives:

- `_setanswerofinputfield`
- `_mapformdatatoobject`
- `_showsnackbar`
- `_clearform`

It also strongly expanded the OpenAI vector-store/file map and confirmed broad Google/Microsoft workspace integration patterns.

However, after five batches the persistent missing areas are clear:

- no scheduled jobs;
- no MCP-visible API→action binding;
- no native webhook receiver/signature verification;
- no native RBAC/permission primitive;
- no database relation/transaction primitive;
- no clean plugin lifecycle/uninstall behavior.

Recommendation: **stop broad bulk installing after this batch and consolidate the platform map**. Further bulk batches are likely to add mostly HTTP wrappers. If continuing, switch to targeted searches/installations only for jobs, APIs, webhooks, RBAC, and complex UI/template bindings.
