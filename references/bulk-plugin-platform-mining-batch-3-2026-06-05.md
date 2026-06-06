# Bulk Plugin Platform Mining — Batch 3 — 2026-06-05

Status: **after user installed another plugin batch; analyzed for NoCode-X platform structure/patterns**.

## Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)
- Previous batch reference: `references/bulk-plugin-platform-mining-batch-2-2026-06-05.md`

## Counts After Batch 3

```text
APIs:         2
Data schemas: 81
Actions:      64
Jobs:         0
Templates:    21
Issues:       283
```

Delta vs Batch 2 snapshot:

```text
APIs:       0
Schemas:   -3
Actions:   -26
Jobs:       0
Templates: -36
Issues:    -36
```

Interpretation: the application state is not monotonic. Installing this batch appears to have replaced/removed some prior batch objects or reset template groups. Do not interpret bulk snapshots as additive unless the plugin lifecycle is controlled.

## Main Action Groups

```text
Amazon Alexa:                6 actions
Pinecone:                    5 actions
Stripe | Products | Prices:  5 actions
Handle push:                 5 actions
Baserow:                     4 actions
Bitbucket:                   4 actions
Microsoft Search:            4 actions
Monday:                      3 actions
Jira:                        3 actions
Calendly:                    3 actions
Google Gmail:                2 actions
Move file:                   2 actions
Search/Chat with assistant:  2 actions
```

## New Platform Primitives vs Batch 2

Batch 3 exposed these primitives that were not in the Batch 2 primitive map:

```text
_creategcpaccesstoken
_downloadhttpcall
_createmedia
_deletedata
_deletemedia
_getvaluefromobject
_urlencode
```

Examples:

```text
_creategcpaccesstoken:
- Google Gmail: List User Messages
- Google Gmail: Send Message

_downloadhttpcall:
- Save document in media library
- Bitbucket: Fetch file by path
- GitLab: Download a file from the project repository

_createmedia:
- Save document in media library
- Bitbucket: Fetch file by path
- GitLab: Download a file from the project repository

_deletedata:
- Handle push event
- Handle push event commit
- Handle push event removed file
- GitLab: Download a file from the project repository

_deletemedia:
- GitLab: Download a file from the project repository

_getvaluefromobject:
- Move file to pinecone assistant

_urlencode:
- GitLab: Download a file from the project repository
```

## Important New Structural Lessons

### 1. Google service-account auth primitive exists

`_creategcpaccesstoken` appears in Gmail actions:

```text
Google Gmail: List User Messages
Google Gmail: Send Message
```

This is a major platform capability. It suggests NoCode-X has a built-in Google Cloud/service-account token generator, not only generic bearer/API-key auth.

Related schemas observed:

```text
Google: Service user json
Google: API Key json
```

### 2. Download HTTP call → media library pattern exists

Batch 3 exposed a clean file ingestion pattern:

```text
_downloadhttpcall
→ _createmedia
```

Examples:

```text
Save document in media library
Bitbucket: Fetch file by path
GitLab: Download a file from the project repository
```

This is distinct from Batch 2's `_uploadhttpfilev2` and `_texttofile` patterns. NoCode-X can both upload files to external services and download external files into its own media library.

### 3. Media deletion primitive exists

Batch 2 had `_deleteallmedia`; Batch 3 adds targeted media deletion:

```text
_deletemedia
```

Example:

```text
GitLab: Download a file from the project repository
```

### 4. Webhook-ish API pattern finally appears, but action binding is still missing

Current APIs:

```text
Webhook: Push event
POST /push-event
actionId: null

a Create a single RepoPushWebhook
POST /repopushwebhook/create
actionId: null
```

Actions related to this API/webhook concept exist:

```text
Create a single RepoPushWebhook
Handle push event
Handle push event updated file
Handle push event added file
Handle push event commit
Handle push event removed file
Update Bitbucket Repo
Feed Assistant with bitbucket data
```

But the NoCode-X API objects are still not attached to actions through `actionId`. This is important: plugin artifacts can model webhook handlers as actions, but API→action wiring may be missing or not exposed through MCP.

### 5. Push event → file diff → assistant feed workflow appears

This batch exposes a much more concrete Git/assistant workflow:

```text
Repo push webhook
→ handle push event
→ detect added/updated/removed files
→ download repo files
→ add to media library
→ move file to Pinecone assistant
→ feed/search/chat assistant
```

Related actions:

```text
Create a single RepoPushWebhook
Handle push event
Handle push event updated file
Handle push event added file
Handle push event removed file
Download files from bitbucket and add to media library
Update Bitbucket Repo
Feed Assistant with bitbucket data
Move file to pinecone assistant
Search/Chat with an assistant
Delete file from pinecone assistant
Remove All files from pinecone assistant
```

This is one of the best discovered platform examples so far.

### 6. Pinecone assistant file lifecycle is modeled

Pinecone action group:

```text
Pinecone: Upload file to assistant
Pinecone: Upload file to assistant_1
Pinecone: Upload file to assistant_2
Pinecone: Delete an uploaded file
Pinecone: Delete file from assistant
```

Related generic actions:

```text
Move file to pinecone assistant
Remove All files from pinecone assistant
Search/Chat with an assistant
```

This improves the Batch 2 RAG/assistant model: NoCode-X can represent file lifecycle in an assistant/vector-store flow.

### 7. OAuth refresh/token lifecycle appears more clearly

Relevant actions:

```text
Amazon Alexa: get access token
Amazon Alexa: Refresh token
Get Accesstoken
Monday: Authenticate
```

Relevant schemas:

```text
AccessToken
AccessTokenRequest
AccessTokenResponse
AuthRequest
AuthResponse
```

This does not prove a complete OAuth redirect flow, but it shows explicit access/refresh token actions and token schemas.

### 8. API_TOKEN auth method appears

Auth methods observed:

```text
BASIC_AUTH: 48
BEARER:     22
NONE:       14
API_TOKEN:   4
```

`API_TOKEN` is new/important compared with previous observations dominated by BASIC_AUTH/BEARER/NONE.

## Current APIs

```text
Webhook: Push event
- POST /push-event
- actionId: null
- authenticatedAccess: false

Create a single RepoPushWebhook
- POST /repopushwebhook/create
- actionId: null
- authenticatedAccess: false
```

Important: API objects exist, but still no action binding through MCP.

## Jobs

```text
Jobs: 0
```

Scheduled/background job pattern still not discovered.

## HTTP/Auth Summary

Auth methods:

```text
BASIC_AUTH: 48
BEARER:     22
NONE:       14
API_TOKEN:   4
```

HTTP methods:

```text
GET:    39
POST:    8
PUT:     4
DELETE:  2
```

## Validation / Issue Patterns

Total issues:

```text
283
```

Top issue classes:

```text
100 × Required argument "Text" was empty
61  × Required argument "Authentication method" was empty
56  × Required argument "Data format" was empty
21  × Required argument "Action" was empty
```

Notable issue classes:

```text
Invocation references non-existing data format
Invocation references non-existing action
Required argument File was empty
Required argument Milliseconds was empty
Execute action missing output STATUS
Found unused invocation "Base64 Decode" in Google Gmail: Send Message
Deprecated createobjectdata
Deprecated deletedata
```

## Security / Secret Classification Lessons

Correct SECRET examples include:

```text
Google: Service user json.private_key
Google: API Key json.api_key
Alexa client id/client secret/access token/refresh token
Pinecone config.apiKey
Pinecone Assistant config.apiKey
APITemplate API_Key
Monday API_token
Jira API_token
Calendly Client_secret / Webhook_signing_key / personal_access_token
GroqCloud API_Key
Bitbucket Assistant Repository_Access_Token
Baserow database_token
```

Potential concerns / review-needed fields:

```text
AccessToken.refresh_token
AccessToken.access_token
AccessTokenRequest.refresh_token
AccessTokenRequest.client_secret
Documentero API Configuration.apiKey
Document.apiKey
MicrosoftResponseToken.access_token
```

Some false positives exist (`nextToken`, `nextPageToken`, `lookup_key`, `max_tokens`), so security scans should distinguish real secrets from pagination/model fields.

## Endpoint Rendering Concern

21 actions still show malformed endpoint fragments like:

```text
ENDPOINT:'https:this._logline(...
```

Examples:

```text
Monday: Authenticate
APITemplate: templates list
Amazon Alexa: Create skill manifest
Stripe | Products | Prices: Create a price
Microsoft Search: searchEntity: query
Documentero: Create document
Mistral AI: chat completion
Jira: create issue
GroqCloud: Create chat completion
```

## Recommendation

Batch 3 was useful. It added several important platform insights:

- Google service-account token primitive;
- download external file → create media library asset;
- targeted media deletion;
- webhook-ish API/action set, though API action binding is missing;
- repo push event → file update → Pinecone assistant feed workflow;
- clearer OAuth access/refresh token handling;
- API_TOKEN auth method.

Continue one more batch if the goal is still platform mining. Specifically look for:

- actual API objects with non-null `actionId`;
- scheduled jobs;
- real webhook signature verification;
- email/SMS/notification workflow beyond simple API calls;
- permissions/RBAC primitives;
- database relation/transaction primitives;
- form submission/template action bindings.

If the next batch does not introduce new primitive classes, stop and consolidate the NoCode-X platform map.
