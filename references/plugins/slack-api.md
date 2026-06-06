# Observed Plugin: Slack API

Status: **observed through MCP fallback; broad Slack Web API scaffold with validation issues**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). Read-only MCP registry fallback returned application data.

## Current Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)

## Installed Objects

### Actions

11 Slack actions were returned:

- `Slack: auth.test`
- `Slack: conversations.list`
- `Slack: conversations.create`
- `Slack:  conversations.join` — note double space after colon
- `Slack: conversations.leave`
- `Slack: conversations.invite`
- `Slack: conversations.kick`
- `Slack: conversations.history`
- `Slack: conversations.replies`
- `Slack: chat.postMessage`
- `Slack: chat.meMessage`

### Data Schemas

13 schemas were returned:

- `Slack API configuration`
- `OAuth test RESPONSE`
- `ConvarsationsList` — typo: likely should be `ConversationsList`
- `CreateConversation RESPONSE`
- `JoinToConversation RESPONSE`
- `LeaveConversation RESPONSE`
- `InviteToConversation RESPONSE`
- `KickFromConversation RESPONSE`
- `ConversationHistory RESPONSE`
- `ConversationReplies RESPONSE`
- `SendMessage RESPONSE`
- `ShareMeMessageToChat RESPONSE`
- `InviteUsers`

`Slack API configuration` contains `userOAuthToken`, classified as `SECRET`.

### APIs / Jobs

- No first-class NoCode-X API objects returned.
- No scheduled jobs returned.

### Templates

Current app contains 25 templates, but no Slack-specific UI templates were observed. The extra non-baseline templates are existing Vanilla Heroes leftovers and duplicated baseline error templates.

Observed duplicated baseline templates after Slack install/current state:

- `Error: not authorized_1`
- `Error: unknown error_1`
- `Error: not found_1`
- `LottieFiles component_1`

This matches the previously observed plugin packaging pattern where some plugins duplicate baseline vanilla error templates.

## Observed Action Implementation Shape

All 11 Slack actions follow the same broad pattern:

1. `_start()`
2. Read first `Slack API configuration` record using `_getfirstfiltereddatav3`.
3. Call Slack endpoint through `_httpcall`.
4. Use bearer-like auth with `userOAuthToken`.
5. Map response to a method-specific response schema.
6. Log response.

MCP-rendered JS includes both `BASIC_AUTH` and `BEARER` auth markers in extracted snippets. Runtime field validation reports missing `Authentication method`, so the rendered action editor/source should be checked before relying on the package.

Some endpoint fragments in MCP-rendered JS still look malformed/truncated, for example:

```text
ENDPOINT:'https:this._logline({NCX_NAME:
```

This may be MCP rendering loss, but it correlates with missing `Text` validation issues and has appeared in other plugins.

## Action Signatures

Observed signatures include:

- `auth.test`: `main()`
- `conversations.list`: `main()`
- `conversations.create`: `main(name:string)`
- `conversations.join`: `main(channel:string)`
- `conversations.leave`: `main(channel:string)`
- `conversations.invite`: `main(channel:string, users: InviteUsers[])`
- `conversations.kick`: `main(channel:string,user:string)`
- `conversations.history`: `main(channel:string)`
- `conversations.replies`: `main(channel:string,ts:string)`
- `chat.postMessage`: `main(channel:string,text:string)`
- `chat.meMessage`: `main(channel:string,text:string)`

## Issues

Global issue list returned 42 open BUG issues, all `MISSING_REQUIRED_FIELD`:

- 20 × missing `Text`
- 11 × missing `Authentication method`
- 11 × missing `Data format`

Issue distribution:

- Most actions have 4 issues each: 2 × missing `Text`, 1 × missing `Authentication method`, 1 × missing `Data format`.
- `auth.test` and `conversations.list` have 3 issues each.

No `UNEXISTING_DATA_FORMAT_USED` was observed in this snapshot for Slack API, unlike several other plugins.

## Capability Assessment

Observed coverage is better than many previous plugins. The plugin covers a useful subset of Slack Web API:

- authentication test;
- list/create/join/leave/invite/kick conversations;
- conversation history and replies;
- post normal messages;
- post `/me` style messages.

Not observed:

- OAuth install/redirect/token exchange flow;
- Slack app manifest/scopes guidance;
- events API or interactivity endpoints;
- slash commands;
- incoming webhooks;
- users.list/users.info;
- files.upload/files.info;
- reactions;
- pins/bookmarks/canvases;
- search;
- pagination/cursor handling in actions;
- rate-limit/retry handling;
- webhook signature verification;
- local persistence of messages/events;
- app APIs or UI templates.

## Quality Notes

- Typo: `ConvarsationsList` should likely be `ConversationsList`.
- Naming issue: `Slack:  conversations.join` has an extra space after colon.
- Baseline templates appear duplicated with `_1` suffixes.
- Current app still contains unrelated leftover objects from prior plugin tests, so use object names rather than global counts for attribution.

## Verdict

Not empty. This is one of the broader API scaffolds observed so far, but it is still not production-ready because all actions have validation issues and the package lacks OAuth lifecycle, event handling, pagination/rate-limit handling, and app-facing APIs/UI.
