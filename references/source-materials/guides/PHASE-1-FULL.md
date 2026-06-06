# Phase 1: Production-Ready Essentials

## Jobs: Scheduled Automation

Jobs enable periodic execution of logic - essential for background tasks, reports, data cleanup, and automated workflows.

### Creating a Job

**Navigation:** Side navigation → Job overview → Create button

**Configuration:**
```
Job Settings:
├─ Name: Job identifier
├─ Description: Purpose/overview
├─ Icon: Visual recognition
├─ Tags: Organization
├─ Frequency: Execution schedule
└─ Execution: Action(s) to run
```

### Frequency Options

| Frequency | Description |
|-----------|-------------|
| **Paused** | Job will not run |
| **Advanced** | Custom cron expression |
| **Every 5 minutes** | High-frequency automation |
| **Every 10 minutes** | Regular polling/tasks |
| **Every 30 minutes** | Medium-frequency jobs |
| **Every hour** | Hourly tasks |
| **Every 2 hours** | Bi-hourly processes |
| **Every 6 hours** | Quarter-day tasks |
| **Every 12 hours** | Half-day processes |
| **Every day** | Daily (first 5 minutes of day) |
| **Every day at 6:00** | Morning routine |
| **Every day at 12:00** | Midday process |
| **Every day at 0:00** | Midnight tasks |
| **Every month** | Monthly (first 5 minutes) |
| **Every first day** | Start of month |
| **Every tenth day** | Mid-month process |
| **Every twentieth day** | End-of-month prep |
| **Every last day** | Month-end tasks |
| **Every first day of year** | Annual process |
| **Every six months** | Bi-annual tasks |

### Cron Expressions (Advanced)

**6-Field Format:** `second minute hour day-of-month month day-of-week`

**Field Values:**
```
Field          Allowed Values    Special Characters
─────────────────────────────────────────────────────
Second         0-59              , - * /
Minute         0-59              , - * /
Hour           0-23              , - * /
Day of Month   1-31              , - * ? / L W
Month          1-12/JAN-DEC      , - * /
Day of Week    0-6/SUN-SAT       , - * ? / L #
```

**Examples:**
```
Every 15 seconds:       */15 * * * * *
Every minute:           0 * * * * *
Every hour at 30 min:   0 30 * * * *
Daily at 2:30 AM:       0 30 2 * * *
Weekly on Monday:       0 0 9 * * 1
Monthly on 1st:         0 0 0 1 * *
```

### Common Job Patterns

**Pattern: Daily Report Generation:**
```
Frequency: Every day at 6:00
Action: Generate Daily Report
├─ Fetch yesterday's data
├─ Calculate metrics
├─ Generate PDF/report
└─ Email to stakeholders
```

**Pattern: Data Cleanup:**
```
Frequency: Every day at 0:00
Action: Cleanup Old Data
├─ Find records older than 90 days
├─ Archive to storage
└─ Delete from active DB
```

**Pattern: API Polling:**
```
Frequency: Every 5 minutes
Action: Sync External Data
├─ Call external API
├─ Process new data
└─ Update local records
```

**Pattern: Expiration Checks:**
```
Frequency: Every hour
Action: Check Expirations
├─ Find expired subscriptions
├─ Update account status
└─ Send renewal reminders
```

### Best Practices

**Job Design:**
```
✅ DO:
├─ Keep jobs focused (single responsibility)
├─ Add logging for monitoring
├─ Handle errors gracefully
├─ Set appropriate frequency
└─ Document job purpose

❌ DON'T:
├─ Create overlapping jobs (race conditions)
├─ Set too frequent intervals (resource waste)
├─ Skip error handling
└─ Leave jobs paused without reason
```

**Error Handling:**
```
Action: Job with Error Handling

1. Try block logic
2. On error → Write to application log
3. On error → Send notification
4. Continue or halt based on severity
```

**Monitoring:**
```
Critical Jobs:
├─ Check application logs regularly
├─ Set up alerts for failures
├─ Monitor execution duration
└─ Review success rates
```

### Quick Jobs Checklist

**Setup:**
- [ ] Define job name and description
- [ ] Choose appropriate icon
- [ ] Select execution frequency
- [ ] Link to action(s)

**Configuration:**
- [ ] Test action independently first
- [ ] Set up error handling
- [ ] Configure logging
- [ ] Document the job

**Monitoring:**
- [ ] Check Application Logs
- [ ] Monitor execution times
- [ ] Set up failure alerts
- [ ] Review periodically

---

## Groups & Rights: Access Control (RBAC)

Role-Based Access Control (RBAC) ensures users have appropriate permissions for their responsibilities.

### Core Concepts

**Rights (Technical Privileges):**
```
Definition: What actions users can perform
Examples:
├─ SEARCH_PRODUCTS
├─ CREATE_ORDER
├─ MANAGE_USERS
└─ VIEW_REPORTS
```

**Roles (Functional Responsibilities):**
```
Definition: What services users can access
Examples:
├─ Customer
├─ Manager
├─ Admin
└─ Accountant
```

**Relationship:**
```
Roles → Contain → Rights
Users → Assigned → Roles
```

### Creating Rights

**Navigation:** Ribbon → "Create Rights"

**Structure:**
```
Right Definition:
├─ Name: Clear identifier (e.g., "CREATE_ORDER")
├─ Description: What it allows
└─ Assignment: Templates, API endpoints

Example:
Name: SEARCH_PRODUCTS
Description: "Allows user to search and view products"
Assigned to: ProductSearch.template, ProductList.api
```

### Creating Roles

**Navigation:** Alt + G → Groups

**Structure:**
```
Role Definition:
├─ Name: Functional role name
├─ Description: Responsibilities
└─ Rights: Drag and drop assigned rights

Example:
Name: Customer
Description: "Can browse products and place orders"
Rights: SEARCH_PRODUCTS, CREATE_ORDER, TRACK_ORDER
```

### Example: E-commerce Application

**Step 1: Define Functional Roles:**
```
Customer:
├─ Browse products
├─ Make purchases
└─ Track orders

Webshop Manager:
├─ Manage products
├─ Process orders
└─ View reports

Accountant:
├─ Monitor payments
└─ Generate financial reports
```

**Step 2: Define Technical Rights:**
```
Customer Rights:
├─ SEARCH_PRODUCTS
├─ CREATE_ORDER
└─ TRACK_ORDER

Manager Rights:
├─ MANAGE_PRODUCTS
├─ PROCESS_ORDERS
└─ VIEW_REPORTS

Accountant Rights:
├─ MONITOR_PAYMENTS
└─ GENERATE_REPORTS
```

**Step 3: Create Role-Right Mapping:**
```
Role: Customer
├─ SEARCH_PRODUCTS → ProductSearch.template, ProductList.api
├─ CREATE_ORDER → Checkout.template, OrderProcessing.api
└─ TRACK_ORDER → OrderTracking.template, OrderHistory.api

Role: Manager
├─ MANAGE_PRODUCTS → ProductManagement.template
├─ PROCESS_ORDERS → OrderProcessing.template, OrderManagement.api
└─ VIEW_REPORTS → AdminDashboard.api

Role: Accountant
├─ MONITOR_PAYMENTS → PaymentGateway.api
└─ GENERATE_REPORTS → Reporting.template, FinancialReports.api
```

### Implementation Steps

**Step 1: Functional Analysis:**
```
Identify personas:
├─ Who uses the app?
├─ What do they need to do?
└─ What should they NOT access?
```

**Step 2: Create Rights:**
```
For each functionality:
├─ Create technical right
├─ Add clear description
└─ Note where it's assigned
```

**Step 3: Create Roles:**
```
Group rights by persona:
├─ Create role
├─ Add description
├─ Drag rights to role
└─ Review completeness
```

**Step 4: Assign to Users:**
```
User management:
├─ Create user accounts
├─ Assign appropriate role(s)
└─ Test access boundaries
```

### User Stories Approach

**Format:** "As a [role], I want to [action], so that [benefit]"

**Examples:**
```
Customer:
├─ "As a Customer, I want to search products,
│   so that I can find items to purchase"
├─ "As a Customer, I want to create orders,
│   so that I can buy products easily"
└─ "As a Customer, I want to track orders,
    so that I know when they arrive"

Manager:
├─ "As a Manager, I want to manage products,
│   so that I can keep inventory updated"
├─ "As a Manager, I want to process orders,
│   so that customers receive timely delivery"
└─ "As a Manager, I want to view reports,
    so that I can analyze sales performance"
```

### Best Practices

**Security Principles:**
```
✅ DO:
├─ Principle of least privilege
├─ Regular access reviews
├─ Clear role descriptions
├─ Separation of duties
└─ Document all permissions

❌ DON'T:
├─ Give admin rights unnecessarily
├─ Create overlapping roles
├─ Skip user story phase
└─ Forget to test access
```

**Naming Conventions:**
```
Rights: VERB_NOUN format
├─ CREATE_ORDER (not "order creation")
├─ DELETE_USER (not "user deletion")
└─ VIEW_REPORTS (not "report viewing")

Roles: Functional titles
├─ Customer (not "User Type 1")
├─ SalesManager (not "Manager Role")
└─ SystemAdmin (not "Admin")
```

### Quick RBAC Checklist

**Planning:**
- [ ] Identify all user personas
- [ ] Document user stories
- [ ] Define access boundaries
- [ ] Map functions to rights

**Implementation:**
- [ ] Create all rights
- [ ] Create all roles
- [ ] Assign rights to roles
- [ ] Assign roles to users
- [ ] Test each role's access

**Review:**
- [ ] Verify least privilege
- [ ] Check for role overlap
- [ ] Test edge cases
- [ ] Document the system
- [ ] Schedule access reviews

---

## Security: Building Secure Applications

NoCode-X embeds enterprise-grade security by design and by default.

### Security Pillars

**Authentication:**
```
Features:
├─ Identity management
├─ Single Sign-On (SSO)
├─ Multi-factor authentication (MFA)
└─ Session management
```

**Authorization:**
```
Features:
├─ Group-based permissions
├─ Role-based access control
├─ Resource-level security
└─ Action-level permissions
```

**Auditability:**
```
Features:
├─ Comprehensive logging
├─ Action tracking
├─ User activity history
└─ Compliance reporting
```

**Data Protection:**
```
Features:
├─ EU data residency
├─ Encryption at rest
├─ Encryption in transit
└─ Backup & recovery
```

### OWASP TOP 10 Compliance

NoCode-X addresses critical security vulnerabilities:

| Vulnerability | Protection |
|---------------|------------|
| **Injection** | Parameterized queries, input validation |
| **Broken Auth** | Secure session management, MFA |
| **Sensitive Data** | Encryption, secure storage |
| **XXE** | Secure XML parsing |
| **Access Control** | RBAC, least privilege |
| **Security Misconfig** | Secure defaults, hardening |
| **XSS** | Output encoding, CSP |
| **Insecure Deserialization** | Safe parsing |
| **Vulnerable Components** | Supply chain security |
| **Insufficient Logging** | Comprehensive audit logs |

### Security Score

**Real-time security monitoring:**
```
Score Components:
├─ Authentication configuration
├─ Authorization setup
├─ Data protection measures
├─ API security
└─ Application settings

Actionable recommendations based on score
```

### DTAP Environment Security

**4-Stage Security Pipeline:**
```
Development → Test → Acceptance → Production

Security increases at each stage:
├─ Dev: Flexible for development
├─ Test: Isolated testing
├─ Acceptance: Production-like security
└─ Production: Full security controls
```

### Application Security Best Practices

**Template Security:**
```
✅ DO:
├─ Enable auth on sensitive pages
├─ Validate all inputs
├─ Use HTTPS only
├─ Set security headers
└─ Review access permissions

❌ DON'T:
├─ Expose admin panels publicly
├─ Skip input validation
├─ Hardcode secrets
└─ Ignore security warnings
```

**API Security:**
```
✅ DO:
├─ Require authentication
├─ Implement rate limiting
├─ Validate all parameters
├─ Log access attempts
└─ Use API keys securely

❌ DON'T:
├─ Allow open endpoints
├─ Expose sensitive data
├─ Skip error handling
└─ Log sensitive info
```

**Data Security:**
```
✅ DO:
├─ Classify data sensitivity
├─ Encrypt sensitive fields
├─ Implement backup strategy
├─ Test recovery procedures
└─ Monitor access patterns

❌ DON'T:
├─ Store passwords in plain text
├─ Share production data
├─ Skip data retention policies
└─ Ignore data residency
```

### Zero-Data Principle

**What it means:**
```
Your data is always yours:
├─ Full data ownership
├─ Easy export anytime
├─ No vendor lock-in
├─ Escrow protection
└─ Compliance ready
```

**Benefits:**
```
Business Continuity:
├─ Export data anytime
├─ Application export available
├─ Self-hosting options
└─ Escrow clause protection
```

### Incident Response

**Preparedness:**
```
Security Events:
├─ Detection mechanisms
├─ Response procedures
├─ Communication plans
└─ Recovery protocols
```

**Your Role:**
```
Responsibilities:
├─ Report suspicious activity
├─ Follow security policies
├─ Keep credentials secure
└─ Participate in reviews
```

### Quick Security Checklist

**Setup:**
- [ ] Enable authentication on all sensitive pages
- [ ] Configure proper authorization (RBAC)
- [ ] Set up MFA for admin accounts
- [ ] Enable audit logging
- [ ] Configure data residency

**Development:**
- [ ] Validate all user inputs
- [ ] Use HTTPS everywhere
- [ ] Implement error handling
- [ ] Review Security Score
- [ ] Test access controls

**Production:**
- [ ] Regular access reviews
- [ ] Monitor audit logs
- [ ] Test backup recovery
- [ ] Keep plugins updated
- [ ] Review security alerts

---

## Publishing & Versioning: DTAP Pipeline

NoCode-X provides built-in DTAP (Development, Test, Acceptance, Production) street for version management.

### Understanding Versions

**Version Definition:**
```
A version = Specific iteration of your application
├─ Identified by version number (1.0, 2.1.3)
├─ Reflects state at specific point in time
├─ Includes all optimizations for production
└─ Immutable once created
```

**Version Uses:**
```
1. Promote to environments (DTAP)
2. Publish on Hub (plugins)
3. Rollback if needed
4. Track changes over time
```

### DTAP Environments

**Four-Stage Pipeline:**

| Environment | Purpose | Who Uses It |
|-------------|---------|-------------|
| **Development** | Active development | Developers |
| **Test** | QA & testing | Testers, developers |
| **Acceptance** | Business validation | Stakeholders, users |
| **Production** | Live application | End users |

**Flow:**
```
Development → Test → Acceptance → Production
     ↑______________________________|
              (feedback loop)
```

### Environment Details

**Development:**
```
Purpose: Latest changes, active work
Characteristics:
├─ Immediate reflection of changes
├─ Primary environment for developers
├─ May be unstable
└─ Frequent updates
```

**Test:**
```
Purpose: Quality assurance
Characteristics:
├─ Stable version for testing
├─ Not accessible to end users
├─ QA team validation
└─ Bug fixing before acceptance
```

**Acceptance:**
```
Purpose: Business validation
Characteristics:
├─ Production-like environment
├─ Stakeholder testing
├─ User acceptance testing (UAT)
└─ Final approval before production
```

**Production:**
```
Purpose: Live application
Characteristics:
├─ Accessible to all end users
├─ Optimized for performance
├─ Maximum stability required
└─ Carefully controlled updates
```

### Creating a Version

**Steps:**
```
1. Click "Publish" (top right)
2. Click "Add version"
3. Enter:
   ├─ Version name (e.g., "v1.2.0")
   └─ Description (changes in this version)
4. Click "Save"
5. Wait for optimization (may take time)
```

**What Happens:**
```
Version Creation Process:
├─ Application is optimized
├─ Production-ready build created
├─ Assets compressed
├─ Code minified
└─ Performance optimizations applied
```

### Promoting Versions

**Promotion Options:**
```
After version creation:
├─ Promote to Test
├─ Promote to Acceptance
├─ Promote to Production
└─ Multiple environments simultaneously
```

**Color Coding:**
```
Version Indicators:
├─ 🟢 Green → Production
├─ 🟠 Orange → Acceptance
├─ 🟡 Yellow → Test
└─ ⬜ Gray → Not deployed
```

### Best Practices

**Version Naming:**
```
Semantic Versioning (recommended):
MAJOR.MINOR.PATCH

Examples:
├─ 1.0.0 → Initial release
├─ 1.1.0 → New features
├─ 1.1.1 → Bug fixes
└─ 2.0.0 → Breaking changes
```

**Release Process:**
```
✅ DO:
├─ Test thoroughly in lower environments
├─ Document changes in version description
├─ Promote sequentially (Dev → Test → Accept → Prod)
├─ Have rollback plan
└─ Communicate with stakeholders

❌ DON'T:
├─ Skip testing environments
├─ Deploy directly to production
├─ Deploy during peak hours
├─ Forget to backup before major updates
└─ Ignore failing tests
```

**Environment Management:**
```
Development: Always latest
Test: After feature completion
Acceptance: Before release
Production: Only stable, tested versions
```

### Hub Publishing

**Making Apps Public:**
```
Versions can be:
├─ Published on Hub (public plugins)
├─ Kept private (internal use)
└─ Distributed to specific workspaces
```

**Plugin Creation:**
```
Your app → Plugin → Hub
├─ Reusable blueprints
├─ Share with community
└─ Monetization options
```

### Quick Publishing Checklist

**Before Creating Version:**
- [ ] All features tested
- [ ] Bugs fixed
- [ ] Documentation updated
- [ ] Security review passed

**Version Creation:**
- [ ] Click "Publish"
- [ ] Click "Add version"
- [ ] Name version (semantic)
- [ ] Describe changes
- [ ] Wait for optimization

**Deployment:**
- [ ] Deploy to Test first
- [ ] Run test suite
- [ ] Deploy to Acceptance
- [ ] Get stakeholder approval
- [ ] Deploy to Production
- [ ] Monitor for issues

**Post-Deployment:**
- [ ] Verify production functionality
- [ ] Monitor performance
- [ ] Check error logs
- [ ] Gather user feedback

---

