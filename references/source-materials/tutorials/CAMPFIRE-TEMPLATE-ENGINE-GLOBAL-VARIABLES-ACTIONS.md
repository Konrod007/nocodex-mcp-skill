# NoCode-X Campfire: New Template Engine And Global Variables In Actions

Source: user-provided transcript of the developer campfire video `NoCode-X Campfire: Q&A, New template engine & global variables in Actions`.

Treat this as transcript-derived platform knowledge. Verify exact current UI labels, docs, and behavior in the live NoCode-X app before making production commitments.

## Why This Video Matters

This campfire contains several reusable platform primitives and caveats that are useful for NoCode-X skill guidance:

- product direction: NoCode-X as a hybrid AI app generator + no-code visual platform;
- CodeGen-X rationale: generate a codebase from the no-code abstraction for stability, portability, and performance;
- Rocket Mode vs future Vibe Mode positioning;
- new LiquidJS-based template placeholder engine;
- global variables becoming available to Actions through same-name parameters;
- parameter precedence rules between explicit template/action parameters and global variables;
- template editor drag-and-drop workarounds and roadmap ideas;
- subflow semantics in Actions;
- performance distinction between Development and Test/Acceptance/Production;
- client-side vs server-side paging for large DataTables;
- QR code generation, Tailwind/Animatopy availability, dropdown placeholders, UI icon/status improvements.

## Product Direction: AI + No-Code Hybrid

The developers explicitly position NoCode-X away from a pure `AI generates the whole app perfectly` model.

Developer-stated direction:

- NoCode-X will not become exactly like Lovable.
- The team does not believe AI will reliably generate an app exactly as imagined from 0 to 100.
- AI should provide a head start / boost.
- Users should then refine the app through the no-code visual layer.
- Future NoCode-X is described as a hybrid between an AI application generator and a no-code platform.

Practical implication:

- Treat Rocket Mode/Vibe Mode output as draft/scaffolding, not final production truth.
- Skill guidance should recommend inspecting generated pages, actions, data formats, jobs, APIs, logs, issues, and tests.
- Do not frame NoCode-X as merely `Lovable inside NoCode-X`; the developer positioning is more `AI scaffold + visual no-code refinement + generated-code future`.

## Rocket Mode And Future Vibe Mode

Current Rocket Mode behavior described in the transcript:

- starts from pages;
- creates a root page;
- creates several pages it thinks the app needs;
- creates logic behind those pages;
- final logic-generation step is hidden from the user at the time of the transcript;
- process is step-by-step and ends when complete.

Future Vibe Mode direction:

- conversational back-and-forth with AI after Rocket Mode;
- examples: `Change that little word`, `Change the corners on this button`;
- intended to support incremental AI edits;
- future AI scope should not be limited only to pages;
- planned/desired scope includes automated jobs, APIs, and more.

Practical implication:

- For current audits, verify whether a change came from page generation, hidden logic generation, or later manual/no-code edits.
- For builder prompts, include not just pages but desired actions, jobs, APIs, data, rights, and test expectations.
- For future-facing notes, label Vibe Mode as roadmap/context unless confirmed in the live app.

## CodeGen-X Direction

The transcript describes the current application model as:

```text
no-code layer + AI layer -> application abstraction -> interpreted to serve the app in environments
```

CodeGen-X direction:

```text
no-code abstraction -> generated codebase -> run on NoCode-X or own servers
```

Reasons given:

- generated code should remain stable even if NoCode-X gets many platform upgrades;
- once generated code runs correctly, later NoCode-X upgrades should not change that generated code;
- generated code unlocks use of libraries such as Tailwind and auth libraries;
- generated apps can be leaner/faster than the current interpreted abstraction;
- the no-code visual abstraction should remain because it enables graphical editing.

Practical implication:

- CodeGen-X is strategically important for production stability, portability, and performance.
- Do not assume current apps already expose full code export unless verified.
- Distinguish current interpreted-app behavior from future/roadmap generated-code behavior.
- In plugin/export audits, treat `code export` as a capability needing direct evidence, not as a blanket assumption.

## AI Credit Tracking

The transcript distinguishes two AI usage categories:

1. AI used to generate/build parts of the application.
2. AI used inside the application, e.g. an LLM-powered chatbot.

Current tracking stated:

- AI generation usage has a credit counter.
- LLM requests inside the application are logged in application logs.
- No monthly/report-style AI usage report exists at the time of the transcript.
- The team has what they need to build such reports and may put it on the roadmap.

Practical implication:

- For AI cost audits, inspect both builder/generation credit counters and application logs for LLM calls.
- If the user asks for monthly rollups, answer `Unknown / not available from transcript` unless confirmed in the live platform.
- Recommend storing app-level AI usage provenance in application data when building production AI apps: user, model, prompt hash/full prompt when appropriate, generated answer, task ID, status, cost/credits if exposed.

## Template Editor Drag-And-Drop And Navigator Workarounds

Known issue/context:

- In pages with many tightly packed elements, drag-and-drop can be jittery or hard to control.
- Custom buttons often involve a styled horizontal list with icon/title/icon packed into a small area.

Improvements described:

- elements inside horizontal/vertical lists can be reordered through drag handles in a non-WYSIWYG/navigator-like view;
- at this point, the shown reorder works within a list but cannot drag out into another component/list;
- while dragging over a vertical or horizontal list, the list grows slightly to make dropping easier;
- more navigator-based movement between vertical/horizontal lists is on the roadmap;
- keyboard movement shortcuts were suggested and accepted as a useful idea;
- element locking was discussed but not available at the time of the transcript.

Practical implication:

- For difficult UI edits, use the navigator/reorder controls where available instead of only the visual canvas.
- Expect visual drag-and-drop edge cases in dense layouts.
- For precise page-building prompts, ask the builder/AI to use clear container hierarchy and named elements to reduce manual jitter.

## Fixed Position In Style Tab

`Position is fixed` means an element stays in place while the page scrolls.

Use cases mentioned:

- navigation bars;
- floating chat buttons/popups;
- any element that should remain visible during scroll.

Practical implication:

- Use fixed positioning for sticky/floating UI, but test in the actual app preview because some behavior may not fully show inside the template editor.

## Subflow In Actions

The transcript clarifies that `subflow` is primarily an organization/commenting tool at this point.

Behavior stated:

- it does not execute anything by itself;
- it helps group coherent parts of an Action visually;
- example groupings:
  - read from database;
  - process data;
  - write to database;
- comparable to commenting code, but at the action-section level.

Roadmap/history:

- original idea included collapse/expand behavior;
- collapse/expand is still desired but may be implemented differently;
- this could eventually help make loops such as `for each` easier to manage.

Practical implication:

- Use subflows to document large actions and make action graphs readable.
- Do not assume subflow is an executable container unless current live behavior proves it.
- For complex actions, prefer named subflows + logs + tests.

## UI Improvements And Small Feature Notes

Transcript notes:

- type indicator added to parameter creation, matching data schema field type coloring/icons;
- text field margin display in the template editor was fixed;
- reusable components now use different icons than pages;
- homepage has a home icon in the folder overview;
- QR code generation function exists: pass text/URL and choose an image element to render the QR code;
- QR code function has advanced settings such as border, light color, dark color, version range;
- Tailwind and Animatopy classes now work on all page types mentioned, including embed functionality, login pages, and registration pages;
- dropdown field choices can use placeholders;
- placeholders in dropdown choices are replaced in the actual application, not necessarily in the template editor.

Practical implication:

- For audits, homepage/reusable component icons can help quickly identify template roles in UI screenshots.
- Tailwind/Animatopy use is a valid custom-styling/animation path, but verify class availability in the target environment.
- QR code generation can be used for links, event tickets, invitation flows, check-ins, payment links, and sharing flows.

## LiquidJS Template Placeholder Engine

The transcript describes a major placeholder-system upgrade using LiquidJS.

Backward compatibility:

- older pipe-based placeholder formatting remains supported;
- examples included date/datetime formatting, JSON display, and fallback/default values.

New capabilities:

- LiquidJS filters are available through pipe syntax;
- LiquidJS tags are available;
- conditionals are possible in template text/title content;
- loops are possible in template text/title content;
- list element access by index is possible;
- filters include examples such as `abs`, `ceil`, `concat`, `capitalize`, and many others in LiquidJS docs;
- NoCode-X docs link out to LiquidJS docs for features not fully explained in NoCode-X docs.

Example shown conceptually:

```text
{{ name | capitalize }}
```

With global variable `name = tristan`, rendered output becomes:

```text
Tristan
```

Practical implication:

- LiquidJS greatly increases what can be done in text/title placeholders.
- Use it for display formatting, fallback display text, simple list rendering, and conditional display strings.
- Avoid putting complex business logic in template placeholders when an Action or database query would be clearer/testable.
- For app audits, template text may contain meaningful logic now; inspect placeholders, not only visible text.
- Verify exact NoCode-X syntax/current docs before writing implementation instructions.

## Global Variables In Actions

This is the central new primitive from the transcript.

Before this feature:

- global variables could be used in placeholders on pages;
- they could not be accessed from other actions for reasoning/logic.

New behavior described:

- global variables are now available in Actions;
- to access a global variable from an Action, create an Action parameter with exactly the same name as the global variable;
- the action can then use/log/reason with that value;
- works for simple values such as strings;
- also works for nested objects and arrays;
- values can be passed on to Actions.

Example described:

```text
Action A sets global variable:
name = "Tristan"

Action B defines parameter:
name

Action B logs parameter `name`:
Tristan
```

Practical implication:

- Global variables now bridge page/template state and Action logic.
- This enables shared state-driven logic without manually passing every value through every page binding.
- Use same-name Action parameters intentionally; names become important contracts.
- For debugging, inspect both the global variable source and the Action parameter list.

## Global Variable vs Template Parameter Precedence

Important precedence rule from the transcript:

```text
explicit template/action parameter value wins over global variable value
```

Resolution order described:

1. If a template/page/action binding passes a parameter value with that name, use that value.
2. Otherwise, search/use the global variable with the same name.

Example:

```text
Global variable:
name = "Tristan"

An action call passes:
name = "Fabrizio"

Action receives:
name = "Fabrizio"
```

Practical implication:

- A global variable may appear to be ignored if a template/action binding passes the same parameter explicitly.
- Same-name conflicts are a likely source of bugs.
- For debugging wrong values, inspect in this order:
  1. action signature/parameter name;
  2. page/template action binding values;
  3. parent template parameters;
  4. global variable source/setter;
  5. logs/action tests.

Recommended naming:

- Use explicit namespaces for global variables where possible:
  - `auth.currentUser`
  - `ui.activeTab`
  - `filters.status`
  - `cart.total`
- Avoid generic global names like `name`, `id`, `status`, `value` unless scoped by convention.

## Input/Dropdown Enable Bug Fix

Bug described:

- dropdown/input fields could reset after an Action enabled the same field that triggered the action;
- functions such as enable button/dropdown/input field could clear values if they enabled the same field whose change triggered the function.

Fix stated:

- this reset behavior was fixed.

Practical implication:

- If similar behavior appears in a current app, verify live platform version/logs and do not assume this old bug still exists.

## Performance: Development vs Test/Acceptance/Production

The transcript gives a useful production/performance distinction.

Stated behavior:

- Development is always somewhat slower because NoCode-X must show current app state without fully recompiling every time;
- when moving from Development to Test/Acceptance/Production, NoCode-X creates a version and performs optimizations;
- compiled/optimized environments should be faster than Development.

Practical implication:

- Do not judge final production performance only from Development preview.
- For performance audits, test in the appropriate promoted environment when possible.
- Still inspect app design because inefficient data loading can remain slow even outside Development.

## DataTable Performance And Server-Side Paging

The transcript describes a major performance issue/pattern:

- current/older DataTable paging can be client-side;
- client-side paging loads all data, then pages in the browser;
- loading 50,000+ records into the browser is slow;
- server-side paging retrieves only the needed page, e.g. 20 records;
- the team was building an easy function/block for server-side paging on DataTables.

Practical implication:

- For large tables, avoid client-side loading of all rows.
- Use server-side paging/filtering/sorting where available.
- For dashboards/reports, push filters, selected attributes, joins, grouping, and aggregation into database queries where possible.
- If a table is slow, first check row counts, query shape, and whether paging is client-side or server-side.

## Execute Action With Frontend Answer

The transcript starts to mention `execute_action_with_frontend_answer` near the end, but the provided transcript is cut off before the explanation completes.

Known from this transcript only:

- it allows executing an action where the frontend does not wait synchronously for the action;
- the result arrives later;
- detailed behavior is cut off.

Practical implication:

- Treat this as incomplete. Do not write firm implementation guidance from this transcript alone.
- If another campfire contains the full explanation, ingest that source before adding a workflow pattern.

## Skill Updates Suggested By This Transcript

Add/update skill guidance for:

- `CodeGen-X` as roadmap/current strategic direction, separated from current verified export capabilities;
- `Rocket Mode` and future `Vibe Mode` positioning;
- LiquidJS placeholder engine and where template logic may hide;
- global variables in Actions via same-name parameters;
- precedence: explicit template/action params override global variables;
- Action subflows as organizational/comment-like sections, not execution containers;
- dense-layout editor workarounds and fixed positioning;
- Dev vs Test/Acceptance/Production performance distinction;
- DataTable client-side vs server-side paging.

## Verification Checklist For Live Apps

When auditing a target NoCode-X app and this transcript seems relevant, verify:

- whether LiquidJS syntax is available in the current environment;
- exact placeholder syntax and supported filters/tags;
- where global variables are created/set in the app;
- whether Action parameters intentionally match global variable names;
- whether page/template bindings pass explicit values that override globals;
- whether slow DataTables are loading all records client-side;
- whether app was tested in Development only or also Test/Acceptance/Production;
- whether CodeGen-X/export features are actually available in the current account/app;
- whether Tailwind/Animatopy classes render in the target page type;
- whether QR code generation function is present in the current function picker.
