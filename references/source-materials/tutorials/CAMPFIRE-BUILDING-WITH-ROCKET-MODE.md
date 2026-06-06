# NoCode-X Campfire: Building With Rocket Mode

Source: user-provided transcript of the developer campfire video `NoCode-X Campfire: Building with Rocket Mode`.

Video URL: `https://www.youtube.com/watch?v=l7IPDecenLA`

Treat this as transcript-derived platform knowledge. Several features are explicitly described as in development / not yet production-released in the transcript. Verify current production availability in the live NoCode-X app before making capability claims.

## Why This Video Matters

This campfire is a practical Rocket/Rocket Mode build session. It shows:

- building a landing page from a prompt without manual drag/drop;
- skipping detailed Intent Canvas planning and building directly at realization level;
- folder strategy intent for generated artifacts;
- AI to-do/task progress;
- token/credit considerations;
- generated animations, CSS, JavaScript, media images, and standard NoCode-X components;
- iterative small-change prompting;
- prompt specificity using existing element names/text;
- page-selection scope rules for AI changes;
- observability surfaces that AI can or will use: logs, issues, tests, job runs;
- AI undo / prompt reuse / future app branches;
- Intent Canvas realization graph showing pages, actions, data formats, and edges;
- known instability before production release.

## 1. Canvas Is Optional For Direct Build

The video starts by acknowledging Intent Canvas but then skips it.

Key point:

- users are not required to fully use the canvas first;
- they can go directly to realization/building and prompt Rocket/Rocket Mode to create app artifacts.

Practical use:

- For quick prototypes, direct build is acceptable.
- For serious/production work, Intent Canvas review remains useful before broad generation.
- After direct generation, use Intent Canvas/Visual Development Mode to inspect what was created.

## 2. Application Intent, Look-And-Feel, Design System, Folder Strategy

The transcript reiterates current canvas foundations:

- application intent describes what the app should do;
- look-and-feel intent describes visual direction;
- a design system can be generated from look-and-feel;
- a folder strategy can instruct the AI how to organize generated artifacts.

Folder strategy example:

```text
For every feature, add a folder.
Bundle everything related to that feature inside that folder.
```

Practical use:

- Define folder strategy before large app generation.
- Use feature-based folders for larger applications; root-only is acceptable for simple pages.
- Ask AI or use canvas buttons; transcript says both routes can trigger the same underlying behavior.

## 3. Initial Landing Page Prompt Pattern

The demo prompt asks for a single landing page for a fictional space startup:

```text
Void Runner
Recruitment terminal for space pirates
Aesthetic: gritty high-tech, Aliens meets Cyberpunk
Design specs: color palette, typography, starfield background, scan-line overlay
Header, hero section, subline, cards, manifest/email capture, CTA button
Footer as scrolling ticker with fake sector coordinates/status updates
```

Practical prompt pattern:

- give app/page name;
- state concept/domain;
- state aesthetic references;
- provide design specs;
- enumerate sections/components;
- specify data capture/forms;
- specify animation/effects if desired.

Caveat:

- a broad first prompt is useful for scaffolding, but the transcript later calls broad prompts a bit like a lottery.
- For controlled production changes, use smaller precise prompts.

## 4. AI To-Do List And Progress

The AI response shows a to-do list. In the demo:

- first a single item appears;
- the list expands as the AI plans work;
- tasks get checked off;
- example tasks include creating a page, creating HTML/CSS/JavaScript, and setting the page as homepage.

Practical use:

- Use the AI task list as a progress/debug signal.
- If the result is incomplete, compare visible artifacts to the AI's to-do list and final status.

## 5. Token/Credit Considerations

The transcript says the team focused on reducing token usage and credits.

Example estimate from the demo:

- first/biggest generation step around 300 credits / about 30 cents;
- subsequent smaller steps should cost less.

Practical use:

- Prefer small iterative changes after initial scaffold.
- Use cancel early when output goes wrong.
- Avoid asking for many generated images at once if image tooling is unstable or expensive.

## 6. AI Tools And Future MCP Exposure

The transcript says the AI can do much of what users can do in the editor, and the goal is to make those tools work 100%.

Planned direction:

- expose Rocket/Rocket Mode not only through the NoCode-X UI;
- expose it through a NoCode-X MCP server;
- external editors/agents such as Claude/Code-like tools could connect and instruct NoCode-X.

Use case mentioned:

- backend in NoCode-X and frontend in a separate code editor/project.

Practical use:

- Treat current UI Rocket tools and future MCP tools as related surfaces.
- For external-agent workflows, require verification of exact tool availability in the configured MCP server.

## 7. Generated Page Capabilities

The generated Void Runner page includes:

- starfield background with small fading/twinkling dots;
- scanline/old-monitor style;
- cards with hover animation;
- flickering/signed-article animation;
- ticker footer;
- CSS animations;
- some JavaScript when requested/needed.

The transcript says NoCode-X added page animations to the AI toolbox.

Practical use:

- AI can generate visual/animated pages, not only static blocks.
- Inspect local styles to see CSS keyframes/classes.
- Inspect local JavaScript for scroll/interaction behaviors.

## 8. CSS vs JavaScript Animations In Editor

The transcript distinguishes editor behavior:

- pure CSS animations can run inside the editor/design view;
- JavaScript is not executed inside the editor for safety/obvious reasons;
- JavaScript-driven animations must be verified in live preview.

Examples:

- ticker footer can be CSS animation;
- star twinkle can be CSS keyframes;
- glitch animation can be CSS;
- scroll-into-view card animations may require JavaScript to detect viewport entry and add classes.

Practical use:

- When an animation works in preview but not editor, check whether it depends on JS.
- When inspecting generated pages, review both local CSS and local JS.

## 9. Media Generation And Media Library

The demo asks AI to create an image for the `Renegade Tech` card.

Observed behavior:

- AI uses a media/image-generation tool;
- it uses the application/page look-and-feel/design system to match colors/style;
- generated image is stored in the media library;
- AI can add the media as a NoCode-X media image component;
- media can be placed inside an existing card and styled with classes.

Example instruction:

```text
Create a cool-looking image for the card 'Renegade Tech'. Make sure this blends in with the look and feel of this card.
```

Follow-up instruction:

```text
Use the image 'Renegade Tech' from the media library on the card 'Renegade Tech' on the homepage.
```

Practical use:

- Separate image generation from placement when stability matters.
- Reference exact card/component names and media names.
- Verify both media library creation and rendered placement.

## 10. Generated Pages Use Standard Editable Components

The transcript emphasizes that generated UI is not merely one monolithic HTML blob.

In Visual Development Mode, cards appear as standard components:

- vertical list;
- title elements;
- editable card/component structure;
- image components;
- local styles.

Practical use:

- After generation, inspect the component tree.
- Prefer generated standard components when later no-code editing is important.
- If AI creates too much custom HTML, ask it to refactor into editable NoCode-X components where possible.

## 11. Prompting Guidance: Small, Precise Steps

Steve asks for prompting tips. Tristan's advice:

- short, small steps;
- be as precise as possible;
- broad initial page prompts are acceptable for first scaffold but are lottery-like;
- reference exact visible text or object names;
- use created element names if available.

Example:

- if an element is named `VR Headline`, using that name in the prompt helps the AI know exactly where to change.
- referencing text on the page can also work, but object names are better for large pages.

Practical use:

- Use exact element/template/action/data names in builder prompts.
- For large pages, select the relevant component and prompt against that selection.
- Keep follow-up prompts narrow and test after each change.

## 12. Scope Of AI Changes From Editor Selection

The transcript answers where to initiate changes from Visual Development Mode.

Rule described:

- if a specific selected element is targeted, AI changes only that selected element;
- if the top-level element/container is selected, AI can change that element and all its children.

Practical use:

- Select the smallest relevant component before asking AI to change it.
- Select the top-level container only for broader layout changes.
- Use selection scope as a guardrail against accidental page-wide edits.

## 13. Conversation Memory And Chat History

The transcript says the AI has memory of the current discussion, similar to chat with LLMs.

Details:

- previous conversation context can be reused;
- after a server restart, being more explicit may be necessary;
- chat history is tied to the same application and same user;
- history persistence was still not fully implemented/perfect in the transcript.

Practical use:

- Do not rely solely on implicit memory for important changes; restate target page/component and desired outcome.
- For reproducibility, keep key prompts or use prompt reuse.

## 14. Browser Dictation

The demo uses a microphone/dictation icon to speak a prompt.

Transcript detail:

- dictation uses built-in browser speech recognition;
- it does not cost tokens/credits;
- it is only converting speech to prompt text.

Practical use:

- Dictation can speed prompt entry but still review/edit the generated text before submitting.

## 15. Avoid Multi-Image Loops While Tooling Is Unstable

The demo asks AI to create a crew-members section but explicitly says `Do not add images`.

Reason:

- image tool was still being worked on;
- adding more than one image at once could cause looping or unnecessary work.

Practical use:

- For current/unstable image workflows, generate and place images one at a time.
- Avoid broad prompts like `add images to all cards` until tooling is verified.

## 16. Guardrails Against Breaking Pages

The transcript states the team is focusing on AI changing pages without breaking them.

Known issue:

- the demo encounters a case where adding a login button breaks the page.

Developer posture:

- this is why the feature was not yet released to production at the time;
- known bugs should be fixed before production release;
- unknown bugs after release are expected and fixable.

Practical use:

- Treat Rocket-generated changes as potentially destructive until verified.
- Use small changes, selection scope, prompt reuse, undo/versioning, and preview checks.
- Verify page structure and styles after each AI edit.

## 17. Observability Surfaces For AI Debugging

The transcript explains that the team is adding observability so AI has enough context to debug.

Surfaces mentioned:

- application logs;
- Issues;
- tests;
- job run history/logs.

Current/planned behavior described:

- AI can read logs and determine action problems;
- AI can inspect issues;
- next step: AI will run tests and inspect test results;
- AI can loop back and fix based on test results;
- job run overview will show every run of every job, with related logs for that run;
- AI will eventually use job run observability when troubleshooting failed jobs.

Practical use:

- Before asking AI to fix an app, collect logs/issues/tests/job runs.
- For generated action/job bugs, require AI to consult observability rather than guessing.

## 18. Prompt Reuse, Undo AI Changes, And Branches

The transcript highlights two UI controls near prompts/results:

- `reuse the prompt`: copies the prompt back into input;
- `undo the changes of the AI`: reverts all changes made by that AI change block.

Broader direction:

- AI changes should produce before/after app versions;
- users should be able to switch between them;
- this leads toward application branches.

Practical use:

- Use prompt reuse to iterate without retyping.
- Use AI-change undo for safety after a bad generation.
- For important production changes, think in versions/branches rather than one-way edits.

## 19. Responsiveness

The transcript says AI can create responsive pages/CSS.

Example guidance:

- if cards are side-by-side, ask AI to stack them on smaller screens;
- verify responsiveness in the editor's responsive/device preview;
- inspect generated local CSS for media queries/responsive rules.

Practical use:

- Always ask explicitly for mobile/tablet behavior when it matters.
- QA generated pages at multiple viewport widths.

## 20. Intent Canvas Levels And Realization Graph

The transcript references canvas levels:

```text
Foundations
Dynamics
Realization
```

Dynamics contains personas and customer journeys.

Realization contains actual application nodes.

Observed graph semantics:

- green/page nodes represent pages;
- action nodes can appear, e.g. `redirect_to_login`;
- data format nodes can appear, e.g. `User`;
- lines/edges connect pages to actions and actions to data;
- edge labels explain triggers/operations, e.g. click button, redirect, fetch data record, write/delete/update.

Practical use:

- Use the realization graph to understand app flow without manually testing every connection.
- Verify UI-to-action and action-to-data relationships visually.
- Use graph issues/red nodes as starting points for debugging.

## 21. Issues From Required Arguments

The demo manually creates an action fetching data by ID but leaves required ID empty.

Observed behavior:

- node is marked red;
- hover shows issue such as `required argument ID was empty`;
- observability panel shows a real app bug;
- after fixing the required argument, the bug is closed;
- after refresh, the issue should disappear from canvas.

Practical use:

- Required-argument problems are visible both in graph and observability.
- When action/data nodes are red, inspect missing required parameters first.
- After fixing, refresh/recheck issues to confirm closure.

## 22. Login Flow Demo Was Incomplete

The intended demo goal:

- add login button to header;
- create login page;
- link button to login page;
- ensure login page works.

What actually happened:

- server issues interrupted the demo;
- adding login button appeared to break a page;
- later AI created a `redirect_to_login` action;
- presenter manually added a button, bound it to action, and used this to show graph edges;
- full working login flow was deferred to a future campfire.

Practical use:

- Do not cite this transcript as proof of a fully working AI-generated login flow.
- It is evidence for graph/action/page linking concepts and current development direction.

## 23. Server/Development Environment Instability

The transcript mentions development server restarts due to cheap/special compute provider capacity being reclaimed.

Practical use:

- Treat demo failures as partly dev-environment related, but still note the actual user-visible instability.
- For production availability claims, verify in the current live production app.

## Skill Guidance Updates From This Source

This transcript supports these reusable patterns:

- Use broad prompts for first scaffold, then small precise prompts for changes.
- Reference exact element names, visible text, page names, media names, and action names.
- Use selected-element scope to control AI change blast radius.
- Generate/place media one at a time when stability matters.
- Distinguish CSS animations from JavaScript behavior during editor vs preview QA.
- Check local CSS/JS and component tree after generated visual effects.
- Use logs/issues/tests/job runs as AI debugging context.
- Treat AI undo/version/branch concepts as key safety primitives.
- Use realization graph to trace page -> action -> data flows and required-argument issues.
- Mark pre-production Rocket/MCP features as roadmap/in-development unless verified live.

## Verification Checklist For Live Apps

When applying this source to a current NoCode-X app, verify:

- whether Rocket/Rocket Mode direct build is available in the target environment;
- whether folder-strategy intent exists and is used by generation;
- whether AI to-do list/task progress is visible and reliable;
- whether generated pages use editable components rather than only HTML blobs;
- whether generated images appear in the media library and can be inserted as media components;
- whether AI can safely modify selected components without affecting siblings/page-wide content;
- whether prompt reuse and AI-change undo are available;
- whether before/after versions or branches exist;
- whether logs, issues, tests, and job-run observability are available to AI;
- whether CSS animations run in editor and JS animations require preview;
- whether realization graph shows page/action/data nodes and labeled edges;
- whether missing required arguments create visible issues and close after fixes;
- whether production build currently supports the demonstrated Rocket features.
