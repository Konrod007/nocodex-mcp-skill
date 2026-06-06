# NoCode-X App Template Audit — 3 Apps — 2026-06-05

Status: **inspected three user-provided application URLs as ready-block/template examples**.

## Applications

Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)

Apps:

```text
1. Jobs
   id: [REDACTED_ID]

2. Root
   id: [REDACTED_ID]

3. Test Updating Template Parameter
   id: [REDACTED_ID]
```

## Summary Table

| App | APIs | Schemas | Actions | Jobs | Templates | Issues | Main value |
|---|---:|---:|---:|---:|---:|---:|---|
| Jobs | 0 | 0 | 0 | 0 | 4 | 0 | Empty/default baseline only |
| Root | 0 | 1 | 3 | 0 | 4 | 6 | Broken DB fetch/update/upsert example |
| Test Updating Template Parameter | 0 | 0 | 2 | 0 | 6 | 0 | Useful reusable template parameter/action example |

## 1. App: Jobs

```text
Application: Jobs
id: [REDACTED_ID]
```

Inventory:

```text
APIs:       0
Schemas:   0
Actions:   0
Jobs:      0
Templates: 4
Issues:    0
Folders:   2
```

Templates:

```text
Error: not authorized
LottieFiles component
Error: unknown error
Error: not found
```

Finding:

```text
This app is only default/error baseline plus Lottie component. No app block, no job, no data/action pattern is visible through MCP.
```

Verdict:

```text
Useful as template/block example: no.
Useful as clean baseline: yes.
```

## 2. App: Root

```text
Application: Root
id: [REDACTED_ID]
```

Inventory:

```text
APIs:       0
Schemas:   1
Actions:   3
Jobs:      0
Templates: 4
Issues:    6
Folders:   2
```

Schema:

```text
Ideas
id: [REDACTED_ID]
```

Actions:

```text
Update Idea with indexed fetch
Fetching actions
Update Idea with upsert
```

Issues:

```text
2 × Invocation "Get all the ideas from the database" uses deprecated method "getfiltereddatav3"
2 × Invocation "Get all the ideas from the database" references non-existing data format "[REDACTED_ID]"
1 × Invocation "Fetch a list of data records" uses deprecated method "getfiltereddatav3"
1 × Invocation "Fetch a list of data records" references non-existing data format "[REDACTED_ID]"
```

MCP/API instability:

```text
get_action_javascript returned 500 Internal Server Error for all 3 actions.
MCP then became temporarily unreachable during deeper template/action inspection.
```

Platform lesson:

This app is likely intended to demonstrate data fetch/update/upsert patterns against an `Ideas` schema. However, validator reports the schema as non-existing even though MCP lists it. This is the same suspicious class seen in `Jobs-Steve`:

```text
MCP lists schema by ID
but validator says action references non-existing data format with same ID
```

Possible causes:

```text
validation/cache bug
stale data-format reference
ownership/folder/environment mismatch
MCP list layer and action validation layer disagree
```

Verdict:

```text
Potentially useful DB fetch/upsert example, but currently broken/uninspectable through action JS due 500 errors.
```

## 3. App: Test Updating Template Parameter

```text
Application: Test Updating Template Parameter
id: [REDACTED_ID]
```

Inventory:

```text
APIs:       0
Schemas:   0
Actions:   2
Jobs:      0
Templates: 6
Issues:    0
Folders:   2
```

Templates:

```text
Parent Template
Reusable Template
Error: not authorized
LottieFiles component
Error: unknown error
Error: not found
```

Important template details:

```text
Parent Template
- elements: TEMPLATE_CODE_1

Reusable Template
- text snippet: <p>CLICK ME</p> <p>PARAMETER: {{PARAM}}</p>
- elements:
  - VERTICAL_LIST_CODE_1
  - TEXT_PART_CODE_2
  - TEXT_PART_CODE_1_1
```

Actions:

```text
Reusable On Click
signature: main(PARAM:string)

Reusable On Load
signature: main(PARAM:string)
```

Primitives:

```text
_start: 2
_logline: 2
_settemplateargument: 2
```

Platform lesson:

This is a clean, useful example of reusable template parameters and lifecycle/action bindings:

```text
Reusable Template exposes parameter {{PARAM}}
↓
Reusable On Load / Reusable On Click receive PARAM:string
↓
Action calls _settemplateargument
↓
Template content can be updated via parameterized action
```

This is valuable because plugin mining showed `_settemplateargument`, but this app demonstrates the simpler reusable-template parameter model directly.

## Cross-App Lessons

### 1. Ready app examples are more targeted than plugins

The three apps are not rich full products, but each can test one platform mechanism:

```text
Jobs-Steve: scheduled job pattern
Root: data fetch/update/upsert pattern, currently broken
Test Updating Template Parameter: reusable template parameter binding
Jobs: empty baseline
```

### 2. Reusable template parameters are confirmed

`Test Updating Template Parameter` is the strongest useful sample in this group.

Reusable recipe:

```text
1. Create reusable template with `{{PARAM}}` placeholder.
2. Embed it in parent template.
3. Attach On Load / On Click actions.
4. Define action signature `main(PARAM:string)`.
5. Use `_settemplateargument` to update/render argument.
```

### 3. Data-format validator inconsistency repeats

Both `Jobs-Steve` and `Root` show data formats that MCP lists, while issues say action invocations reference non-existing data formats.

This should be reported as a platform/developer issue if reproducible.

### 4. MCP server stability remains a risk

During `Root` inspection:

```text
get_action_javascript returned HTTP 500 for all actions
MCP became unreachable after consecutive failures
```

For template/app audits, use shallow inventory first, then drill down one app at a time.

## Recommendations

Continue inspecting ready app examples, but prioritize apps with non-default templates/actions/jobs:

```text
- reusable template/component examples
- form/config pages
- dashboards
- navigation/menu examples
- jobs
- APIs with action binding
- real data CRUD apps
- auth/login/RBAC apps
```

Skip/low priority:

```text
- apps with only Error pages + LottieFiles
- apps with zero schemas/actions/jobs/APIs unless used as baseline
```

## Verdict

```text
This batch is useful mainly because of `Test Updating Template Parameter`.
```

Ratings:

```text
Насколько полезно для понимания платформы: 7/10
Насколько полезно как готовые app templates: 3/10
Насколько полезно для reusable patterns: 7/10
Production readiness: 2/10
```
