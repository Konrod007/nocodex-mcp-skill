# Observed Plugin: Gmail Postmaster Tools API

Status: **observed through MCP fallback; partial read-only Gmail Postmaster scaffold with validation issues**.

Observed in workspace `[REDACTED_WORKSPACE]`, application `Unnamed Application` (`[REDACTED_ID]`). Normal MCP tool channel had recently returned `ClosedResourceError`; read-only registry fallback returned application data.

## Current Context

- Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)
- Application: `Unnamed Application` (`[REDACTED_ID]`)

## Installed Objects

### Actions

- `Gmail Postmaster: Get Domains List` (`[REDACTED_ID]`)
- `Gmail Postmaster: Get Domains TrafficStats List` (`[REDACTED_ID]`)
- `Gmail Postmaster: Get Domain by Domain Name` (`[REDACTED_ID]`)

### Data Schemas

- `DomainsList` (`[REDACTED_ID]`)
- `Domain` (`[REDACTED_ID]`)
- `TrafficStats List` (`[REDACTED_ID]`)
- `Google: Service user json` (`[REDACTED_ID]`)
- `Google: API Key json` (`[REDACTED_ID]`)

The two Google credential schemas may come from a generic Google API dependency package rather than this plugin itself.

### APIs / Jobs / Templates

- No first-class NoCode-X API objects returned.
- No scheduled jobs returned.
- No Gmail Postmaster-specific UI templates returned. Existing templates were baseline/default pages and previously installed Vanilla Heroes templates.

## Schema Summary

### `Domain`

Fields:

- `name`
- `createTime`
- `permission` enum:
  - `PERMISSION_UNSPECIFIED`
  - `OWNER`
  - `READER`
  - `NONE`

### `DomainsList`

Fields:

- `domains[]` containing `name`, `createTime`, `permission`
- `nextPageToken`

### `TrafficStats List`

Fields include:

- `trafficStats[]`
- `name`
- `userReportedSpamRatio`
- `ipReputations[]`
  - `reputation`: `REPUTATION_CATEGORY_UNSPECIFIED`, `HIGH`, `MEDIUM`, `LOW`, `BAD`
  - `ipCount`
  - `sampleIps[]`
- `domainReputation`
- `spammyFeedbackLoops[]`
  - `id`
  - `spamRatio`
- `spfSuccessRatio`
- `dkimSuccessRatio`
- `dmarcSuccessRatio`
- `outboundEncryptionRatio`
- `inboundEncryptionRatio`
- `deliveryErrors[]`
  - `errorClass`: `DELIVERY_ERROR_CLASS_UNSPECIFIED`, `PERMANENT_ERROR`, `TEMPORARY_ERROR`
  - `errorType`: `DELIVERY_ERROR_TYPE_UNSPECIFIED`, `RATE_LIMIT_EXCEEDED`, `SUSPECTED_SPAM`, `CONTENT_SPAMMY`, `BAD_ATTACHMENT`, `BAD_DMARC_POLICY`, `LOW_IP_REPUTATION`, `LOW_DOMAIN_REPUTATION`, `IP_IN_RBL`, `DOMAIN_IN_RBL`, `BAD_PTR_RECORD`
  - `errorRatio`

## Observed Action Implementation Shape

All three actions use roughly this pattern:

1. Read first `Google: Service user json` record with `_getfirstfiltereddatav3`.
2. Create GCP access token with `_creategcpaccesstoken`.
3. Use bearer auth for a Google Postmaster HTTP GET call.
4. Map response to `DomainsList`, `Domain`, or `TrafficStats List`.
5. Log the response.

Observed hard-coded delegated user:

- `DELEGATED_USERMAIL: 'rafal@nocode-applications.com'`

This should be replaced/configured for the target Google Workspace tenant before production use.

MCP-rendered JS has malformed/truncated fragments similar to other Google plugins:

- `SCOPE:'https:`
- `ENDPOINT:'https:`
- `TEXT:'https:`

This may be MCP rendering loss, but it aligns with missing `Text`, `Authentication method`, and `Data format` validation issues, so the rendered action editor should be checked.

## Issues

Global issue list returned 24 open BUG issues for the three Postmaster actions:

- 10 × missing `Text`
- 6 × missing `Authentication method`
- 6 × missing `Data format`
- 2 × `UNEXISTING_DATA_FORMAT_USED`

By action:

- `Gmail Postmaster: Get Domains TrafficStats List`: 9 issues
- `Gmail Postmaster: Get Domain by Domain Name`: 9 issues
- `Gmail Postmaster: Get Domains List`: 6 issues

`UNEXISTING_DATA_FORMAT_USED` references `Google: Service user json` (`[REDACTED_ID]`) as non-existing even though the schema is visible. This is the same stale/internal-reference pattern observed in other NoCode-X Google plugins.

## Capability Assessment

Observed capabilities:

- List Gmail Postmaster domains.
- Get a domain by domain name.
- List traffic stats for a domain.
- Parse key Postmaster telemetry fields such as spam ratio, IP/domain reputation, SPF/DKIM/DMARC success ratios, encryption ratios, feedback loops, and delivery errors.

Not observed:

- Get a single trafficStats resource by exact date/name.
- Pagination parameters / nextPageToken handling actions.
- Date range controls for traffic stats.
- Persistence/storage of daily stats.
- Scheduled sync jobs.
- Alerting for reputation/delivery/spam changes.
- Dashboard/UI templates.
- OAuth user consent flow.
- Dynamic delegated user configuration.
- First-class app API endpoints.

## Verdict

Not empty; useful as a narrow read-only starting scaffold for Postmaster domains and traffic stats. Not production-ready without fixing action configuration, delegated user, pagination/date-range handling, persistence, and scheduled monitoring/alerting.
