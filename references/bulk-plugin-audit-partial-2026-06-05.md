# Partial Bulk Plugin Audit — 2026-06-05

Status: **after user installed a subset of remaining plugins in bulk**.

## Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)
- Baseline reference: `references/bulk-plugin-audit-baseline.md`

## Baseline Before Bulk Install

```text
Folders:      2
APIs:         0
Data schemas: 0
Actions:      0
Jobs:         0
Templates:    21
Issues:       0
```

Baseline templates were 17 Vanilla Heroes leftovers plus 4 default error/LottieFiles templates.

## After Partial Bulk Install

```text
Folders:      2
APIs:         1
Data schemas: 37
Actions:      34
Jobs:         0
Templates:    25
Issues:       158
```

New template names beyond baseline:

- `ROOT`
- `Settings`
- `Connection Success`
- `Configuration Exist`

## Action Groups Observed

### Airtable

Actions: 8

- `Airtable: List records`
- `Airtable: Create comment`
- `Airtable: Update table`
- `Airtable: Delete record`
- `Airtable: Create record`
- `Airtable: Get record`
- `Airtable: Create table`
- `Airtable: Create base`

Issues: 37

### Bitbucket

Actions: 6

- `Bitbucket: Get file or directory contents`
- `Bitbucket: List repositories in a workspace`
- `Bitbucket: Get repo hooks`
- `Bitbucket: Fetch file by path`
- `Bitbucket: List workspaces for user`
- `Bitbucket: Create a commit by uploading a file`

Issues: 27

### Stripe | Core Resources | Customers

Actions: 6

- `Retrieve a customer`
- `Delete a customer`
- `Search customers`
- `Create a customer`
- `Update a customer`
- `List all customers`

Issues: 34

### Stripe | Products

Actions: 4

- `Create a product`
- `Update a product`
- `List all products`
- `Retrieve a product`

Issues: 32

### SupaBase

Actions: 3

- `SupaBase: Retrieve table data`
- `SupaBase: Write data to table `
- `SupaBase: Retrieve project tables list`

Issues: 4

### Firebase

Actions: 2

- `Firebase: Add data`
- `Firebase: Retrieving Data`

Issues: 3

### Softr

Actions: 2

- `Softr: Create User`
- `Softr: Delete User`

Issues: 7

### HTML/CSS to Image

Actions: 1

- `Convert HTML & CSS Code to an Image`

Issues: 7

## NoCode-X API Observed

One API was returned:

```text
Name: Fetch website information
Endpoint: website-info
Method: GET
Authenticated access: false
Action: null
```

Concern: the API has no attached action (`actionId: null`, `actionName: null`), so it is probably not operational as-is.

## Issue Summary

Total open issues: 158

Top classes:

- 61 × missing `Text`
- 37 × missing `Data format`
- 37 × missing `Authentication method`
- 4 × missing `UI element`
- multiple `UNEXISTING_DATA_FORMAT_USED`
- 1 × deprecated `createobjectdata`
- 1 × missing `File`
- 2 × missing `Response type`

## Security / Data Classification Concerns

Potential secret fields not classified as `SECRET`:

- `Airtable API configuration.USER_TOKEN_ID`
- `User.password`
- `Firebase API Configuration.apiKey`

## Endpoint / Rendering Concerns

8 actions showed malformed endpoint fragments of the recurring form:

```text
ENDPOINT:'https:this._logline(...
```

Sample actions:

- `Softr: Create User`
- `Stripe | Products: Create a product`
- `Stripe | Core Resources | Customers: Search customers`
- `Stripe | Core Resources | Customers: Create a customer`
- `Stripe | Core Resources | Customers: List all customers`
- `Convert HTML & CSS Code to an Image`
- `Bitbucket: List workspaces for user`
- `Stripe | Products: List all products`

## Usefulness Assessment

Bulk install mode is useful for **marketplace triage**, not for clean plugin-level attribution.

Useful signal recovered:

- which integrations create actions at all;
- which integrations are more substantial by action count;
- global quality/validation issue counts;
- security classification problems;
- obviously broken endpoint/rendering patterns;
- rough short-list for deeper manual audit.

Not useful for:

- exact plugin/package attribution when schema names are generic;
- clean before/after diffs per plugin;
- proving production readiness;
- testing runtime behavior without credentials and manual setup;
- determining whether each marketplace plugin is empty, because bulk install only shows aggregate survivors.

## Current Candidate Shortlist

Most worth deeper inspection if needed:

1. `Airtable` — 8 actions, broad record/table/base coverage, but 37 issues.
2. `Bitbucket` — 6 actions, repo/workspace/file/hook coverage, but 27 issues.
3. `Stripe Customers` — 6 actions, useful CRUD/search/list set, but 34 issues.
4. `SupaBase` — 3 actions, fewer issues than most, but likely config/reference problems.
5. `Firebase` — 2 actions, fewer issues, but very small scope and `apiKey` not SECRET.
6. `HTML/CSS to Image` — niche but potentially useful, 1 action with endpoint/security concerns.

## Recommendation

Do not install all remaining plugins only to find production-ready tools. The partial bulk result confirms the earlier pattern: plugins are mostly scaffolds with high validation/setup debt.

Bulk mode is still useful if the goal is to produce a high-level marketplace quality report and identify a small candidate shortlist. It is not worth continuing if the goal is to discover finished, ready-to-use plugins.
