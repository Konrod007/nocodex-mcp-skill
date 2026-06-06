# Bulk Plugin Audit Baseline

Captured before user installs all remaining plugins in bulk.

## Context

- Captured UTC: `2026-06-05T11:05:48Z`
- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)

## Baseline Counts

```text
Folders:      2
APIs:         0
Data schemas: 0
Actions:      0
Jobs:         0
Templates:    21
Issues:       0
```

## Baseline Folders

- `Plugins` (`[REDACTED_ID]`)
- `Root` (`[REDACTED_ID]`)

## Baseline Actions / Schemas / APIs / Jobs

None visible through MCP at baseline.

## Baseline Templates

Known Vanilla Heroes leftovers:

- `Black Border Button`
- `Play Button component (Dark Mode)`
- `Vertically centered hero sign-up form`
- `Colored Border Button (Dark Mode)`
- `Centered hero`
- `Centered screenshot`
- `Play Button component`
- `heroes page`
- `Black Border Play Button`
- `White Background Button`
- `Dark mode hero`
- `Sign-up Form`
- `White Border Play Button (Dark Mode)`
- `Colored Background Button`
- `Border hero with cropped image and shadows`
- `Colored Border Button`
- `Responsive left-aligned hero with image`

Normal baseline/default templates:

- `Error: not authorized`
- `Error: unknown error`
- `Error: not found`
- `LottieFiles component`

## Notes For After Snapshot

When user finishes bulk installing plugins, take a fresh inventory and compute:

- new actions = after actions minus empty baseline;
- new schemas = after schemas minus empty baseline;
- new APIs/jobs = after minus empty baseline;
- new templates = after templates minus the 21 names listed above;
- new issues = all after issues, because baseline issues were zero.

Because plugins are installed in bulk, attribution will be name/folder/description/schema-reference based, not exact install-order diff.
