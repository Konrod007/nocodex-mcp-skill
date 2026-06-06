# NoCode-X App Template Audit — Jobs-Steve — 2026-06-05

Status: **inspected application from user-provided URL as an example app/template/block, not marketplace plugin batch**.

## Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Jobs-Steve` (`[REDACTED_ID]`)
- URL: `https://app.nocode-x.com/company/[REDACTED]` as provided by user (application id parsed as `[REDACTED_ID]`)

## Inventory

```text
APIs:         0
Data schemas: 1
Actions:      1
Jobs:         1
Templates:    4
Issues:       4
Folders:      2
```

Folders:

```text
Root
Plugins
```

## Important Finding

This app is important because it is the first inspected example with a NoCode-X scheduled job object:

```text
Job: Recurring job test
id: [REDACTED_ID]
```

Earlier bulk plugin batches repeatedly showed `Jobs: 0`. This app proves scheduled/background jobs exist as first-class MCP-visible application objects.

## Objects

### Data schema

```text
application_log
id: [REDACTED_ID]
fields:
- event: string|null
```

### Action

```text
JOB Test
id: [REDACTED_ID]
signature: main()
```

Primitive calls:

```text
_start
_logline
_createdate
_formatDate
_replaceplaceholders
_createobjectdata
```

Action flow:

```text
_start
→ write application log line: "Test write to NCX application log"
→ create current date
→ format date as yyyyMMddTHHmmss
→ replace placeholders in text "Test event logged{{p0}}"
→ create data record in application_log with event=<formatted event line>
```

Generated JavaScript excerpt:

```js
main(){
  this._start();
  this._logline({ LOGLINE:'Test write to NCX application log', LOGLEVEL:'INFO' });
  let {OUTPUT:CURRENT_DATE}=this._createdate({ TYPE:'NOW', UNIT:'MINUTES' });
  let {OUTPUT:FORMATTED_DATE}=this._formatDate({ DATE:CURRENT_DATE, DATE_XXX_FORMAT:'yyyyMMddTHHmmss', FORMAT_TYPE:'FREE' });
  let {RESULT:EVENT_LINE}=this._replaceplaceholders({ TEXT:'Test event logged{{p0}}', PLACEHOLDERS:{...} });
  let {DATA_XXX_ID:CREATED_DATA_ID}=this._createobjectdata({ NAME:FORMATTED_DATE, DATA_XXX_FORMAT:dataformat_f94d2ddd_5503_4348_b6a5_e95a4d3cf3cc, BODY:{event:EVENT_LINE} });
}
```

### Templates

Only default/error templates plus Lottie component:

```text
Error: not authorized
Error: unknown error
Error: not found
LottieFiles component
```

No real app UI/template block was visible through MCP.

## Issues

```text
4 BUG issues
```

Issue classes:

```text
1 × Invocation "Create date" uses deprecated method "createdate"
2 × Invocation "Create data" uses deprecated method "createobjectdata"
1 × Invocation "Create data" references non-existing data format "[REDACTED_ID]"
```

The `non-existing data format` issue is suspicious because MCP `list_all_dataschemas` and `get_dataschema` do return the schema with exactly that ID. This may indicate a validation/cache bug, data format ownership mismatch, or stale internal reference.

## Platform Lessons

### 1. Scheduled jobs are MCP-visible

Unlike plugin batches, this app returns a real job via `list_all_jobs`.

### 2. Job appears to execute an action

MCP exposes the job object but not full job configuration. The app has exactly one action (`JOB Test`), strongly implying the job is attached to that action, but the exact binding/schedule is not available from the listed MCP fields.

### 3. Typical scheduled task recipe

This app reveals a minimal scheduled logging recipe:

```text
Job
→ Action main()
→ create current date
→ format date
→ create database record
→ application log line
```

### 4. Date primitives exist but may be deprecated

New/important primitives:

```text
_createdate
_formatDate
```

`_createdate` is flagged deprecated by validation. `_formatDate` is not flagged in current issues.

## Gaps / Unknowns

MCP currently does not show:

```text
- cron expression / interval / schedule frequency
- job enabled/disabled status
- environment/DTAP scope
- direct job→action binding field
- last run / next run / run history
```

Need UI inspection or additional MCP support to fully document job configuration.

## Recommendation

This is a useful app template for platform understanding, not because of UI blocks, but because it demonstrates the missing scheduled job layer.

Next steps:

1. Use UI/browser if authenticated to inspect the job configuration screen.
2. Confirm schedule frequency, enabled state, environment, and action binding.
3. Run/read logs if possible to verify the job actually creates `application_log` records.
4. Ask NoCode-X/MCP vendor for a `get_job(jobId)` tool if unavailable.

## Verdict

```text
Useful as scheduled-job architecture example: yes.
Useful as UI/app template example: low.
```

Ratings:

```text
Насколько полезно для понимания платформы: 8/10
Насколько полезно как готовый app template: 2/10
Насколько полезно для reusable patterns: 6/10
Production readiness: 2/10
```
