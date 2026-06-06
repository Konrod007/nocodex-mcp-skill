# NoCode-X MCP Vendor Roadmap Ideas

These are future MCP capabilities that would make NoCode-X agents more reliable and production-grade.

## Validation And Test Execution

Recommended tools:

```text
validate_application
validate_api
validate_action
validate_dataschema
run_api_test
run_action_test
run_page_check
run_job_test
get_validation_results
get_test_results
```

Why: inspection plus logs is useful, but agents need deterministic validation before and after changes.

## Structured Mutations

Recommended tools:

```text
create_api
update_api
delete_api
create_dataschema
update_dataschema
delete_dataschema
create_action
update_action
delete_action
create_template
update_template
delete_template
create_job
update_job
delete_job
```

Why: builder prompts are useful for complex generation, but simple deterministic edits should be typed and auditable.

## Diff And Approval Flow

Recommended tools:

```text
prepare_application_patch
preview_application_patch
apply_application_patch
rollback_application_patch
get_change_history
```

Why: mature agents should show what will change before applying it.

## Observability

Recommended tools:

```text
list_environments
read_api_logs
read_job_logs
read_deployment_logs
read_builder_logs
get_recent_errors
get_error_detail
```

Why: debugging needs scoped logs and environment discovery.

## Product Feedback Loop

Track aggregated MCP usage to identify product gaps:

- tools users tried to call but did not exist;
- tools that often fail;
- repeated user intents;
- common debugging paths;
- missing validation/test needs.

Use this data to improve both the MCP surface and the main NoCode-X UI.

## Official Docs Gaps Found During Planning Review

Source review included `docs.nocode-x.com` sections for workspaces, applications, users, developers, data formats, APIs, jobs, publishing/testing, and security.

Questions to ask NoCode-X developers/product team:

- Is there a safe user deactivation/suspension flow separate from irreversible user deletion?
- What happens to business records, ownership fields, and audit trails when a user is deleted?
- Are user/group/right/developer-permission operations available through API or MCP?
- Which resources exactly support group/right assignment: templates, APIs, data formats, actions, jobs, data records, fields, or generated CRUD APIs?
- How are rights enforced when an action is triggered indirectly by page events, APIs, jobs, or data-format triggers?
- What are the exact limits for jobs: maximum runtime, retries, overlap/concurrency, cancellation, failure history, and execution logs?
- What defaults do generated CRUD APIs use for authentication, authorization, validation, pagination, error shape, and logging?
- Can audit logs and application logs be queried/exported through API or MCP, and what are the retention/export guarantees?
- What exact field types, validations, relationships, and indexes are supported by Data Formats and the built-in database?
- What operations are included in version snapshots, and what environment-specific data/config is explicitly excluded from promotion?
- How are secrets, external API keys, and AI provider keys stored, rotated, and prevented from leaking into logs or MCP outputs?
- Which MCP tools can inspect the new Standard Page dashboard, security detections, users, groups, rights, versions, and environment deployment state?
