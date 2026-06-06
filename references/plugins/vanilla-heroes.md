# Observed Plugin: Vanilla Heroes

Status: **observed through MCP fallback; UI/template pack with placeholder actions and validation issues**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). Normal MCP tool channel temporarily returned `ClosedResourceError`, but `hermes mcp test nocodex-mcp` succeeded and read-only registry fallback returned application data.

## Current Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)

## Installed Objects

### Templates / Pages

MCP returned 21 templates total. In addition to the baseline default templates, `Vanilla Heroes` appears to install a sizeable hero/landing-page UI component set:

Baseline/default templates:

- `Error: not authorized`
- `Error: unknown error`
- `Error: not found`
- `LottieFiles component`

Observed Vanilla Heroes templates/components:

- `White Background Button`
- `Sign-up Form`
- `Colored Border Button`
- `Play Button component (Dark Mode)`
- `Centered screenshot`
- `Colored Border Button (Dark Mode)`
- `Dark mode hero`
- `Colored Background Button`
- `Responsive left-aligned hero with image`
- `Play Button component`
- `Vertically centered hero sign-up form`
- `White Border Play Button (Dark Mode)`
- `Black Border Button`
- `Centered hero`
- `heroes page`
- `Black Border Play Button`
- `Border hero with cropped image and shadows`

`heroes page` is an aggregator page with elements/templates:

- `HEROES_1`
- `CENTERED_SINGUP_FORM_1`
- `LEFT_ALIGN_1`
- `CENTERED_SCREENSHOT_1`
- `CENTERED_HERO_1`
- `CROPPED_IMAGE_1`
- `DARK_MODE_1`

Hero variants observed:

- `Centered hero`
- `Dark mode hero`
- `Responsive left-aligned hero with image`
- `Vertically centered hero sign-up form`
- `Border hero with cropped image and shadows`
- `Centered screenshot`

### Actions

Six actions were returned:

- `Sign up` (`[REDACTED_ID]`)
- `Left button action` (`[REDACTED_ID]`)
- `Execute left button action` (`[REDACTED_ID]`)
- `Right button action` (`[REDACTED_ID]`)
- `Play button action` (`[REDACTED_ID]`)
- `Execute right button action` (`[REDACTED_ID]`)

Action JS inspection showed the direct actions are placeholders that only log text, for example:

- `Sign up`: logs `You are in sign up action.`
- `Left button action`: logs `Left button action has been executed.`
- `Right button action`: logs `Right button action has been executed.`
- `Play button action`: logs `Play button action`

The `Execute left/right button action` actions accept action parameters and call `_action(...)`, but their signatures show null action parameters in the MCP-rendered JS:

- `main(LEFT_BUTTON_ACTION:null)`
- `main(RIGHT_BUTTON_ACTION:null)`

### Data Schemas / APIs / Jobs

- Data schemas: none
- NoCode-X APIs: none
- Scheduled jobs: none

This is expected for a visual component/template pack, but it means the plugin does not provide persistence, backend workflows, or public API endpoints.

## Parameters / Reusability

Templates expose useful customization parameters. Observed examples include:

- `TITLE`
- `DESCRIPTION`
- `LEFT_BUTTON_TEXT`
- `LEFT_BUTTON_ACTION`
- `PLAY_ACTION`
- `PLAY_TITLE`
- `PLAY_SUBTITLE`
- `IMAGE_URL`

Default marketing copy observed:

- `Build Software Faster, Secured instantly!`
- `Build Software Secured instantly!`
- `NoCode-X helps you build high quality, fully customized & secured webapplications quickly`
- `Start for free`
- `Watch Demo`
- `1m 32s`

Some default action parameter values reference action IDs not present in the installed action list, e.g. `[REDACTED_ID]` and `[REDACTED_ID]`, while actual installed action IDs differ. This likely contributes to missing Action issues until the user wires actions manually.

## Issues

Global issue list returned 8 open BUG issues:

- 4 × `MISSING_REQUIRED_FIELD`: `Text` was empty
- 4 × `MISSING_REQUIRED_FIELD`: `Action` was empty

Issue attribution:

- `Sign up`: missing `Text`
- `Left button action`: missing `Text`
- `Right button action`: missing `Text`
- `Play button action`: missing `Text`
- `Execute left button action`: missing `Action` (duplicated twice)
- `Execute right button action`: missing `Action` (duplicated twice)

## Notable Quality Notes

- This plugin is **not empty**; it installs a fairly broad hero/landing-page template set.
- It is mostly frontend/UI, not an API/data/backend plugin.
- Button and play actions are placeholders/loggers; they must be replaced or wired to real actions for a real app.
- Some buttons in nested HTML show `disabled`, so rendered behavior should be checked in the UI before assuming CTA buttons are clickable.
- Some element/template codes contain typos such as `SINGUP_*` instead of `SIGNUP_*`.
- Default copy includes typo/spacing issue: `webapplications`.
- Uses a Google Drive sample image URL and media-library IDs; verify image availability and replace with app-owned assets.

## Capability Assessment

Useful as a visual landing page / hero component pack. It is not useful as a backend integration or workflow package. Production use requires replacing placeholder copy, wiring CTAs/play/signup to real actions, checking responsive rendering, checking button disabled states, replacing images/assets, and resolving open validation issues.
