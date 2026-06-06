# Security Policy

## Reporting Security Issues

If you find sensitive data in this repository, please open a private report if GitHub security advisories are enabled, or contact the maintainer directly. If private reporting is not available, open a minimal public issue without including the secret value.

## What Counts As Sensitive

Do not publish:

- API keys;
- OAuth access tokens;
- OAuth refresh tokens;
- bearer tokens;
- client secrets;
- passwords;
- private keys;
- cookies;
- session files;
- `.env` files;
- MCP auth files;
- private workspace/application IDs tied to real private apps;
- private customer/user data;
- logs containing secrets or personal data.

Use `[REDACTED]` instead.

## Maintainer Checklist Before Releases

Run at least one secret scan before publishing or tagging:

```bash
grep -RInE --exclude-dir=.git \
  '(api[_-]?key|secret|token|password|passwd|bearer|authorization|refresh[_-]?token|access[_-]?token|client[_-]?secret|BEGIN (RSA|OPENSSH|PRIVATE) KEY|mcp_auth|\.env|credentials|cookie|session)' .
```

If available, also run:

```bash
gitleaks detect --source . --no-git
trufflehog filesystem .
```

Review matches manually. Many documentation files mention token/secret fields as examples; that is acceptable only when no real values are present.

## No Production Guarantee

This repository is documentation and skill material. It does not guarantee security or production readiness of any NoCode-X app. Always verify authentication, authorization, data classification, audit logs, generated APIs, jobs, and secret handling in the target application.
