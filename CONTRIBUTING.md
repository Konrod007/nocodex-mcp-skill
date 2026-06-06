# Contributing

Thanks for helping improve this NoCode-X MCP Hermes skill.

## Contribution Goals

Good contributions make the skill more grounded, practical, and verifiable. Preferred contributions include:

- verified end-to-end implementation recipes;
- NoCode-X MCP tool examples;
- corrections to platform assumptions;
- official documentation links with concise summaries;
- clarified app-planning patterns;
- plugin audit corrections;
- security/RBAC clarifications;
- known pitfalls with reproduction steps;
- examples of logs, issues, and validation flows.

## Evidence Levels

Please label the evidence behind a claim:

- `Official docs`: confirmed from docs.nocode-x.com or other official NoCode-X material.
- `MCP observation`: observed through NoCode-X MCP tools.
- `Rendered UI observation`: observed in the browser UI.
- `Tutorial/video`: derived from a lesson, transcript, or implementation walkthrough.
- `Hypothesis`: plausible but not yet verified.
- `Unknown`: explicitly not known yet.

## Do Not Contribute

Do not submit:

- real API keys;
- OAuth tokens;
- passwords;
- private keys;
- cookies;
- `.env` files;
- private workspace/application URLs;
- private user/customer data;
- private business plans or app-specific proprietary logic;
- screenshots or logs containing secrets or personal data.

Replace sensitive values with `[REDACTED]`.

## Preferred Recipe Format

For implementation recipes, use this structure:

```md
# Recipe: <name>

## Goal

## Source / Evidence

## Required NoCode-X Objects
- Data Formats
- Actions
- Templates / Pages
- APIs
- Jobs
- Groups / Rights

## Step-by-Step Implementation

## Expected Logs / Issues

## Verification Checklist

## Common Pitfalls

## Open Questions
```

## Pull Request Checklist

Before opening a PR:

- [ ] No secrets or private data are included.
- [ ] Evidence level is stated for important claims.
- [ ] Official links are included where relevant.
- [ ] Unknowns are labelled, not guessed.
- [ ] New references are linked from `SKILL.md` or a relevant index file.
- [ ] Large copied third-party material is justified, attributed, and safe to publish.

## Language

Repository metadata and Git history are in English. Technical terms should keep the exact product/API/file names used by NoCode-X.
