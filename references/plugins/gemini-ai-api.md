# Gemini AI API Plugin

Status: **observed through MCP**.

Observed in workspace `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`), application `Unnamed Application` (`[REDACTED_ID]`).

## Purpose

Gemini AI integration plugin for sending text prompts to Google's Gemini API and receiving generated text responses.

This plugin appears to install as a plugin-local action plus supporting data schemas, not as an ordinary NoCode-X API object exposed by `list_all_apis`.

## Installed/Observed APIs

- None returned by `list_all_apis`.
- `search_apis("Gemini")`, `search_apis("Google AI")`, and related API searches returned `[]`.

Interpretation: Gemini is represented by actions/data schemas rather than a first-class application API object in the current MCP surface.

## Installed/Observed Actions

### `Gemini AI: API test`

- ID: `[REDACTED_ID]`
- Purpose: test/invoke Gemini API with a request payload and log/store the response.
- Observed input shape: `APITestRequest`.
- Observed output shape: `APITestResponse`.
- Observed configuration dependency: `Gemini AI API configuration`.

### Expected capability

Based on the installed schemas, the action is intended to support text generation with a Gemini request body shaped like:

```json
{
  "contents": [
    {
      "parts": [
        {
          "text": "Prompt text"
        }
      ]
    }
  ]
}
```

And a simplified NoCode-X response shape:

```json
{
  "candidate_responses": [
    {
      "text": "Generated answer"
    }
  ]
}
```

## Installed/Observed Data Schemas

### `Gemini AI API configuration`

- ID: `[REDACTED_ID]`
- Purpose: stores plugin configuration.
- Fields:
  - `API_key`: string, `dataClassification: SECRET`

Setup note: this must be filled after installation. Missing API key/auth configuration is expected post-install setup debt, not by itself evidence of plugin failure.

### `APITestRequest`

- ID: `[REDACTED_ID]`
- Purpose: request payload for Gemini generation.
- Observed schema:
  - `contents[]`
    - `parts[]`
      - `text`: string

This matches the core Gemini generateContent request shape.

### `APITestResponse`

- ID: `[REDACTED_ID]`
- Purpose: simplified response mapping for generated text.
- Observed schema:
  - `candidate_responses[]`
    - `text`: string

## Capabilities Documented

Observed/expected capabilities from installed objects:

1. Store a Gemini API key as a secret configuration value.
2. Accept a text prompt through `APITestRequest.contents[].parts[].text`.
3. Send a Gemini-style `contents/parts/text` generation request.
4. Return generated text through `APITestResponse.candidate_responses[].text`.
5. Log the raw or mapped response through NoCode-X application logs.

Not observed in this plugin snapshot:

- model selection field, e.g. `gemini-1.5-flash`, `gemini-2.0-flash`, etc.;
- temperature/top-p/max tokens parameters;
- system instruction field;
- multimodal input fields such as image/audio/file parts;
- streaming response support;
- embeddings;
- function calling / tool calling;
- safety settings;
- chat/session history abstraction;
- batch APIs;
- explicit OAuth flow. Gemini API key configuration appears to be the intended auth mechanism.

## Post-Install Setup Requirements

Expected after installation:

1. Create or fill one `Gemini AI API configuration` record.
2. Set `API_key`; treat it as a secret.
3. Configure the action's HTTP auth/API-key binding if the UI requires manual selection.
4. Configure request/response data formats if the plugin action shows missing `Data format` validation issues.
5. Provide a test prompt in `APITestRequest.contents[].parts[].text`.
6. Run `Gemini AI: API test`.
7. Check action/application logs for response or API error.

## Observed Issues / Validation Notes

Global issue list after installation included open BUG issues linked to `Gemini AI: API test`:

- `MISSING_REQUIRED_FIELD`: `Authentication method`
- `MISSING_REQUIRED_FIELD`: `Data format`
- `MISSING_REQUIRED_FIELD`: `Text`
- `UNEXISTING_DATA_FORMAT_USED`: invocation `Get first from filtered data` references `Gemini AI API configuration` (`[REDACTED_ID]`) as non-existing

Important interpretation:

- Missing auth/text/data-format fields can be normal immediately after plugin installation because auth and setup happen after installation.
- `UNEXISTING_DATA_FORMAT_USED` should be rechecked after configuration and/or builder refresh because the schema was visible through `list_all_dataschemas`; it may indicate a stale internal reference or validation cache issue.

Per-action issue call for `Gemini AI: API test` returned `[]` in one MCP run while `list_all_issues` showed issues linked to the same action ID. Prefer `list_all_issues` for global plugin validation state and cross-check by action ID manually.

## JavaScript / Logic Notes

`get_action_javascript` returned a TypeScript-like generated action body. The visible shape included:

- `_start()`
- `_getfirstfiltereddatav3` reading `Gemini AI API configuration`
- `_httpcall` intended to call an external HTTP endpoint
- `_logline` logging the response

The extracted JS text appeared truncated or malformed around the endpoint:

```text
ENDPOINT:'https:this._logline(...)
```

Do not conclude the plugin is broken solely from this until after post-install configuration is completed and the rendered UI/action editor is checked. The MCP JS extractor may expose partially assembled code when required fields are still blank.

## Security Notes

- Never expose actual Gemini API keys.
- Treat `Gemini AI API configuration.API_key` as secret material.
- Redact API keys in logs, screenshots, and documentation as `[REDACTED]`.

## Recommended Test Flow

1. Fill `Gemini AI API configuration.API_key`.
2. Open `Gemini AI: API test` in NoCode-X action editor.
3. Confirm auth mechanism/API key placement.
4. Confirm endpoint and method are set.
5. Confirm output data format is `APITestResponse`.
6. Run with a minimal request:

```json
{
  "contents": [
    {
      "parts": [
        {
          "text": "Say hello in one short sentence."
        }
      ]
    }
  ]
}
```

7. Verify `candidate_responses[0].text` or inspect raw logs.
8. Re-run `list_all_issues`; remaining `UNEXISTING_*` or malformed endpoint issues after configuration should be treated as potential plugin/platform bugs.
