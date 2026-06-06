# NoCode-X MCP Debugging Playbook

## First Triage

Start every debugging session with:

1. `get_current_workspace`
2. `get_current_application`
3. `list_all_issues`
4. `read_logs` for the target environment when known

If environment is unknown, ask the user which NoCode-X environment to inspect.

## Evidence Trail Pattern

Use evidence trails instead of single-tool conclusions:

```text
symptom -> affected surface -> object ID -> config/code -> logs/issues -> likely cause
```

Examples:

```text
button fails -> template element -> attached action -> action JS -> action logs -> missing field
API fails -> API config -> schema -> action caller -> app logs -> wrong payload
job fails -> scheduled job -> related action/API/schema -> logs/issues -> runtime failure
```

## Logs

Use log tools for the last ten minutes:

- global app logs: `read_logs(environment)`
- action logs: `read_action_logs(actionId, environment)`
- page logs: `read_page_logs(templateId, environment)`

Always include the environment inspected in the final answer.

## Page Interaction Debugging

1. `list_all_templates`
2. `get_page_html(templateId)`
3. `list_template_elements(templateId)`
4. `get_attached_actions_on_element(templateId, elementCode)`
5. `get_action_javascript(actionId)`
6. `list_action_issues(actionId)`
7. `read_action_logs(actionId, environment)`
8. `read_page_logs(templateId, environment)`

Final answer should name the template, element, action, and log evidence.

## API Failure Debugging

1. `search_apis(keyword)` or `list_all_apis`
2. `get_api(apiId)`
3. `search_dataschemas(keyword)` or `list_all_dataschemas`
4. `get_dataschema(dataSchemaId)`
5. `search_actions(keyword)` for callers/handlers
6. `read_logs(environment)`

Final answer should separate API config issues from schema/data issues and runtime/log issues.

## Action Failure Debugging

1. `search_actions(keyword)` or `get_actions`
2. `get_action_javascript(actionId)`
3. `list_action_issues(actionId)`
4. `read_action_logs(actionId, environment)`
5. Inspect related APIs/schemas if referenced in code or issues.

Final answer should include the action ID/name, code-level clue, logs, and safe fix path.

## Job Debugging

1. `list_all_jobs` or `find_jobs(keyword)`
2. Identify related action/API/schema names.
3. Use action/API/schema tools to inspect dependencies.
4. Use `read_logs(environment)` and `read_action_logs` if an action is involved.

Final answer should distinguish schedule/config problems from runtime action failures.

## When Evidence Is Insufficient

Say what was checked and what remains unknown. Ask for a missing environment, page/template, action, API, schema, or reproduction steps only when tools cannot discover it.
