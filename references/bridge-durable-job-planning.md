# NoCode-X Bridge / Durable Job Planning Pattern

Use this reference when a user wants to move an existing service or workflow toward NoCode-X, especially when the current workflow includes long-running collection, crawling, sync, or batch-processing tasks.

Keep this reference class-level. Do not copy private app names, business ideas, URLs, repository paths, credentials, or app-specific implementation details into this shared skill.

## Core Principle

Treat NoCode-X as a visual control plane / workflow layer first, not as the first replacement for a working source-of-truth system.

Recommended sequence:

1. Make the existing process durable and observable locally.
2. Emit stable jobs/events/snapshots from that local process.
3. Sync or expose those events/snapshots to NoCode-X.
4. Build NoCode-X UI/actions around control, monitoring, review, and manual operations.
5. Only later migrate source-of-truth responsibilities, if reconciliation and permissions are proven.

## When To Prefer A Local Durable Worker First

Prefer a local durable job/event model before a NoCode-X bridge when the workflow has any of these properties:

- long-running browser/API request;
- hundreds or thousands of items;
- must survive reloads, timeouts, server restarts, or worker crashes;
- needs cancellation, retries, partial success, or resume;
- needs trustworthy progress counters;
- produces data that must not be duplicated;
- should later be shown in NoCode-X as an operations dashboard.

## Minimal Durable Job Model

Use tables or schemas equivalent to:

- `collection_jobs`: one row per run; status, filter snapshot, totals, counters, timestamps.
- `collection_items`: one row per unit of work; status, attempts, lease owner, lease expiry, error.
- `collection_events`: append-only audit trail; started, item claimed, item completed, item failed, cancelled, resumed.
- result tables: idempotent outputs keyed by stable source/entity keys.

Status model:

- job: `queued`, `running`, `cancelling`, `cancelled`, `succeeded`, `partial`, `failed`.
- item: `pending`, `leased`, `succeeded`, `failed`, `skipped`.

Worker rules:

- claim work with a lease, not with in-memory state;
- reclaim expired leases;
- update counters from DB facts, not optimistic UI state;
- retry transient failures with max attempts;
- store permanent failures separately from missing/empty results;
- stop claiming new items after cancel is requested;
- make result writes idempotent.

## Minimal API Shape

Prefer short HTTP requests that only create/control/read jobs:

- `POST /.../jobs` — create job from selected filter snapshot.
- `GET /.../jobs/:id` — read durable progress.
- `POST /.../jobs/:id/cancel` — request cancellation.
- optional: `POST /.../jobs/:id/retry-failed`.

Do not keep the browser request open while processing all items.

## NoCode-X Bridge Shape

Once durable local jobs/events exist, bridge to NoCode-X through stable payloads:

- snapshot DTOs for current state;
- event DTOs for append-only history;
- source-specific keys so one provider/source does not overwrite another;
- cursor-based sync;
- idempotency keys;
- reconciliation checks;
- shadow/dry-run mode before active sync.

Good NoCode-X surfaces for this pattern:

- operations dashboard;
- job center;
- progress and error logs;
- review queue;
- manual retry/cancel controls;
- settings/configuration screens;
- visual links to external repo/issues/PRs when development is involved.

## Decision Gates Before Full Bridge/Migration

Do not make NoCode-X the source of truth until:

- local worker completes large runs reliably;
- restart/resume test passes;
- cancellation test passes;
- duplicate result prevention is proven;
- event ordering/cursors are stable;
- NoCode-X sync can run in shadow mode and reconcile counts;
- credentials/secret storage and RBAC are understood.

## Planning Output Pattern

When asked for recommendations before code changes:

1. Read the user's architecture docs and relevant current implementation.
2. Separate immediate reliability fix from strategic NoCode-X migration.
3. Estimate complexity for each path.
4. Recommend order of implementation.
5. Produce a concise plan with phases, likely files/components, tests, risks, and verification commands.
6. If persisting the plan for a private project, write it into the project workspace, not into this shared skill.
