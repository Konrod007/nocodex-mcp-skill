# Massive NoCode-X Update: AI Workflows, OCR, and MCP Integration

Source: user-provided transcript of the developer video titled `Massive NoCode-X Update: Next-Gen AI Workflows, World-Class OCR & MCP Integration!`.

Treat these as transcript-derived platform notes. Verify in the live NoCode-X editor or official docs before making production commitments.

## Covered Transcript Segment

The provided transcript covers:

- updated LLM completion request behavior;
- model catalog updates;
- API-token vs NoCode-X-credit usage;
- new LLM request robustness/observability;
- image generation through the same generative-task infrastructure;
- generated image storage in the media library;
- OCR over media files, including page selection and table output mode.

The video title also mentions MCP integration, but the provided text segment does not include concrete MCP details beyond the title. Do not infer MCP capabilities from this transcript alone.

## Key Platform Changes

### 1. LLM Completion Request Uses Rocket Mode Infrastructure

The transcript says the existing `LLM completion request` action still supports:

- user prompt;
- assistant prompt;
- system prompt;
- placeholder replacement inside prompts;
- model selection;
- custom API token if the user has one;
- fallback to NoCode-X account credits if no external API token is supplied.

The important platform change is that LLM calls now use the same underlying infrastructure as Rocket Mode:

- asynchronous generative-task execution;
- retry behavior;
- more robust execution compared with the previous direct-style LLM request path;
- centralized observability for every LLM request.

Practical interpretation:

- Continue using `LLM completion request` for text generation, classification, extraction, chat-style responses, and AI automation.
- Expect better reliability due to shared generative-task infrastructure.
- When debugging LLM behavior, inspect the generative task/observability records, not only ordinary action logs.

### 2. Updated Model Catalog

The transcript says the model list was updated and includes newer models across families such as:

- Claude;
- Llama;
- Mistral;
- GPT;
- etc.

Practical interpretation:

- Do not hard-code outdated model assumptions in recipes.
- When preparing a builder request, specify quality/cost/latency requirements rather than assuming only one provider/model is available.
- If exact model availability matters, verify the live model selector in the target NoCode-X account.

### 3. LLM Observability / Generative Task Tracking

The transcript says every LLM request from an application can now be inspected with observability details such as:

- request prompt;
- generated answer;
- current task status;
- selected model;
- credit cost.

For image generation, the video shows a task in `generating` status and later `success`, with a displayed credit cost.

Practical use:

- During audits, check whether AI workflows have observable generative-task records.
- For debugging, compare:
  - action input placeholders;
  - final prompt sent to the model;
  - answer returned;
  - model selected;
  - status/error;
  - credit cost.
- For production workflows, consider storing user-facing AI outputs and important metadata in application data records if the built-in observability is not meant as business-state storage.

### 4. Image Generation Action

The transcript demonstrates an LLM/generative action that can generate an image from a text prompt, e.g. `Generate an image of a cat with a mohawk`.

Observed behavior from the transcript:

- prompt text supports placeholder replacement;
- at the time of the demo, one image model was available in that action;
- files can optionally be passed to the model;
- custom GPT/OpenAI API token can be supplied;
- otherwise NoCode-X account credits can be used;
- image generation appears in the generative-task observability UI;
- generated images are automatically stored in the NoCode-X media library.

Practical use:

- Generate marketing images, placeholders, illustrations, social assets, user-specific visuals, or internal design drafts.
- After generation, use normal NoCode-X file/media workflows: attach to email, upload to external storage/FTP, store in another database, show in UI, or pass to another action.
- Track credit cost and latency; image generation may take longer and cost more than text completion.

Cautions:

- Verify content-safety and brand-review requirements before exposing image generation to end users.
- Store provenance such as prompt, user, model, task ID, media ID, and approval status if generated images enter a production workflow.

### 5. OCR Over Media Files

The transcript demonstrates OCR on a media-library file, using an uploaded invoice as an example.

Observed inputs/options:

- get/select a media file by media ID;
- choose pages to analyze;
- page selection is a comma-separated list/range-style input such as page `0`, or `0,1`, or possibly `1 to 10` depending on UI semantics;
- choose how tables are processed;
- table output can be Markdown in most cases;
- HTML table mode may be better when visual structure inside a table matters;
- custom API token can be supplied;
- result can be written to logs, pushed to an API, stored in the database, or used by any downstream logic.

Practical OCR workflows:

```text
Media file invoice/contract/form
-> OCR selected pages
-> Markdown or HTML result
-> LLM extraction / validation
-> structured data record
-> review UI / approval workflow
-> external API / email / storage
```

Useful scenarios:

- invoice extraction;
- receipt processing;
- contract/document intake;
- scanned form processing;
- turning PDFs/images into Markdown for search or AI workflows;
- document ingestion before vector/assistant indexing.

Cautions:

- Page numbering appears zero-based in the demo (`page zero`). Verify in the live action UI before processing multi-page files.
- Markdown table output is usually simpler for downstream LLM/data extraction.
- HTML table output may preserve layout cues better, but may require sanitization and parsing.
- For production, store the source media ID, selected pages, OCR mode, result, extraction status, confidence/review fields if available, and human approval state.

## Debugging Checklist For AI/OCR Workflows

When an AI/OCR NoCode-X workflow fails or gives poor output, check:

1. Was a model selected?
2. Is the custom API token present and valid, or should NoCode-X credits be used?
3. Did placeholder replacement produce the expected final prompt?
4. Is there a generative-task record?
5. What is the task status: queued/generating/success/error?
6. What prompt/input did observability record?
7. What answer/output did observability record?
8. What credit cost was recorded?
9. For image generation: was a media-library file created?
10. For OCR: is the media ID correct?
11. For OCR: are pages selected correctly and using the expected zero/one-based numbering?
12. For OCR tables: should Markdown or HTML output be used?
13. Is the result being logged only, or persisted into business data where needed?
14. Are sensitive documents and generated outputs handled according to the app's data policy?

## Practical Verdict

This update is meaningful because it makes AI features less like isolated helper actions and more like a platform-level generative-task subsystem:

```text
LLM/text generation
image generation
OCR/document understanding
observability/status/cost tracking
media-library integration
```

The strongest reusable NoCode-X patterns are:

- use observability to debug prompt/model/cost issues;
- use generated media as normal media-library assets;
- use OCR as the first step in document-processing workflows;
- combine OCR with LLM extraction and structured database records;
- avoid treating logs/observability as durable business-state storage unless the platform explicitly supports that use.
