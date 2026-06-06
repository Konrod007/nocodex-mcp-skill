# NoCode-X MCP Tools Reference

This reference covers the 40 MCP entries currently exposed by NoCode-X in Hermes for `nocodex-mcp`: 36 NoCode-X application tools plus 4 generic MCP prompt/resource helpers.

## Workspace And Application Context

### `get_workspaces`
- Purpose: List all available workspaces for the user.
- Arguments: none.
- Use when: choosing or confirming the workspace before app work.

### `find_workspace`
- Purpose: Search workspaces by keyword, sorted by best match.
- Arguments: `keyword` string, required.
- Use when: the user names a workspace but does not provide an ID.

### `switch_workspace`
- Purpose: Switch the current workspace context.
- Arguments: `id` string, required.
- Use when: the selected workspace is not the user’s target workspace.

### `get_current_workspace`
- Purpose: Return the current workspace from the MCP session.
- Arguments: none.
- Use when: starting any workflow or verifying context.

### `get_applications`
- Purpose: List all available applications in the current workspace.
- Arguments: none.
- Use when: discovering apps after workspace selection.

### `find_application`
- Purpose: Search applications by keyword, sorted by best match.
- Arguments: `keyword` string, required.
- Use when: the user names an app but does not provide an ID.

### `switch_application`
- Purpose: Switch the current application context.
- Arguments: `applicationId` string, required.
- Prerequisite: selected workspace.
- Use when: the current app is not the target app.

### `get_current_application`
- Purpose: Return the current application from the MCP session.
- Arguments: none.
- Use when: starting any app-specific workflow or verifying context.

### `get_application_info`
- Purpose: Get information on the current application.
- Arguments: none.
- Use when: beginning architecture review, documentation, or debugging.

### `create_application`
- Purpose: Create a new application in the current workspace and switch to it.
- Arguments: `name` string, `description` string, both required.
- Use when: the user explicitly asks to create a new app.
- Safety: mutating.

## Actions And Logic

### `get_actions`
- Purpose: List all actions, logic, and workflows in the current application.
- Arguments: none.
- Use when: auditing app logic or finding action IDs.

### `search_actions`
- Purpose: Search available actions by keyword in the current application.
- Arguments: `keyword` string, required.
- Use when: looking for a specific workflow, handler, or feature.

### `get_action_javascript`
- Purpose: Get JavaScript for a specific action.
- Arguments: `actionId` string, required.
- Use when: diagnosing action behavior or documenting workflow internals.

### `get_attached_actions_on_element`
- Purpose: Get actions attached to a specific template element.
- Arguments: `elementCode` string and `templateId` string, both required.
- Use when: debugging a click/interaction on a page.
- ID discovery: get `templateId` from `list_all_templates`; get `elementCode` from `list_template_elements` or `get_page_html`.

### `list_action_issues`
- Purpose: Get all issues for a specific action in the current application.
- Arguments: `actionId` string, required.
- Use when: debugging a failing or suspicious action.

## APIs

### `list_all_apis`
- Purpose: List all APIs inside the current application.
- Arguments: none.
- Use when: auditing backend/API surface or finding API IDs.

### `search_apis`
- Purpose: Search APIs by keyword.
- Arguments: `keyword` string, required.
- Use when: looking for a specific endpoint or feature.

### `get_api`
- Purpose: Get detailed information on a specific API.
- Arguments: `apiId` string, required.
- Use when: reviewing endpoint configuration, inputs, outputs, or related logic.

## Data Schemas

### `list_all_dataschemas`
- Purpose: List all data schemas, database tables, or DTOs in the current application.
- Arguments: none.
- Use when: understanding the data model.

### `search_dataschemas`
- Purpose: Search data schemas by keyword.
- Arguments: `keyword` string, required.
- Use when: looking for a specific entity/table/DTO.

### `get_dataschema`
- Purpose: Get detailed information on a specific data schema.
- Arguments: `dataSchemaId` string, required.
- Use when: reviewing fields, relationships, validation, or API dependencies.

## Templates, Pages, And UI

### `list_all_templates`
- Purpose: List all templates in the current application.
- Arguments: none.
- Use when: discovering pages/templates and IDs.

### `get_page_html`
- Purpose: Get HTML code for a page/template.
- Arguments: `templateId` string, required.
- Use when: inspecting page structure or locating UI elements.

### `list_template_elements`
- Purpose: List HTML elements for a template.
- Arguments: `templateId` string, required.
- Use when: finding `elementCode` for interaction debugging.

### `get_template_parameters`
- Purpose: Get parameters defined on a template.
- Arguments: `templateId` string, required.
- Use when: documenting template inputs or debugging missing page data.

## Logs, Issues, And Troubleshooting

### `list_all_issues`
- Purpose: List all issues inside the current application.
- Arguments: none.
- Use when: starting a health check or debugging unknown failures.

### `read_logs`
- Purpose: Read application logs from the last ten minutes.
- Arguments: `environment` string, required.
- Use when: debugging global runtime behavior.
- Environment: use the environment names exposed by NoCode-X; if unknown, ask the user or inspect UI/context.

### `read_action_logs`
- Purpose: Read action logs from the last ten minutes.
- Arguments: `actionId` string and `environment` string, both required.
- Use when: a specific action fails or behaves unexpectedly.

### `read_page_logs`
- Purpose: Read page-triggered logs from the last ten minutes.
- Arguments: `templateId` string and `environment` string, both required.
- Use when: debugging page interactions or frontend-triggered behavior.

## Jobs, Folders, And Media

### `list_all_jobs`
- Purpose: List all scheduled jobs in the current application.
- Arguments: none.
- Use when: reviewing background automation.

### `find_jobs`
- Purpose: Find scheduled jobs by keyword in the current application.
- Arguments: `keyword` string, required.
- Use when: locating a specific scheduled/background process.

### `list_all_folders`
- Purpose: List folders inside the current application.
- Arguments: none.
- Use when: understanding organization and locating grouped assets/configuration.

### `get_media_library_images`
- Purpose: Search images in the application media library.
- Arguments: `query` string, required.
- Use when: finding existing visual assets.

### `get_media_library_file`
- Purpose: Get an actual file from the media library.
- Arguments: `id` string, required.
- Use when: retrieving a known media file by ID.

## Builder

### `request_building_action`
- Purpose: Request the NoCode-X builder to inspect or modify the selected application.
- Arguments: `prompt` string, required.
- Prerequisite: selected workspace and selected application.
- Use when: a task requires NoCode-X internal builder generation or mutation.
- Safety: potentially mutating. Ask for confirmation unless the user explicitly requested the change.
- Required follow-up: call `check_building_status`.

### `check_building_status`
- Purpose: Check real-time status of a builder task and its sub-tasks.
- Arguments: `taskId` string, required.
- Use when: polling any `request_building_action` task.
- Rule: keep polling until terminal success/failure/cancelled status.

## Generic MCP Prompt And Resource Helpers

These are MCP-protocol helper tools surfaced by Hermes for the same server. Use them only when NoCode-X exposes useful prompts/resources; they are not a substitute for application inspection tools.

### `list_prompts`
- Purpose: List available prompts exposed by the NoCode-X MCP server.
- Arguments: none.
- Use when: checking whether the server provides reusable prompt templates.

### `get_prompt`
- Purpose: Retrieve a named prompt from the NoCode-X MCP server.
- Arguments: `name` string required; optional `arguments` object.
- Use when: the user asks to use a server-provided prompt or after `list_prompts` reveals one that matches the task.

### `list_resources`
- Purpose: List resources exposed by the NoCode-X MCP server.
- Arguments: none.
- Use when: discovering server-provided resource URIs.

### `read_resource`
- Purpose: Read a resource by URI.
- Arguments: `uri` string, required.
- Use when: `list_resources` returns a relevant URI.
