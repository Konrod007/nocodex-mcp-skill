# Platform Source Ingestion

Use this when the user provides local NoCode-X documentation, tutorials, exported notes, or supplemental platform materials and asks to improve the NoCode-X skill.

## Goal

Turn source materials into durable, class-level platform guidance without turning one session's files into a narrow one-off skill.

## Workflow

1. Identify source scope: folder path, file count, main indexes, and high-signal files such as `SKILL.md`, `core/`, `references/`, `guides/`, and tutorial indexes.
2. Extract stable platform concepts only:
   - Rocket Mode prompting;
   - UI/template hierarchy;
   - data formats, actions, Scope/State;
   - APIs/integrations;
   - jobs/automation;
   - RBAC/security;
   - design system/plugins;
   - testing/debugging/release;
   - license/resource notes, if explicitly present.
3. Do not mirror entire upstream docs. Distill concise operational playbooks and checklists.
4. Preserve grounding boundaries:
   - label local documentation as `Platform note`;
   - label MCP/browser/log observations as `Confirmed in app`;
   - label unavailable app facts as `Unknown`;
   - do not claim rendered UI behavior, live integrations, or account/license limits unless verified.
5. Prefer updating existing class-level references, especially `references/platform-playbook.md`, over creating many narrow files.
6. Add a pointer in `SKILL.md` or `references/workflows.md` whenever a new support file is added.
7. Validate after edits by loading the skill and the new support file with `skill_view` in the next normal tool-enabled session.

## Pitfalls

- Do not save token files, `.env`, OAuth artifacts, or credentials from local folders.
- Do not encode transient setup failures as durable platform limitations.
- Do not assume the user's target NoCode-X workspace/app uses the same license tier or platform version as the source materials.
- Do not overwrite MCP-first app auditing rules with general platform advice; app facts must still come from MCP/browser/log evidence.
