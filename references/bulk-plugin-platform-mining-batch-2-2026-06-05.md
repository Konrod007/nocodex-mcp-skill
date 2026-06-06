# Bulk Plugin Platform Mining — Batch 2 — 2026-06-05

Status: **after user installed another batch of plugins; analyzed for NoCode-X platform structure and reusable patterns, not production readiness**.

## Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)
- Previous partial bulk report: `references/bulk-plugin-audit-partial-2026-06-05.md`

## Counts After Batch 2

```text
APIs:         2
Data schemas: 84
Actions:      90
Jobs:         0
Templates:    57
Issues:       319
```

Delta vs previous partial bulk snapshot:

```text
APIs:      +1
Schemas:   +47
Actions:   +56
Jobs:      +0
Templates: +32
Issues:    +161
```

## Main New Action Groups

```text
Edusign:             9 actions
Airtable:            8 actions
Notion:              7 actions
Microsoft Calendar:  5 actions
Paperform:           5 actions
GitHub:              4 actions
Pipedrive:           4 actions
LiveChat:            3 actions
Microsoft File:      3 actions
```

Additional platform/pattern groups:

```text
Delete all:     2 actions
Create scrape:  2 actions
Insert detail:  2 actions
Insert mini:    2 actions
Insert card:    2 actions
Fetch data:     2 actions
Upload file:    1 action
Scrape URL:     1 action
Fetch website:  1 action
Execute card:   1 action
Log string:     1 action
show-list-length: 1 action
```

## New Platform Primitives Observed

This batch was useful because it exposed many workflow primitives beyond basic HTTP wrappers.

Most common primitives:

```text
_start                         90
_logline                       75
_getfirstfiltereddatav3        55
_httpcall                      53
_replaceplaceholders           31
_action                        15
```

UI/template/data rendering primitives:

```text
_addtemplatecomponenttolist              4
_addtemplatecomponenttohorizontallist    4
_addtemplatecomponenttolistv2            4
_settemplateargument                     2
_hidepartv2                              1
```

Data/query/object primitives:

```text
_getfiltereddatav3       4
_getdatav2               2
_createobjectdata        2
_createobjectfreev2      2
_updateobjectfreev2      1
_updatedata              1
_deletedatabydataformatid 1
_getdataformatjsonschema 1
_getobjectfromlist       1
```

File/media/content primitives:

```text
_uploadhttpfilev2        1
_texttofile              1
_loadmedia               1
_encodebase64            1
_deleteallmedia          1
_htmltomarkdown          1
_objecttojson            1
_objecttostring          1
```

Web/scraping/list/string primitives:

```text
_scrape                  1
_selectlinksfromhtml     1
_stripanchorsfromurl     2
_seperatedstringtolist   1
_storelistinscope        1
_createstringvariable    2
_wait                    1
_getbaseurl              2
```

## Important New Structural Lessons

### 1. NoCode-X has reusable UI list/card rendering primitives

The batch added card templates and actions around:

```text
Card
Mini Card
Detail Card
Vertical Detail Cards
Horizontal Cards
Display Horizontal Cards
TEST PAGE Cards / Mini Cards / Detail Cards
```

Related actions show a platform pattern:

```text
get filtered data / get data by id
→ set template arguments
→ add template component to vertical/horizontal list
```

This is valuable because it reveals how dynamic lists are built in NoCode-X templates.

### 2. NoCode-X supports action composition through `_action`

`_action` appeared in 15 actions, including Microsoft Calendar/File, card buttons, scrape workflows, and assistant workflows.

This suggests a pattern:

```text
small actions can be composed into higher-level workflows
```

### 3. There is a content ingestion / RAG-like workflow pattern

Actions and primitives observed:

```text
Create scrape request for link
Create scrape requests for links
Scrape URL
Create file in vector store
Upload file to assistant
Search/Chat with an assistant
Fetch website information from assistant
```

Relevant primitives:

```text
_scrape
_selectlinksfromhtml
_stripanchorsfromurl
_htmltomarkdown
_texttofile
_uploadhttpfilev2
_createobjectfreev2
_getdataformatjsonschema
_objecttojson
_objecttostring
_wait
```

This is the most important new architectural pattern in batch 2: NoCode-X can model a scrape → transform → file/vector-store → assistant search/chat pipeline.

### 4. NoCode-X has file/media operations beyond raw HTTP

New file/media primitives:

```text
_uploadhttpfilev2
_loadmedia
_encodebase64
_texttofile
_deleteallmedia
```

Examples:

```text
Upload file to assistant
Edusign: Create a document using base64
Delete all media
Create file in vector store
```

This expands the platform model beyond API wrappers.

### 5. API endpoints are still created without attached actions

Current APIs:

```text
My Blank API #1             GET /[REDACTED_ID] actionId=null
Fetch website information   GET /website-info                            actionId=null
```

No real API→action binding observed yet.

### 6. Jobs are still absent

```text
Jobs: 0
```

No scheduled/background job pattern discovered in this batch.

## Auth / HTTP Patterns

Authentication methods observed in rendered actions:

```text
BASIC_AUTH: 57
BEARER:     47
NONE:        7
```

HTTP methods observed:

```text
GET:    53
POST:    9
PUT:     3
PATCH:   1
DELETE:  1
```

This confirms that most plugins are still HTTP wrapper actions, but batch 2 added more internal/platform primitives.

## Validation / Issue Patterns

Total issues:

```text
319
```

Top issue classes:

```text
110 × Required argument "Text" was empty
66  × Required argument "Authentication method" was empty
62  × Required argument "Data format" was empty
16  × Required argument "Action" was empty
6   × Required argument "List ui element" was empty
4   × Required argument "List" was empty
```

New/deeper issue types:

```text
Deprecated getfiltereddatav3
Deprecated addtemplatecomponenttolist
Deprecated addtemplatecomponenttolistv2
Deprecated createobjectfreev2
Non-existing data format {DATA_FORMAT}
Variable DATA may be null but is used without null-check
Required output Result was empty
Required argument Data-format was empty
```

## Security / Secret Classification Lessons

Examples correctly classified as SECRET:

```text
Pinecone config.apiKey
Notion API configuration.OAuth_Client_Secret
Notion API configuration.Secret_internal
GetMicrosoftToken.client_id / client_secret
Pipedrive API configuration.personal_API_token
Foursquare API Configuration.API_Key / Service_API_Key
LinkedIn API Configuration.Client_ID / Primary_Client_Secret / Access_token
LiveChat API configuration.Token / Client_Secret / Redirect_URI
Stripe API configuration.api_key
Edusign API Configuration.API_key
DeepL API Configuration.DeepL_API_Key
Paperform API configuration.access_token
Scrape Config.apiKey
```

Potentially sensitive fields not classified as SECRET or suspiciously exposed:

```text
CustomerSession.client_secret
Airtable API configuration.USER_TOKEN_ID
UserService.microsoft_access_token
GitHub API configuration.Personal_access_token
MicrosoftResponseToken.access_token
MicrosoftResponseToken_1.access_token
Repository.temp_clone_token
```

Some false positives may exist (`changeKey`, `keys_url`, `access`), but access tokens and client secrets should be reviewed.

## Endpoint Rendering Concern

25 actions still showed malformed endpoint fragments like:

```text
ENDPOINT:'https:this._logline(...
```

Examples:

```text
Foursquare: Place Search
Edusign: Create a course
Notion: List all users
GitHub: get user
Stripe: Create a Customer Session
Linkedin: Create a Share
DeepL: translate text
LiveChat: start chat
Microsoft File: Create fileStorageContainer
Docusign: Get all documents
GitHub: create a repository for the authenticated user
```

This remains either a builder/export bug or MCP JS rendering bug; runtime editor verification is required.

## Recommendation

Batch 2 was useful for platform understanding. It exposed several non-trivial NoCode-X capabilities:

- dynamic list/card rendering;
- template component insertion;
- action composition;
- file upload/load/base64/text-to-file/media deletion;
- scrape/link extraction/html-to-markdown;
- assistant/vector-store style workflow;
- object-free create/update and schema introspection.

Continue only if next batches are mined for new platform primitives/patterns, not plugin readiness.

Stop after 1–2 more batches if no new primitives beyond HTTP wrappers, card/list rendering, scraping, files/media, assistant workflow, APIs, or jobs appear.
