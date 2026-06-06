# Observed Plugin: Perplexity API

Status: **observed through MCP fallback; minimal chat-completions scaffold with security/quality concerns**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). Read-only MCP registry fallback returned application data.

## Current Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)

## Installed Objects

### Actions

One action was returned:

- `Perplexity: Chat Completions` (`[REDACTED_ID]`)

### Data Schemas

Three schemas were returned:

- `Perplexity API Configuration` (`[REDACTED_ID]`)
- `ChatCompletionRequest` (`[REDACTED_ID]`)
- `ChatCompletionResponse` (`[REDACTED_ID]`)

### APIs / Jobs / Templates

- No first-class NoCode-X APIs returned.
- No scheduled jobs returned.
- No Perplexity-specific UI templates returned.
- Current app still contains 21 templates from baseline/Vanilla Heroes leftovers, not Perplexity.

## Configuration Schema

`Perplexity API Configuration` contains:

- `api_key`

Important concern: in the observed schema metadata, `api_key` is **not classified as `SECRET`**. API keys should be marked as secret/sensitive.

## Request Schema

`ChatCompletionRequest` contains:

- `model` — required
- `messages[]` — required, items require `role` and `content`
- `max_tokens` — required
- `temperature` — required
- `top_p` — required
- `search_domain_filter`
- `return_images` — required
- `return_related_questions` — required
- `search_recency_filter`
- `top_k` — required
- `stream` — required
- `presence_penalty` — required
- `frequency_penalty` — required
- `response_format`

This is a reasonably useful Perplexity chat-completions request shape, but several optional API parameters are marked required, which may make basic usage unnecessarily heavy.

## Response Schema

`ChatCompletionResponse` contains:

- `id`
- `model`
- `object`
- `created`
- `citations[]`
- `choices[]`
- `usage.prompt_tokens`
- `usage.completion_tokens`
- `usage.total_tokens`

This captures the important Perplexity-specific value: citations.

## Observed Action Implementation Shape

Action signature:

```text
main(REQUEST: ChatCompletionRequest)
```

The rendered JS shows this pattern:

1. `_start()`
2. Read first `Perplexity API Configuration` record via `_getfirstfiltereddatav3`.
3. `_httpcall(...)` with bearer-style auth using `CONFIG.payload.api_key`.
4. Log `RESPONSE`.

Concerns from MCP-rendered JS:

- Extracted auth markers include both `BASIC_AUTH` and `BEARER`; actual invocation appears to use `BEARER`.
- `DATA_XXX_FORMAT` extraction returned empty for output mapping even though `ChatCompletionResponse` exists.
- Endpoint fragment appears malformed/truncated:

```text
ENDPOINT:'https:this._logline({NCX_NAME:
```

This may be MCP rendering loss, but it matches the recurring endpoint/text rendering issue seen in other plugins and should be verified in the action editor/package source.

## Issues

Global `list_all_issues` returned `0` open issues for the current app snapshot.

That means NoCode-X validation did not currently flag the Perplexity objects, despite the concerns above.

## Capability Assessment

Observed coverage:

- one chat completions action;
- API-key configuration;
- request schema with messages/model/sampling/search options;
- response schema with citations, choices, usage.

Not observed:

- model presets/default values;
- streaming support beyond request boolean;
- separate action for structured JSON mode;
- separate search/research abstraction;
- conversation/session persistence;
- citation rendering UI;
- prompt templates;
- moderation/safety controls;
- retry/rate-limit handling;
- NoCode-X APIs;
- scheduled jobs;
- UI templates.

## Quality / Developer Notes

- Mark `Perplexity API Configuration.api_key` as `SECRET`.
- Verify endpoint text in action editor/source; MCP-rendered JS shows a malformed endpoint fragment.
- Verify output mapping to `ChatCompletionResponse`; extraction did not show an output `DATA_XXX_FORMAT` ID.
- Consider making many request tuning parameters optional or providing defaults.
- Add model enum/defaults for currently supported Perplexity models if the platform supports it.
- Add citation-friendly UI or helper action if this is meant to be useful beyond raw API calls.

## Verdict

Minimal but not empty. Useful as a starting point for one Perplexity chat-completions call, but not production-ready and has at least one important credential-classification concern.
