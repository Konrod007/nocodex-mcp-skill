# Safety And Limitations

## Safety Rules

- Do not inspect or reveal auth-token files, `.env` values, `mcp_auth.json`, access tokens, or refresh tokens.
- Treat user deletion as destructive and irreversible. Official NoCode-X Users docs state that deleting a user cannot be undone and revokes memberships, permissions, and rights associated with that user.
- Treat `request_building_action` as potentially mutating.
- Treat `create_application` as mutating.
- Prefer read-only inspection tools before any builder request.
- Confirm workspace and application before any app-specific action.
- If the user asks for a change, explain likely affected objects before invoking builder.
- If the user asks only for analysis, do not invoke builder to modify anything.

## Current Capability Boundaries

The current toolset is strong for inspection and debugging:

- APIs, schemas, actions, JavaScript, templates, page HTML, logs, jobs, issues, media.

The current toolset is not yet a full structured mutation API:

- no `update_api`;
- no `update_action`;
- no `update_dataschema`;
- no `update_template`;
- no `apply_patch`;
- no first-class diff/preview;
- no explicit run-test tools.

Use `request_building_action` for changes that require NoCode-X internal builder behavior.

## Environment Handling

Log tools require `environment`. Do not invent environment names. If unknown, ask the user or inspect available NoCode-X UI/context when possible.

## Confidence Labels

Use these labels in final answers when helpful:

- **Confirmed**: directly observed through MCP output.
- **Likely**: inferred from multiple MCP facts.
- **Unknown**: not available from current tools.
- **Needs NoCode-X builder**: requires internal generation or mutation.

## Product-Grade Interaction Pattern

Follow mature devtool UX:

1. Show the current workspace/application when relevant.
2. State what was inspected.
3. Provide the evidence trail.
4. Separate diagnosis from recommendation.
5. Ask for confirmation before mutating operations.
6. Keep the user-facing answer concise, with details available on request.
