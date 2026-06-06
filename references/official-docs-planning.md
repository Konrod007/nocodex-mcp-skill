# Official NoCode-X Docs: Planning Notes

This file summarizes official NoCode-X documentation pages that are useful for understanding the platform and planning applications. Source pages were read from `https://docs.nocode-x.com/`. Treat this as official-documentation notes, not as live MCP facts. When applying to a concrete app, verify current workspace/application state through MCP and/or rendered UI.

## Documentation Map

The official sitemap contained 626 URLs when inspected. High-value planning sections include:

- `nocode-x-platform/` — platform navigation, workspaces, applications, developers, users, template editor, action editor.
- `building-concepts/` — UI, logic, jobs, database/data formats, API, design system, media library, groups and rights.
- `publishing/` — versioning and DTAP-style promotion.
- `testing/` — preview/testing by environment.
- `security/` — authentication, authorization, auditability, backup, DTAP, data residency, security score, application security.
- `licenses-&-billing/` — core resources, AppSumo tiers, AI credit billing.
- `how to/interactive manuals/` — implementation tutorials.

## Platform Navigation

Source: `https://docs.nocode-x.com/nocode-x-platform/Platform navigation`

The side navigation exposes major application-building areas:

- UI;
- APIs;
- Database;
- Logic;
- Groups;
- Rights;
- Jobs;
- Design system;
- Media;
- Plugins;
- Users;
- Workspace info;
- Hub;
- Account settings;
- Logout.

Planning implication: when auditing an app, inspect these as separate surfaces. Do not assume a working UI implies APIs, groups, jobs, rights, or logs are correctly configured.

Application-wide tools include:

- application logs;
- audit logs;
- creating and publishing versions;
- previewing one of the four built-in environments.

## Workspaces

Source: `https://docs.nocode-x.com/nocode-x-platform/workspaces`

A workspace is an isolated container. Official docs describe it as a boundary around a project, customer, environment, or regulated domain. A workspace can contain:

- one or many applications;
- any amount of users;
- one or more developers;
- single sign-on settings;
- any amount of cores;
- a private marketplace.

Important official planning point: units/resources are attached to a workspace, not to the overall account.

Use one workspace when:

- building for yourself or one internal team;
- simplest setup is preferred;
- no separate billing or strict isolation is required.

Use multiple workspaces when:

- serving multiple customers requiring clear cost separation;
- different access controls, regions, or compliance settings are needed;
- clean separation is needed for development/staging/production or customer/project boundaries.

Skill rule: start with one workspace unless organizational, billing, isolation, region, or compliance needs justify multiple workspaces.

## Applications

Source: `https://docs.nocode-x.com/nocode-x-platform/applications`

NoCode-X applications can be:

- web applications;
- mobile applications;
- pure APIs;
- automations.

An application belongs to a workspace and contains:

- Templates;
- APIs;
- Actions;
- Jobs;
- Groups;
- Rights;
- Data formats;
- Data;
- Media;
- Design systems;
- Plugins.

Important application attributes:

- Name: unique and recognizable within the workspace.
- Description: short purpose description.
- Icon: visible in the application selector.
- Endpoint: subdomain/domain endpoint for the web application.
- Custom domain.
- Meta title.
- Meta description.
- Home page: the page used for the root URL redirect.
- Favicon.

Planning implication: define endpoint, homepage, metadata, favicon, and custom-domain needs early, not after UI work is complete.

## Developers And Developer Access

Sources:

- `https://docs.nocode-x.com/nocode-x-platform/developers`
- `https://docs.nocode-x.com/building-concepts/groups and rights/manage developer access`

Developers build applications in workspaces. A workspace can have a limited set of developers based on assigned cores, while a developer can have access to multiple workspaces.

Developers with `Manage users` permissions can invite other developers if cores permit. Developer permissions can be granted at application level and workspace level. Developers without any permissions cannot change applications.

Application developer access can be configured for read and create/edit across major features, including:

- Design systems;
- Data formats;
- APIs;
- Actions;
- Dashboards/overview;
- Jobs;
- Data;
- Media;
- Templates;
- Versions.

Workspace permissions mentioned in docs:

- Manage applications;
- Manage workspace information;
- Manage users;
- Manage billing.

Planning implication: for multi-person work, model creator/developer permissions separately from end-user roles. Use coarse-grained application-level access first; fine-grained controls are available but should be used pragmatically to avoid unnecessary complexity.

## Users

Source: `https://docs.nocode-x.com/nocode-x-platform/users`

Users are persons or machines using an application. Users can have rights and/or belong to groups. Users are linked to a workspace and managed through User Management.

User creation fields documented:

- Email: username.
- Password: minimum 8 characters, at least 1 number, at least 1 uppercase letter.
- Confirm Password.
- Temporary Password: ON by default; requires password change at first login.
- Force OTP: OFF by default; requires authenticator-app one-time password setup.
- Force WebAuthn: OFF by default; requires registering a WebAuthn device.
- Firstname.
- Lastname.
- Choose Environment: development, test, acceptance, production.

Deletion warning: deleting a user is destructive, cannot be undone, and revokes memberships, permissions, and rights associated with that user.

## Template Editor And UI

Sources:

- `https://docs.nocode-x.com/nocode-x-platform/Template editor`
- `https://docs.nocode-x.com/building-concepts/ui/`

Template editor concepts:

- Element picker: ready-to-use UI elements.
- Element instance: configured UI element visualized in the application.
- Element instance settings: element settings, style settings, and action triggers.
- UI visualization: preview canvas with pan/zoom.
- Template-specific tools: screen type, zoom, grid, multilingual settings, page hierarchy, authentication/authorization, template settings, UI testing.

Planning implication: UI planning should include template hierarchy, screen types, authentication/authorization on templates, language requirements, and tests.

## Action Editor And Logic

Sources:

- `https://docs.nocode-x.com/nocode-x-platform/Action editor`
- `https://docs.nocode-x.com/building-concepts/logic/`
- `https://docs.nocode-x.com/building-concepts/logic/actions`
- `https://docs.nocode-x.com/building-concepts/logic/action-triggers`
- `https://docs.nocode-x.com/building-concepts/logic/application-logs`
- `https://docs.nocode-x.com/building-concepts/logic/analyzers/`

Action editor concepts:

- Function picker: drag-and-drop predefined functions.
- Function instance: configured function call executed when reached.
- Function instance settings: name, description, icon, tags, parameters, output.
- Start/action settings: action information, action parameters, action output.
- Action logic canvas: execution path visualization.
- Action-specific tools: zoom, automatic block structuring, create/use tests.

Important rule from docs: a function instance not reachable from the start block will never execute and is effectively dead.

Planning implication: action design should define parameters, outputs, logs, tests, and reachable execution paths. During audits, check analyzers/issues and dead/unreachable blocks.

The official sitemap contains analyzer pages for issues such as:

- cyclomatic complexity;
- deprecated method used;
- empty action;
- invalid data-format field reference;
- missing action outputs;
- missing action parameters;
- missing foreach item name;
- missing output;
- missing required field;
- null pointer;
- out-of-scope reference;
- secure data exposed;
- template parameter;
- non-existing action/data-format/template usage;
- unused code;
- WCAG contrast violation.

Planning implication: NoCode-X has a built-in issue/analyzer model. App reviews should inspect Issues, not only runtime logs.

## Data Formats And Database

Sources:

- `https://docs.nocode-x.com/building-concepts/data/`
- `https://docs.nocode-x.com/building-concepts/data/Data formats/`
- `https://docs.nocode-x.com/building-concepts/data/Data formats/Creating data format`
- `https://docs.nocode-x.com/building-concepts/data/Data formats/Creating data format from csv`
- `https://docs.nocode-x.com/building-concepts/data/Data formats/Creating data format from json`
- `https://docs.nocode-x.com/building-concepts/data/Data formats/Generating data format using gen-AI`
- `https://docs.nocode-x.com/building-concepts/data/datatypes/Data classification`

Data formats define the contract for data used in NoCode-X, especially for actions and built-in database storage. If data is stored in the built-in database, it must be valid according to a data format.

Data-format metadata:

- Name;
- Description;
- Tags;
- Icon.

Data-format properties:

- fields/properties with types and specifications;
- required/optional status;
- validations;
- default values;
- dependencies/relationships.

Data-format action triggers:

- After creation of data;
- After update of data;
- After removal of data.

Reserved field keys from official docs:

- `properties`;
- `items`;
- `noCodeXType`.

Do not use these exact names as user-defined field keys because they collide with schema processing and can cause parsing/runtime errors.

Creation methods:

- manual blank data format;
- from CSV via generative AI;
- from JSON;
- from text/business description via generative AI.

CSV import checklist from docs:

- consistent separators;
- properly formatted header row with unique field names;
- all required fields present;
- matching data types;
- no invalid characters;
- escaped special characters;
- consistent date formats;
- correct escape sequences.

JSON import notes from docs:

- JSON must be valid;
- docs mention JSON schema draft-07 compatibility;
- required fields are marked mandatory;
- field types are mapped to NoCode-X types;
- format validations such as email are preserved;
- multiple JSON schemas can create multiple data schemas.

Generative data-format planning:

- Consolidated approach: one nested format with related data inside one object. Easier single-call retrieval but can become large and inefficient for targeted queries.
- Normalized approach: smaller linked formats per entity. More scalable and maintainable, but requires more calls/joins and more complex management.

Planning implication: for operational systems, prefer normalized formats for entities that need filtering, permissions, independent updates, history, or analytics. Use consolidated nested formats for small, naturally embedded data that is rarely queried independently.

## APIs

Sources:

- `https://docs.nocode-x.com/building-concepts/api/`
- `https://docs.nocode-x.com/building-concepts/api/CRUD from Data-format`

APIs enable data exchange, automation, and integration with external services.

Official API creation options include:

- blank API;
- full CRUD from data format;
- full CRUD from text;
- create/read/find/update/delete APIs from data format;
- create/read/find/update/delete APIs from text.

CRUD from data format creates:

- read single item;
- read list of items;
- create single item;
- update single item;
- delete single item.

Docs frame CRUD generation as useful for rapid deployment, sharing information, bootstrapping web applications, creating data lakes, and keeping separation between data and processing layers.

Planning implication: define data formats first when APIs are needed. Generate CRUD APIs as scaffolding, then inspect security, authorization, validation, logging, and naming before production use.

## Jobs

Source: `https://docs.nocode-x.com/building-concepts/jobs/`

Jobs execute logic periodically. Job fields:

- Name;
- Description;
- Icon;
- Tags;
- Frequency;
- Execution: one or more actions to execute periodically.

Documented frequency options include:

- Paused;
- Advanced cron;
- Every 5 minutes;
- Every 10 minutes;
- Every 30 minutes;
- Every hour;
- Every 2 hours;
- Every 6 hours;
- Every 12 hours;
- Every day;
- Every day at 6:00;
- Every day at 12:00;
- Every day at 0:00;
- Every month;
- Every first/tenth/twentieth/last day of the month;
- Every first day of the year;
- Every sixth month of the year.

Advanced cron uses six fields:

```text
second minute hour day-of-month month day-of-week
```

Planning implication: design job actions as independently testable units, then attach them to schedules. Use `Paused` while building. Avoid overlapping or high-frequency jobs until duration and idempotency are known.

## Groups, Rights, Authorization

Sources:

- `https://docs.nocode-x.com/building-concepts/groups and rights/groups and rights how to`
- `https://docs.nocode-x.com/security/Authorization`

Rights are technical privileges. Each right should have:

- Name;
- Description.

Roles/groups represent functional responsibilities and are used to assign service or application responsibilities to users. Rights are linked to roles/groups.

Official planning approach:

1. Define functional roles.
2. Define technical privileges needed for those roles.
3. Create rights.
4. Create roles/groups and assign rights.

Authorization principles from docs:

- least privilege;
- need to know;
- no access by default when a group is defined on a resource;
- fine-grained access control by design.

Planning implication: model roles and rights before building sensitive templates/APIs/actions. Test negative cases: unauthenticated, wrong group, missing right, wrong environment.

## Publishing, Versioning, Environments

Sources:

- `https://docs.nocode-x.com/publishing/`
- `https://docs.nocode-x.com/testing/`
- `https://docs.nocode-x.com/security/DTAP`

Versions are specific iterations/releases of an application. Created versions can be used to:

- promote to one or more environments;
- publish on the Hub.

NoCode-X has four environments:

- Development: latest application under active development; every change is reflected immediately.
- Test: version moved beyond development for development-team testing; not accessible to real users.
- Acceptance: business/stakeholder testing; not yet accessible to the general user base.
- Production: live version accessible to end users.

Creating a version:

- click Publish;
- click Add version;
- choose name and describe changes;
- NoCode-X creates an optimized version, which may take time depending on app size;
- promote the version to Test, Acceptance, and/or Production.

Environment color indicators in docs:

- Green: production;
- Orange: acceptance;
- Yellow: test;
- Gray: not deployed anywhere.

Testing docs: the Play button opens the home page of the application in Development, Test, Acceptance, or Production. It is advisable to configure a home page.

DTAP docs add:

- changes flow Development → Test → Acceptance → Production;
- lower-environment data/config should not be promoted unless explicitly required;
- sensitive production data should not be reused in lower environments;
- versioning supports roll forward and roll backward;
- synthetic test data can be generated according to data formats and business context.

Planning implication: define home page and test data early. Treat version creation/promotion as a deployment step, not just a UI action.

## Security, Auditability, Backup, Data Residency

Sources:

- `https://docs.nocode-x.com/security/Securing your application`
- `https://docs.nocode-x.com/security/Authentication`
- `https://docs.nocode-x.com/security/Authorization`
- `https://docs.nocode-x.com/security/Auditability`
- `https://docs.nocode-x.com/security/Backup`
- `https://docs.nocode-x.com/security/Data Residency`
- `https://docs.nocode-x.com/security/Security score`

Application security checklist from docs:

- configure authentication via embedded identity provider or SSO;
- define functional roles and fine-grained authorization;
- classify sensitive data at attribute level;
- enable/implement logging for create/update/delete and sensitive reads;
- use write-audit-log components in actions where needed;
- enable AI guardrails when embedding AI;
- monitor creator dashboard for detections such as unauthenticated exposure of sensitive information;
- use DTAP pipelines.

Authentication notes:

- supported authentication factors are knowledge, property, and inherence;
- SSO supports OpenID Connect 1.0 and OAuth 2.0;
- with external SSO, the identity provider becomes responsible for authentication strength and credential lifecycle;
- break-the-glass accounts are special emergency accounts with additional property factors and monitored usage;
- docs advise against biometric/inherence factors in centralized systems due to GDPR concerns.

Auditability notes:

- updates, deletions, and creations are logged by default;
- when a sensitive data label is assigned, read access is also logged;
- logs are retained for up to one year according to the docs;
- logging is consistent across APIs and templates;
- developer logging component supports scope, placeholders, and severity levels.

Backup notes:

- backups are taken twice daily at 00:00 and 12:00 CET;
- this gives a documented RPO of 12 hours;
- backups are out-of-band and isolated from runtime;
- self-hosted backup frequency/configuration can be customized with Helm charts.

Data residency notes:

- NoCode-X is operated by Co-Dex.eu BV, a Belgian legal entity;
- docs state processing/storage is restricted to Belgium and France for the managed service;
- GDPR and European legal framework are emphasized;
- self-hosting options exist for stricter residency requirements.

Security score notes:

- docs claim external validation, a 98% Security Scorecard score, and 100% Internet.nl compliance at the time of the page.
- Treat these as docs claims and verify current status before contractual or compliance use.

Planning implication: for serious apps, include authentication method, groups/rights, data classification, audit logs, backup/RPO expectations, environment policy, and AI guardrails in the project plan.

## Licensing, Cores, AI Credits

Sources:

- `https://docs.nocode-x.com/licenses-&-billing/AppSumo deals`
- `https://docs.nocode-x.com/licenses-&-billing/Understanding AI Credits and Billing`

Core resources include:

- CPU minutes;
- storage;
- bandwidth;
- developers.

Docs emphasize:

- no user-based pricing for end users;
- resources are bundled as cores;
- AppSumo resources are fixed by tier;
- extra resources can be purchased beyond AppSumo limits;
- AI credits use `1 AI Credit = $0.001` base cost;
- managed-account AI usage has a 25% service fee;
- users can bring their own API keys or use managed pricing and switch between them.

Planning implication: high-frequency jobs, heavy AI usage, file storage, media, and bandwidth-heavy apps need resource budgets before production.

## Self-Hosted

Source: `https://docs.nocode-x.com/when-to-choose-nocode-x/Self hosted`

Self-hosted NoCode-X is described for organizations needing compliance, full control, data sovereignty, or cyber resilience.

Responsibilities transferred to the hosting party include:

- maintaining Kubernetes or Docker infrastructure;
- keeping NoCode-X updated;
- managing CDN/WAF;
- certificate management;
- identity and access management;
- backup capabilities;
- restore processes and restore tests.

Deployment notes:

- Kubernetes is preferred via Helm chart;
- Docker is possible but may require more setup;
- minimum hardware listed: 16 GB RAM, 8 vCPU, 50 GB primary storage, 50 GB+ backup storage;
- larger system example: 46 GB RAM, 12 vCPU, 100 GB primary storage, 100 GB+ backup storage;
- requires SSL/TLS certificates and proxy/firewall access to public NoCode-X endpoint for updates and Hub access.

Planning implication: self-hosting is not just a deployment option; it shifts operational responsibility to the customer. Include patching, backups, restore tests, WAF/CDN, certificates, and update windows in the plan.

## Gaps / Questions To Verify With NoCode-X Developers

The official docs add many concepts but still leave questions important for production planning:

- Are user creation/deletion/update operations available through API or MCP?
- Is there a safe user deactivation flow separate from irreversible deletion?
- What happens to business records owned/created by a deleted user?
- Which resources exactly support group/right assignment: templates, APIs, data formats, actions, jobs, fields?
- How are rights enforced on actions triggered indirectly by templates, jobs, APIs, or data triggers?
- What is the exact retention policy and export mechanism for application logs and audit logs?
- Can audit logs be queried/exported through API or MCP?
- What are practical limits for jobs: maximum runtime, overlap behavior, retries, concurrency, failure history, and cancellation?
- What are practical limits for generated CRUD APIs and advanced database queries?
- How do generated APIs handle authentication, authorization, validation, pagination, and error formats by default?
- What fields/types/validations are supported by data formats beyond the examples?
- What is the exact data-classification behavior at runtime, including read logging and UI/API enforcement?
- What operations are included in version snapshots and what is excluded by environment-boundary rules?
- How are secrets, API keys, and AI provider keys stored, rotated, and prevented from appearing in logs?
- Which MCP tools can inspect or mutate users, groups, rights, environments, logs, versions, and generated APIs?
