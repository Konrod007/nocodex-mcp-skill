# NoCode-X MCP Hermes Skill

Unofficial community-maintained Hermes skill and knowledge base for working with NoCode-X through MCP.

This repository is designed for AI agents and developers who need practical, evidence-based guidance for inspecting, debugging, auditing, and planning NoCode-X applications.

> Status: unofficial, community-maintained, research-oriented. This repository is not affiliated with, endorsed by, or maintained by NoCode-X / Co-Dex.eu BV unless explicitly stated by them.

## Community Overview

For a community-facing explanation of what this repository contains and why it may be useful, see [`COMMUNITY.md`](COMMUNITY.md).

## What This Repository Contains

- A Hermes `SKILL.md` for NoCode-X MCP workflows.
- Reference playbooks for NoCode-X platform concepts, application planning, debugging, safety, and MCP usage.
- Plugin and template audit notes collected from practical NoCode-X exploration.
- Official-documentation planning notes summarizing important NoCode-X docs pages.
- Source tutorial materials, including detailed video transcript notes, kept intentionally so the skill can cite and learn from concrete implementation lessons.
- A vendor roadmap / question list for NoCode-X developers.

## Why This Exists

NoCode-X is powerful but broad. For an AI agent to help reliably, it needs more than generic low-code advice. It needs:

- platform vocabulary;
- MCP tool usage patterns;
- app audit methodology;
- examples of real implementation flows;
- known pitfalls and open questions;
- a strict distinction between observed facts, official documentation, and hypotheses.

This repository turns local research into a reusable skill that can be reviewed, corrected, and extended in public.

## Installation

Clone this repository into your Hermes skills directory:

```bash
# Windows Git Bash example
mkdir -p '/c/Users/<user>/AppData/Local/hermes/skills/mcp'
git clone https://github.com/Konrod007/nocodex-mcp-skill.git \
  '/c/Users/<user>/AppData/Local/hermes/skills/mcp/nocodex-mcp'
```

Or copy the folder manually to:

```text
C:\Users\<user>\AppData\Local\hermes\skills\mcp\nocodex-mcp
```

Then start a fresh Hermes session and load the skill:

```text
skill_view(name='nocodex-mcp')
```

## Main Files

```text
SKILL.md
references/platform-playbook.md
references/official-docs-planning.md
references/platform-tutorial-sources.md
references/tools-reference.md
references/workflows.md
references/debugging-playbook.md
references/safety-and-limitations.md
references/vendor-roadmap.md
references/plugin-developer-issues.md
references/plugins-catalog.md
references/source-materials/
```

## Source Materials And Video Transcripts

This repository intentionally keeps detailed tutorial notes and full video-transcript-derived materials under:

```text
references/source-materials/
```

Reason: the goal is to build a highly detailed operational skill, not a short marketing summary. The transcripts and lesson notes help the agent cite concrete implementation examples and recover practical steps when planning or debugging NoCode-X apps.

Publication note:

- These materials are included for community research, education, interoperability, and documentation improvement.
- Official NoCode-X documentation and product materials remain the property of their respective owners.
- If any rights holder wants content removed, shortened, or replaced with links/summaries, please open an issue or contact the maintainer.

## Recommended Usage

Use this skill when you need to:

- inspect a NoCode-X workspace/application through MCP;
- audit APIs, Data Formats, Actions, Templates, Jobs, Issues, Logs, or plugins;
- prepare a precise NoCode-X builder request;
- debug a broken NoCode-X app;
- plan a NoCode-X application architecture;
- compare observed MCP facts with official documentation;
- identify missing documentation or questions for NoCode-X developers.

## Evidence Policy

The skill follows a strict evidence policy:

- MCP facts are treated as observed application facts.
- Official docs notes are treated as official-documentation claims.
- Tutorial/video notes are treated as implementation-learning sources.
- Hypotheses must be labelled as hypotheses.
- Unknowns must be reported as `Unknown`, not invented.

## How NoCode-X Developers Can Help

The most valuable contributions would be verified implementation recipes and clarifications, especially:

1. End-to-end app examples.
2. CRUD from Data Format examples.
3. Advanced database query examples: joins, grouping, aggregation, filters.
4. Page-level Action parameter examples.
5. Jobs: runtime limits, retry, concurrency, cancellation, logs.
6. Webhook/API/event-log/snapshot patterns.
7. RBAC enforcement details.
8. User deletion vs deactivation behavior.
9. MCP tool map: read-only vs mutating tools.
10. Secrets handling: storage, rotation, log exposure, MCP exposure.

See also:

```text
references/vendor-roadmap.md
references/official-docs-planning.md
```

## Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md).

## Security

Do not submit secrets, API keys, OAuth tokens, cookies, real user data, private app URLs, or private workspace/application IDs.

See [`SECURITY.md`](SECURITY.md).

## License

This repository is released under the MIT License for original community-authored content. Third-party product names, trademarks, official documentation, and tutorial materials remain owned by their respective rights holders. See [`NOTICE.md`](NOTICE.md).
