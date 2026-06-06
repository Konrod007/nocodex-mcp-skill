# Production B2B/B2C SaaS Template For NoCode-X

Use this reference when planning a production-grade SaaS application in NoCode-X, especially when the app needs user accounts, customer organizations, self-service onboarding, admin portals, billing-aware limits, dashboards, and role-based access.

Keep this template generic. Do not copy private product names, business workflows, customer data, workspace IDs, URLs, credentials, or project-specific implementation details into the shared skill.

## Core Principle

NoCode-X Workspaces are developer/operator infrastructure, not customer-facing tenancy.

For a SaaS product, model customer accounts inside the application:

```text
NoCode-X Workspace
└─ NoCode-X Application
   └─ SaaS tenant model inside app data
      ├─ Organization / Account / Company
      ├─ Memberships
      ├─ Roles / Rights
      ├─ Projects / Workspaces inside the product domain
      ├─ Billing / Plan / Usage
      └─ Product-specific records
```

Do not invite customers into the NoCode-X Workspace unless they are actually part of the development/operator team. Treat Workspace access like infrastructure/admin access.

## Product Modes

### B2C SaaS

Use when one user usually owns their own data.

Typical model:

```text
User
├─ Profile
├─ Personal settings
├─ Subscription / plan
├─ Product records
├─ Usage records
└─ Notifications
```

Useful for:

- solo creator tools;
- personal dashboards;
- lightweight productivity apps;
- individual subscriptions;
- tools where collaboration is optional or later.

### B2B SaaS

Use when a legal entity, team, department, agency, or customer company owns shared data.

Typical model:

```text
Organization / Account / Company
├─ Owner
├─ Admins
├─ Members
├─ Invitations
├─ Roles / Rights
├─ Projects / domain objects
├─ Billing / plan / seats
├─ Usage records
├─ Audit logs
└─ Integrations
```

Useful for:

- agency/client portals;
- internal business tools;
- SEO/marketing platforms;
- analytics/reporting products;
- workflow and approval systems;
- any product where a company admin manages employees.

### Hybrid B2C -> B2B

Start with B2C if the product is mostly personal, but leave room for B2B later:

- create a default Organization for every new user;
- make every product record belong to `organization_id`, not only `user_id`;
- model Membership even if it initially has one member;
- keep roles simple at first: `OWNER`, `ADMIN`, `MEMBER`, `VIEWER`.

This avoids painful migration when adding teams later.

## Core Data Formats

Use these as planning building blocks. Rename them to match the product domain, but keep the responsibilities separate.

### Identity And Tenancy

```text
UserProfile
- user_id
- display_name
- avatar_url
- locale
- timezone
- onboarding_status
- created_at
- updated_at

Organization
- id
- name
- slug
- type: individual | company | agency | internal
- owner_user_id
- plan_id
- billing_customer_id
- status: active | trialing | suspended | cancelled
- created_at
- updated_at

Membership
- id
- organization_id
- user_id
- role_id
- status: active | invited | suspended | removed
- joined_at
- removed_at

Invitation
- id
- organization_id
- email
- role_id
- token_hash
- invited_by_user_id
- status: pending | accepted | revoked | expired
- expires_at
- accepted_at
```

### Authorization

```text
Role
- id
- organization_id optional for custom roles
- key: OWNER | ADMIN | MEMBER | VIEWER | BILLING_ADMIN | SUPPORT
- name
- description

Right
- id
- key: VIEW_PROJECT | EDIT_PROJECT | MANAGE_TEAM | MANAGE_BILLING
- description

RoleRight
- role_id
- right_id
```

Use technical rights for enforcement and roles for human-facing assignment.

### Product Domain

Use product-specific records, always scoped by `organization_id` for B2B-ready apps:

```text
Project / WorkspaceInsideProduct / Client / Site / Campaign
- id
- organization_id
- name
- status
- created_by_user_id
- created_at
- updated_at

ProductItem / Record / Asset / Task / Report
- id
- organization_id
- project_id optional
- owner_user_id optional
- status
- data fields
- created_at
- updated_at
```

### Billing And Usage

```text
Plan
- id
- key
- name
- price_label
- limits_json
- features_json

Subscription
- id
- organization_id
- provider
- provider_customer_id
- provider_subscription_id
- plan_id
- status
- current_period_start
- current_period_end
- cancel_at_period_end

UsageRecord
- id
- organization_id
- metric_key
- quantity
- period_start
- period_end
- source
- created_at

FeatureEntitlement
- id
- plan_id
- feature_key
- enabled
- limit_value optional
```

For production, prefer external billing as source of truth and sync billing status into NoCode-X unless native billing behavior is proven.

### Operations And Audit

```text
AuditLog
- id
- organization_id
- actor_user_id
- action_key
- target_type
- target_id
- metadata_json
- created_at

Notification
- id
- organization_id
- user_id
- type
- title
- body
- read_at
- created_at

SupportTicket / Feedback
- id
- organization_id
- user_id
- subject
- body
- status
- created_at
- updated_at
```

## Essential Screens / Templates

### Public Marketing And Conversion

- Landing page.
- Pricing page.
- Feature pages.
- Use-case pages.
- FAQ.
- Contact / request demo.
- Legal pages: Terms, Privacy, DPA if needed.

### Authentication And Onboarding

- Sign up.
- Login.
- Password reset / account recovery if supported.
- Email verification if supported.
- First-run onboarding checklist.
- Create organization / join invited organization.
- Choose plan or start trial.
- Empty states that explain next actions.

### User Account

- Profile.
- Password/security settings.
- Notifications preferences.
- Connected accounts / integrations.
- Personal API keys if relevant.
- Sessions/devices if supported.

### Organization / Team Area

- Organization switcher.
- Organization settings.
- Members list.
- Invite member.
- Pending invitations.
- Role management.
- Remove/suspend member.
- Transfer ownership.
- Usage and limits.
- Billing settings.

### Product Application Area

- Main dashboard.
- Projects/list view.
- Project detail.
- Create/edit core domain object.
- Activity feed.
- Reports/analytics.
- Review/approval queue.
- Export/download area.
- Integrations setup.
- Error/empty/loading states.

### Admin / Operator Area

- Internal admin dashboard.
- Customer organizations list.
- User lookup.
- Subscription/status overview.
- Recent errors/logs.
- Job/status monitor.
- Support/feedback queue.
- Feature flags / rollout controls.

Keep internal operator tools separate from customer-facing organization admin screens.

## Essential Actions And APIs

### Account Lifecycle

- Create user profile after registration.
- Create default organization for new user.
- Create membership for owner.
- Complete onboarding step.
- Switch active organization.
- Update profile.

### Team Lifecycle

- Invite member.
- Accept invitation.
- Revoke invitation.
- Change member role.
- Suspend/remove member.
- Transfer ownership.
- List organization members.

### Authorization Checks

Centralize checks so templates, actions, and APIs do not each reinvent access logic.

Recommended helper actions:

```text
GetCurrentMembership
AssertOrganizationAccess
AssertRight
AssertProjectAccess
ListAccessibleProjects
```

Every sensitive read/write should derive `organization_id` from the current user membership or validated route context, not from an untrusted client value alone.

### Billing / Entitlements

- Sync subscription state from billing provider.
- Check plan feature enabled.
- Check usage limit before expensive action.
- Increment usage after successful operation.
- Handle failed payment / suspended subscription state.

### Product Workflows

- Create project/domain object.
- Update project settings.
- Run product-specific job.
- Retry failed job/item.
- Export report/data.
- Assign task/review item.
- Mark item approved/resolved/ignored.

## Rights And Roles Starter Set

### Suggested Rights

```text
VIEW_DASHBOARD
VIEW_PROJECT
CREATE_PROJECT
EDIT_PROJECT
DELETE_PROJECT
MANAGE_TEAM
MANAGE_BILLING
MANAGE_INTEGRATIONS
RUN_JOB
CANCEL_JOB
VIEW_REPORTS
EXPORT_DATA
VIEW_AUDIT_LOG
MANAGE_ORGANIZATION_SETTINGS
```

### Suggested Roles

```text
Owner
- all rights

Admin
- manage projects, members, integrations, jobs, reports
- no ownership transfer unless explicitly allowed

Member / Specialist
- work with assigned projects and product records
- run allowed jobs
- view reports

Viewer / Client Viewer
- read-only access to selected dashboards/reports

Billing Admin
- billing and usage screens only, plus basic org visibility

Support / Operator
- internal role for service operator, not customer employee
```

## Production Readiness Blocks

A production SaaS application should intentionally cover these areas:

### Access Control

- Every list is filtered by organization/project access.
- Direct URL access is tested.
- API access is tested separately from UI visibility.
- Removed/suspended users lose access.
- Invitation tokens expire and can be revoked.

### Tenant Isolation

- Every tenant-owned data format has `organization_id`.
- Product records do not rely only on `created_by_user_id`.
- External backend calls include verified organization context.
- Exports cannot include another organization's data.

### Billing And Limits

- Plan features are explicit.
- Usage metrics are recorded.
- Limit checks happen before expensive operations.
- Failed/cancelled subscriptions degrade safely, e.g. read-only access.

### Observability

- Important actions write logs.
- Errors are visible in application logs/issues.
- User-visible failures have friendly messages.
- Admin/operator dashboard exposes recent failures and stuck jobs.

### Data Lifecycle

- Soft delete where recovery or audit matters.
- Ownership transfer before deleting an owner.
- Export path for customer data.
- Retention policy for logs, files, and deleted records.

### Security

- Secret fields for API keys and credentials.
- No secrets in logs, templates, or final messages.
- HTTPS for external calls.
- Sensitive fields classified.
- Negative access tests before production.

## Development Phases

### Phase 1: B2C/B2B-Ready Foundation

- UserProfile.
- Organization.
- Membership.
- Basic roles: Owner/Admin/Member/Viewer.
- Dashboard.
- Project/domain object CRUD.
- Access filters by organization.

### Phase 2: Team Workflow

- Invitations.
- Member management.
- Role changes.
- Project-level access.
- Audit log.
- Notification basics.

### Phase 3: Billing And Limits

- Plans.
- Subscription status.
- Usage records.
- Entitlement checks.
- Billing admin screen.

### Phase 4: Production Operations

- Internal operator dashboard.
- Error/job monitor.
- Data export.
- Support/feedback flow.
- Security review and negative access tests.

### Phase 5: Advanced SaaS Features

- Custom roles.
- SSO for larger customers if supported/proven.
- Domain verification.
- API keys/webhooks per organization.
- Feature flags.
- Advanced reporting.

## Proof-Of-Concept Tests

Before using the template for an important product, build a small app and verify:

1. User A in Organization A cannot see Organization B data through UI list, direct URL, API call, or manipulated action parameter.
2. Organization admin can invite, change role, and remove a member.
3. Removed member loses access immediately.
4. Viewer can read allowed reports but cannot mutate data or run expensive jobs.
5. Generated CRUD APIs do not expose cross-organization data.
6. Billing/plan status can block a feature without deleting customer data.
7. Logs do not leak tokens, passwords, or secret field values.
8. DTAP promotion does not mix production users/data into lower environments.

## NoCode-X Implementation Notes

- Treat generated CRUD as scaffolding; inspect authentication, authorization, pagination, filtering, logging, and error shape before production use.
- Prefer database-level filters, joins, grouping, and aggregations for dashboards.
- Use page-level action parameters deliberately; wrong route or inherited values can cause cross-tenant bugs.
- Use explicit helper actions for access checks instead of scattering role logic across many pages.
- Keep heavy long-running processing in an external durable worker unless NoCode-X Jobs limits/retries/cancellation/logging have been proven for the workload.
- Use NoCode-X as the application control plane, portal, admin UI, review workflow, and dashboard layer when external workers are involved.

## Common Pitfalls

- Treating NoCode-X Workspace as customer tenancy.
- Filtering data in UI only, while APIs/actions can still access cross-tenant records.
- Letting users pass arbitrary `organization_id` without checking membership.
- Creating product records scoped only by `user_id`, then needing team accounts later.
- Building billing screens before defining plan entitlements and usage metrics.
- Deleting owners before ownership transfer.
- Logging secrets from integrations.
- Assuming generated CRUD APIs are production-safe without inspection.

## Quick Planning Checklist

- [ ] Is this B2C, B2B, or hybrid?
- [ ] Is every tenant-owned record scoped by `organization_id`?
- [ ] Are Membership and Role modeled separately?
- [ ] Are rights named as technical permissions?
- [ ] Are customer admins inside the application, not the NoCode-X Workspace?
- [ ] Are direct URL/API negative access tests planned?
- [ ] Is billing source of truth defined?
- [ ] Are usage limits and feature entitlements explicit?
- [ ] Are support/operator screens separate from customer admin screens?
- [ ] Are secrets classified and excluded from logs?
