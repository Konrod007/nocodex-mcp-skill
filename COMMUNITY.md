# Community overview

This is an unofficial community knowledge base and Hermes skill for working with NoCode-X through MCP.

It is meant for people who are exploring NoCode-X, trying to understand how the platform is structured, or building AI-assisted workflows around NoCode-X applications. The repository collects practical notes, platform concepts, MCP usage patterns, plugin observations, tutorial-derived implementation material, and planning checklists in one place.

The goal is not to replace the official NoCode-X documentation. The goal is to make the platform easier to study, inspect, and use with an AI agent.

Repository: https://github.com/Konrod007/nocodex-mcp-skill

## Short description

An unofficial community-maintained Hermes skill and knowledge base for exploring, planning, auditing, and debugging NoCode-X applications through MCP.

## Medium description

This repository contains a detailed Hermes skill for NoCode-X MCP workflows. It helps AI agents and users inspect NoCode-X workspaces and applications, understand platform concepts, audit objects such as Data Formats, Actions, Templates, APIs, Jobs, Issues, Logs, and plugins, and plan applications using evidence from MCP observations, official documentation, and tutorial materials.

It is especially useful if you want a structured way to learn how NoCode-X works internally instead of treating it as a black-box no-code builder.

## Community post

I started an unofficial community repository for people who want to explore NoCode-X more deeply and use it with AI agents:

https://github.com/Konrod007/nocodex-mcp-skill

It is a Hermes skill plus a growing knowledge base for NoCode-X MCP workflows. The repo collects practical notes on how to inspect applications, understand platform objects, audit plugins, plan app architecture, and compare what is visible through MCP with what is described in the official docs.

Inside, there are references for:

- NoCode-X platform concepts;
- workspaces, applications, users, developers, environments, and publishing;
- Data Formats, Actions, Templates, APIs, Jobs, Groups, Rights, Issues, Logs, and plugins;
- MCP tool usage patterns and fallback workflows;
- debugging and safety checklists;
- plugin audit notes;
- official documentation planning notes;
- detailed tutorial and video-transcript-derived implementation materials.

The goal is to make NoCode-X easier to study and reason about. If you are trying to understand what the platform can do, how applications are structured, or how an AI agent can help inspect and plan NoCode-X apps, this repo should be useful.

It is unofficial and community-maintained. It does not replace the official docs. It is more of a field notebook: observed behavior, practical recipes, open questions, and reusable workflows for AI-assisted NoCode-X work.

## What is inside

### Hermes skill

`SKILL.md` defines how Hermes should approach NoCode-X MCP tasks. It tells the agent when to inspect, when to be careful with mutating actions, how to treat evidence, and which reference files to load for different tasks.

### Platform playbook

`references/platform-playbook.md` summarizes important NoCode-X platform concepts and planning patterns:

- workspaces and applications;
- data formats and schema planning;
- actions and logic;
- template/page planning;
- APIs and generated CRUD;
- jobs and scheduled automation;
- groups, rights, authentication, and authorization;
- publishing, testing, and DTAP environments;
- security, backups, audit logs, and resource planning.

### Official docs planning notes

`references/official-docs-planning.md` summarizes important official NoCode-X documentation sections that are useful for planning applications. It is designed as a practical planning reference, not a replacement for the official documentation.

### MCP workflows and tooling notes

The repository includes workflow notes for using NoCode-X through MCP, including fallback approaches when a normal MCP tool surface is unavailable.

Useful files include:

- `references/tools-reference.md`
- `references/workflows.md`
- `references/mcp-transport-fallback.md`
- `references/debugging-playbook.md`
- `references/safety-and-limitations.md`

### Plugin and template audit notes

The repository includes community audit notes for NoCode-X plugins and application templates. These notes help identify:

- what objects a plugin installs;
- which Data Formats, Actions, Templates, APIs, or Jobs appear;
- what setup is probably still required;
- which validation issues may be expected;
- which issues may be platform or plugin defects;
- where secrets or token fields should be treated carefully.

### Tutorial and transcript-derived materials

The repository intentionally keeps detailed tutorial notes and video-transcript-derived materials under:

`references/source-materials/`

These materials are useful because they preserve concrete implementation lessons. They help the skill recover real patterns from examples, such as authentication flows, CRUD screens, dashboards, API integrations, LLM automations, email integrations, vector database usage, and plugin-based workflows.

### Safety and evidence policy

The skill is designed to avoid guessing. It separates:

- MCP observations;
- official documentation claims;
- tutorial-derived implementation notes;
- hypotheses;
- unknowns.

That matters because NoCode-X applications can contain real data, credentials, production environments, and destructive operations. The repository tries to make AI-assisted work safer by documenting what should be verified before acting.

## Who this is useful for

This repository may be useful if you are:

- learning NoCode-X and want a deeper technical map of the platform;
- using Hermes or another AI agent to inspect NoCode-X applications;
- comparing official docs with observed MCP behavior;
- planning a NoCode-X application before building it;
- auditing plugins or marketplace templates;
- debugging Actions, APIs, Jobs, Templates, Data Formats, or Issues;
- building repeatable workflows for NoCode-X app reviews;
- collecting open questions for the NoCode-X team.

## What this is not

This repository is not official NoCode-X documentation.

It is not a guarantee that any plugin, template, or workflow is production-ready.

It is not a substitute for checking the current NoCode-X UI, official docs, application logs, rendered pages, and MCP outputs.

It is a public working notebook and AI-agent skill that can be corrected and extended over time.

## How the community can help

Useful contributions include:

- corrections to inaccurate notes;
- links to official documentation pages;
- better explanations of NoCode-X concepts;
- tested implementation recipes;
- MCP inspection examples;
- plugin audit updates;
- safety improvements;
- clarified terminology;
- examples of real planning workflows with private data removed.

Please do not submit secrets, private workspace IDs, real user data, API keys, OAuth tokens, cookies, private app URLs, or proprietary app logic.

## Suggested GitHub repository description

Unofficial community Hermes skill and knowledge base for exploring, planning, auditing, and debugging NoCode-X applications through MCP.

## Suggested social preview text

A community field notebook for NoCode-X MCP: platform concepts, app planning notes, plugin audits, debugging workflows, and detailed tutorial-derived implementation material for AI-assisted NoCode-X work.
