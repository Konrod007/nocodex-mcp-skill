# Phase 2: Important Additions

## Design System: Visual Consistency

The Design System enables centralized creation and management of your application's visual style. Changes propagate uniformly across all UI elements.

### Overview

**Benefits:**
```
✅ Single source of truth for visual style
✅ Changes apply globally, no manual updates
✅ Consistent user experience
✅ Faster development with predefined tokens
✅ Easy theme switching (Dark/Light mode)
```

**Architecture:**
```
Application
└── Design System (one active at a time)
    ├── Colors (palette tokens)
    ├── Typography (font families, sizes)
    ├── Spacing (margins, padding scale)
    └── Components (shared UI elements)
```

### Colors

**Setting Up Color Palette:**
```
Design System → Colors → Add Color

Each color defines:
├─ Name: Semantic name (e.g., "Primary", "Error", "Background")
├─ Value: HEX code or color picker
└─ Usage: Where to apply
```

**Recommended Color Structure:**
```
Brand Colors:
├─ Primary: Main brand color
├─ Primary Light: Hover states
├─ Primary Dark: Active states
└─ Secondary: Accent color

Semantic Colors:
├─ Success: #22C55E (green)
├─ Warning: #F59E0B (amber)
├─ Error: #EF4444 (red)
└─ Info: #3B82F6 (blue)

Neutral Colors:
├─ Background: Page background
├─ Surface: Cards, panels
├─ Text Primary: Main text
├─ Text Secondary: Muted text
└─ Border: Dividers, outlines
```

**Using Colors in UI:**
```
Element → Style → Color
└── Shows Design System colors in picker

Example:
Button background → Primary
Error message → Error
Card background → Surface
```

### Typography

**Typography Tokens:**
```
Design System → Typography

Settings:
├─ Font Family: Primary font (e.g., Inter, Roboto)
├─ Scale: Size progression ratio
└─ Weights: Available font weights
```

**Text Styles:**
```
Predefined styles:
├─ Display Large: Hero headings
├─ Display Medium: Page titles
├─ Display Small: Section headers
├─ Headline Large: Major sections
├─ Headline Medium: Subsections
├─ Headline Small: Card titles
├─ Title Large: List headers
├─ Title Medium: Item titles
├─ Title Small: Labels
├─ Body Large: Primary content
├─ Body Medium: Secondary content
├─ Body Small: Captions, metadata
└─ Label styles: Buttons, inputs
```

**Applying Typography:**
```
Text Element → Style → Typography
└── Select predefined style

Benefits:
├─ Consistent hierarchy
├─ Easy global changes
└─ Responsive by default
```

### Dark vs Light Mode

**Mode Configuration:**
```
Design System supports:
├─ Light Mode (default)
├─ Dark Mode
└─ Auto (follows system preference)

Each mode has separate color values for same tokens
```

**Token Strategy:**
```
Semantic tokens work in both modes:

Token: "Background"
├─ Light: #FFFFFF (white)
└─ Dark: #1A1A1A (dark gray)

Token: "Text Primary"
├─ Light: #1A1A1A (near black)
└─ Dark: #FFFFFF (white)
```

**Implementation:**
```
1. Define semantic color tokens
2. Set values for Light mode
3. Set values for Dark mode
4. Use tokens consistently
5. Mode switching is automatic
```

### Best Practices

**Design System Creation:**
```
✅ DO:
├─ Start with brand guidelines
├─ Use semantic naming (not "Blue" but "Primary")
├─ Test accessibility (contrast ratios)
├─ Include all necessary states
├─ Document usage patterns
└─ Test both Light and Dark modes

❌ DON'T:
├─ Use too many colors (max 8-10)
├─ Skip Dark mode preparation
├─ Use arbitrary values in UI
├─ Ignore mobile typography sizes
└─ Forget hover/focus states
```

**Token Naming:**
```
✅ GOOD (Semantic):
├─ Primary, Secondary
├─ Success, Error, Warning
├─ Background, Surface
└─ Text Primary, Text Secondary

❌ BAD (Literal):
├─ Blue, Red, Green
├─ Light Gray, Dark Gray
└─ Big Text, Small Text
```

### Quick Design System Checklist

**Setup:**
- [ ] Define brand colors (primary, secondary)
- [ ] Create semantic color tokens
- [ ] Set up typography scale
- [ ] Configure Light mode colors
- [ ] Configure Dark mode colors
- [ ] Test contrast ratios (accessibility)

**Application:**
- [ ] Apply colors through Design System picker
- [ ] Use typography tokens consistently
- [ ] Test in both Light and Dark modes
- [ ] Verify on mobile devices
- [ ] Document custom patterns

**Maintenance:**
- [ ] Review periodically
- [ ] Update as brand evolves
- [ ] Get team feedback
- [ ] Maintain consistency

---

## Hub: Plugins & Integrations

The Hub contains pre-built plugins that accelerate development by providing reusable blueprints.

### What is a Plugin?

**Definition:**
```
Plugin = Blueprint for Building Concepts

Contains:
├─ Templates (UI components)
├─ Actions (logic flows)
├─ API definitions
└─ Data formats

Key insight: Plugins are built WITH NoCode-X
→ You can modify any installed plugin
→ Never locked into plugin limitations
```

**Plugin Types:**
```
Public Hub:
├─ Community-created plugins
├─ Official NoCode-X plugins
└─ Free and paid options

Private Hub:
├─ Organization-specific
├─ Internal tools
└─ Proprietary solutions
```

### Installing Plugins

**Navigation:**
```
Side navigation → Hub

Process:
1. Browse or search plugins
2. Click plugin name for details
3. Review README/documentation
4. Click "Install"
5. Select version (usually latest)
```

**After Installation:**
```
View installed plugins:
Side navigation → Plugins

Installed plugins appear in:
├─ Template picker
├─ Action library
├─ Component lists
└─ Can be customized immediately
```

### Using Plugins

**Templates from Plugins:**
```
Create Template → Select from plugin
├─ Pre-built page layouts
├─ Component libraries
└─ Complete page patterns
```

**Actions from Plugins:**
```
Create Action → Plugin actions
├─ Pre-built logic flows
├─ Integration patterns
└─ Utility functions
```

**Common Plugin Categories:**
```
UI Components:
├─ Navigation bars
├─ Form libraries
├─ Data tables
└─ Charts and graphs

Integrations:
├─ Email services (Mailgun, SendGrid)
├─ Payment processors (Stripe, Mollie)
├─ AI services (OpenAI, Gemini)
└─ Storage (AWS S3, Google Cloud)

Utilities:
├─ Date/time handlers
├─ String manipulators
├─ Data validators
└─ File processors
```

### Creating Plugins

**When to Create:**
```
✅ Create plugin when:
├─ Pattern repeats across projects
├─ Sharing with team/organization
├─ Publishing to community
└─ Complex reusable functionality
```

**Plugin Development:**
```
1. Build functionality in app
2. Test thoroughly
3. Export as plugin
4. Add documentation (README)
5. Publish to Hub (public/private)
```

**Plugin Structure:**
```
Plugin Package:
├─ Templates/
│   └─ Reusable UI components
├─ Actions/
│   └─ Logic flows
├─ APIs/
│   └─ Endpoint definitions
├─ Data/
│   └─ Data formats
└─ README.md
   └─ Usage instructions
```

### Private vs Public Hub

**Private Hub:**
```
Use for:
├─ Internal company tools
├─ Proprietary integrations
├─ Team-specific patterns
└─ Client-specific solutions

Benefits:
├─ Control access
├─ Internal IP protection
├─ Team collaboration
└─ Version control
```

**Public Hub:**
```
Use for:
├─ Community contributions
├─ Monetization
├─ Open source patterns
└─ Ecosystem building

Benefits:
├─ Reach wider audience
├─ Community feedback
├─ Recognition
└─ Revenue potential
```

### Best Practices

**Plugin Selection:**
```
✅ DO:
├─ Check plugin ratings/reviews
├─ Review documentation
├─ Test in development first
├─ Check update frequency
└─ Verify compatibility

❌ DON'T:
├─ Install unnecessary plugins
├─ Use unmaintained plugins
├─ Skip security review
└─ Ignore version updates
```

**Plugin Usage:**
```
✅ DO:
├─ Customize to fit your needs
├─ Understand how it works
├─ Keep plugins updated
├─ Document customizations
└─ Give feedback to creators

❌ DON'T:
├─ Treat as black box
├─ Modify without understanding
├─ Skip testing after updates
└─ Forget to credit creators
```

### Quick Hub Checklist

**Finding Plugins:**
- [ ] Identify needed functionality
- [ ] Search Hub for existing solutions
- [ ] Review plugin documentation
- [ ] Check ratings and reviews
- [ ] Verify last update date

**Installation:**
- [ ] Install in development first
- [ ] Test thoroughly
- [ ] Review all components
- [ ] Customize as needed
- [ ] Document modifications

**Maintenance:**
- [ ] Monitor for updates
- [ ] Test updates in dev
- [ ] Update production carefully
- [ ] Remove unused plugins
- [ ] Contribute improvements back

---

## Testing: Quality Assurance

Testing ensures your application works correctly before reaching users.

### Testing Methods

**1. Play Button Testing:**
```
Location: "Application wide tools" section
Action: Click "Play" button

Opens application in:
├─ Development environment
├─ Test environment
├─ Acceptance environment
└─ Production environment

Tip: Configure homepage template first
```

**2. Action Testing:**
```
Location: Action Editor → Test tab

Features:
├─ Test actions with sample data
├─ View step-by-step execution
├─ Check variable values
├─ Debug logic flows
└─ Verify outputs
```

**3. Manual UI Testing:**
```
Checklist:
├─ All buttons clickable
├─ Forms submit correctly
├─ Navigation works
├─ Responsive on mobile
├─ Error states handled
└─ Loading states visible
```

### Environment-Based Testing

**Development Testing:**
```
Purpose: Feature validation
Focus:
├─ New functionality works
├─ No console errors
├─ Basic flows complete
└─ Debug logs enabled
```

**Test Environment:**
```
Purpose: Quality assurance
Focus:
├─ Integration testing
├─ Edge case handling
├─ Performance baseline
├─ Cross-browser testing
└─ Regression testing
```

**Acceptance Testing:**
```
Purpose: Business validation
Focus:
├─ User stories verified
├─ Stakeholder approval
├─ Real-world scenarios
├─ Production-like data
└─ Final sign-off
```

**Production Monitoring:**
```
Purpose: Live validation
Focus:
├─ Error rate monitoring
├─ Performance tracking
├─ User feedback collection
├─ Critical path uptime
└─ Rollback readiness
```

### Common Testing Scenarios

**Authentication Flows:**
```
Test:
├─ Registration process
├─ Login/logout
├─ Password reset
├─ Session timeout
└─ Permission enforcement
```

**Data Operations:**
```
Test:
├─ Create records
├─ Read/display data
├─ Update existing records
├─ Delete records
├─ Search/filter functionality
└─ Data validation
```

**Error Handling:**
```
Test:
├─ Invalid inputs
├─ Network failures
├─ Timeout scenarios
├─ API errors
├─ Missing data
└─ Edge cases
```

### Debugging with Application Logs

**Accessing Logs:**
```
Side navigation → Application Logs

Log Information:
├─ Timestamp
├─ Action name
├─ Execution details
├─ Variable values
├─ Errors and warnings
└─ Performance metrics
```

**Using Logs for Debugging:**
```
1. Reproduce the issue
2. Check logs immediately
3. Filter by action/time
4. Trace execution flow
5. Identify failure point
6. Fix and retest
```

**Adding Custom Logs:**
```
Action: "Write to application log"
Use for:
├─ Tracing execution
├─ Recording decisions
├─ Debugging values
└─ Monitoring performance
```

### Common Errors & Solutions

**"No Homepage Set" Error:**
```
Cause: Application doesn't know starting page

Solution:
1. Go to Application settings
2. Select Root Template as homepage
3. Save and retest
```

**"Authentication Required" Error:**
```
Cause: Template requires login, user not authenticated

Solution:
1. Log in with valid credentials
2. Or disable auth on template (testing only)
3. Check user has required role
```

**"Value argument was null" Error:**
```
Cause: Missing data connection in action

Solution:
1. Check Application Logs
2. Find which action failed
3. Verify all inputs connected
4. Check variable exists
5. Reconnect blocks if needed
```

**Action Not Executing:**
```
Check:
├─ Trigger configured correctly
├─ Conditions evaluate to true
├─ No errors in logic
├─ Action is enabled
└─ User has required rights
```

### Best Practices

**Testing Strategy:**
```
✅ DO:
├─ Test incrementally (feature by feature)
├─ Use realistic test data
├─ Test edge cases
├─ Verify error handling
├─ Test on target devices
├─ Get user feedback early
└─ Automate where possible

❌ DON'T:
├─ Skip testing in lower environments
├─ Use only perfect data
├─ Ignore mobile testing
├─ Test only "happy path"
├─ Rush testing phase
└─ Skip documentation
```

**Bug Reporting:**
```
Good bug report includes:
├─ Steps to reproduce
├─ Expected behavior
├─ Actual behavior
├─ Screenshots/logs
├─ Environment details
└─ Impact assessment
```

### Quick Testing Checklist

**Before Testing:**
- [ ] Set homepage template
- [ ] Configure test users
- [ ] Prepare test data
- [ ] Define test scenarios

**Functional Testing:**
- [ ] All actions execute correctly
- [ ] Data displays accurately
- [ ] Forms validate properly
- [ ] Navigation works smoothly
- [ ] Error messages are helpful

**Cross-Environment:**
- [ ] Works in Development
- [ ] Works in Test
- [ ] Works in Acceptance
- [ ] Production deployment ready

**Quality Checks:**
- [ ] No console errors
- [ ] Mobile responsive
- [ ] Accessibility verified
- [ ] Performance acceptable
- [ ] Security validated

---

## FAQ: Frequently Asked Questions

### Getting Started

**Q: How long does it take to learn NoCode-X?**

```
Beginners: Can build simple apps in a few hours
Developers: Can leverage advanced features in days

Factors:
├─ Application complexity
├─ Familiarity with similar tools
├─ Quality of requirements
└─ Available templates/plugins

Recommendation: Start with tutorial videos
```

**Q: What can I build with NoCode-X?**

```
Possible Applications:
├─ Web and mobile applications
├─ E-commerce platforms
├─ Dashboards and analytics tools
├─ CRM systems
├─ Internal business tools
├─ Customer portals
├─ AI-powered applications
├─ Workflow automations
└─ API integrations

Limitation: Your imagination (and requirements)
```

**Q: Can I hire someone to build my app?**

```
Yes! Options:
├─ NoCode-X certified developers
├─ Agency partners
├─ Freelance platforms
└─ Community Discord

Benefits:
├─ Faster development
├─ Expert guidance
├─ Best practices
└─ Knowledge transfer
```

### Technical Questions

**Q: Can NoCode-X connect to third-party services?**

```
Absolutely! Methods:
├─ REST APIs: Connect any service with API
├─ GraphQL: Modern API integration
├─ Plugins: Pre-built integrations
├─ Webhooks: Real-time notifications
├─ Custom: Build your own connectors

Examples: Stripe, SendGrid, Slack, Salesforce, etc.
```

**Q: Can I use custom domain name?**

```
Yes!
├─ Professional branding
├─ SSL certificate included
├─ Easy DNS configuration
└─ Subdomain support

Setup: Application settings → Domain configuration
```

**Q: Is NoCode-X secure?**

```
Enterprise-grade security:
├─ OWASP TOP 10 compliance
├─ Multi-factor authentication
├─ Data encryption (rest & transit)
├─ EU data residency
├─ Comprehensive audit logging
├─ Security Score monitoring
└─ Regular security updates
```

**Q: What happens if NoCode-X shuts down?**

```
Business continuity protected:
├─ Data export: Available anytime
├─ Application export: Full backup
├─ Self-hosting: On-premises option
├─ Escrow clause: Legal protection
├─ Open source components
└─ Zero-data principle
```

### Ownership & Data

**Q: Who owns my data?**

```
You own your data completely:
├─ Full ownership rights
├─ Export anytime
├─ GDPR compliant
├─ No third-party sharing
└─ Control over retention
```

**Q: Who owns my application?**

```
You own your application:
├─ Full intellectual property rights
├─ Can export/backup
├─ Distribute as plugin
├─ Monetize freely
└─ NoCode-X owns the platform only
```

**Q: Can I export my data?**

```
Yes, anytime:
├─ Data export: JSON, CSV formats
├─ Application export: Full app backup
├─ Plugin export: For distribution
└─ API access: Programmatic export
```

**Q: Can I export my application?**

```
Yes:
├─ Export as plugin
├─ Backup to file
├─ Migrate to self-hosted
├─ Version control integration
└─ No vendor lock-in
```

### Comparison Questions

**Q: How does NoCode-X compare to Bubble.io?**

```
NoCode-X Advantages:
├─ Better performance and scalability
├─ Stronger security features
├─ More deployment options
├─ Built-in AI capabilities
├─ Advanced collaboration tools
├─ Transparent pricing
└─ EU data residency

Trade-offs:
└─ Smaller community (growing fast)
```

**Q: How does NoCode-X compare to Power Platform?**

```
NoCode-X Advantages:
├─ More flexible deployment
├─ Transparent pricing
├─ Advanced AI integration
├─ No Microsoft dependency
├─ Cross-platform
└─ No vendor lock-in

Best for: Independent, flexible solutions
```

**Q: Why use NoCode-X if I know how to code?**

```
Benefits for developers:
├─ Faster prototyping (days vs months)
├─ Focus on business logic
├─ AI-assisted development
├─ Easy collaboration
├─ Built-in best practices
├─ Reduced maintenance
└─ Still extensible with code when needed
```

### Vibe Coding Philosophy

**Q: What is "Vibe Coding" in NoCode-X?**

```
Hybrid approach:
├─ AI generates 80% (boilerplate)
└─ You refine 20% (business logic)

Benefits:
├─ Speed: Fast foundation
├─ Control: You own final decisions
├─ Quality: Secure by design
├─ Maintenance: Visual logic, not spaghetti code
└─ Confidence: Review everything
```

**Q: Why only 80% AI generation?**

```
Smart trade-off:
├─ First 80% is repetitive boilerplate
├─ Last 20% requires deep context
├─ Avoids "spaghetti code"
├─ Prevents AI hallucinations in security
├─ You understand and own the result
└─ Easier maintenance long-term
```

**Q: Is NoCode-X a chatbot?**

```
No - it's better:
├─ Structured workflow (not open chat)
├─ Step-by-step guidance
├─ Deterministic process
├─ Consistent results
├─ No "blank page syndrome"
└─ Senior PM approach, not chatbot
```

### Common Issues

**Q: Why do I get errors when testing?**

```
Common causes:
1. No homepage set
   → Configure Root Template as homepage

2. Authentication required
   → Login or disable auth (testing)

3. Missing data connections
   → Check Application Logs

4. Required fields empty
   → Fill all required inputs

5. Logic errors
   → Review action step-by-step
```

**Q: How do I debug my application?**

```
Debugging tools:
├─ Application Logs: Execution trace
├─ Action Tester: Step through logic
├─ Browser DevTools: Console errors
├─ Write to log: Custom debugging
└─ Preview mode: Quick testing
```

**Q: Why is my app slow?**

```
Optimization tips:
├─ Check Application Logs for bottlenecks
├─ Optimize database queries
├─ Use pagination for large datasets
├─ Minimize nested actions
├─ Cache frequently accessed data
└─ Test on production environment
```

### Pricing & Licensing

**Q: Is there a free tier?**

```
Yes! Free tier includes:
├─ Core features
├─ Development environment
├─ Community support
├─ Limited resources

Upgrade for: Production, more resources, premium features
```

**Q: How does pricing work?**

```
Transparent pay-as-you-use:
├─ No hidden fees
├─ Predictable costs
├─ Scale as you grow
├─ Clear feature tiers
└─ Cancel anytime

vs competitors: Often bundled, complex pricing
```

**Q: What about AppSumo/LTD (Lifetime Deal) licenses?**

```
LTD licenses (e.g., from AppSumo) provide:
├─ Fixed resource allocation (e.g., Tier 3: 5000 CPU min, 100GB storage)
├─ One-time payment (no monthly fees)
├─ Full feature access (same as regular subscriptions)
├─ Fixed AI credits (e.g., 50,000 one-time)
└─ Different from core-based monthly pricing

Important differences:
├─ LTD: Fixed resources, no recurring cost
├─ Regular: Flexible scaling, monthly billing
├─ LTD ideal for: Predictable workloads, budget planning
└─ Regular ideal for: Growing apps, variable usage

See "AppSumo Lifetime Deal (LTD): License Tier 3" section for details.
```

**Q: Can I make money with NoCode-X?**

```
Yes! Options:
├─ Build apps for clients
├─ Create and sell plugins
├─ Offer consulting services
├─ Build SaaS products
├─ Join partner program
└─ Teach others
```

### Getting Help

**Q: Where can I get support?**

```
Resources:
├─ Documentation: docs.nocode-x.com
├─ Discord: Community chat
├─ YouTube: Tutorial videos
├─ Email: Support team
├─ Hub: Example plugins
└─ Interactive tutorials: Built-in guides
```

**Q: How do I report bugs?**

```
Channels:
├─ Discord: Quick questions
├─ Email: Detailed reports
├─ Support portal: Tracked issues
├─ Community: Workarounds
└─ Feature requests: Roadmap voting
```

**Q: Can I contribute to NoCode-X?**

```
Yes! Ways to contribute:
├─ Create plugins for Hub
├─ Write tutorials
├─ Help in Discord
├─ Report bugs
├─ Suggest features
└─ Share your projects
```

---

# AppSumo Lifetime Deal (LTD): License Tier 3

Special pricing tier for AppSumo/LTD customers with fixed resource allocation.

## 📊 Resource Limits (Tier 3)

| Resource | Limit | Notes |
|----------|-------|-------|
| **Developers** | 10 people | Team collaboration limit |
| **CPU minutes** | 5,000/month | Processing time budget |
| **Storage** | 100 GB | Data and media storage |
| **Bandwidth** | 100 GB/month | Data transfer limit |
| **AI Credits** | 50,000 (one-time) | Initial AI credit balance |

## 🛠 Development Tools Included

**Core Building:**
```
✅ Add custom elements - Create custom UI components
✅ Prebuilt components in Hub - Access Hub plugin library
✅ AI-assisted development - Rocket Mode AI assistant
✅ Schedule logic to run - Jobs/scheduler functionality
✅ Drag-and-drop UI building - Visual template editor
✅ Responsive design - Mobile-friendly layouts
✅ Build reusable UI elements - Component reusability
✅ Design UI in a central place - Design System management
```

## 💻 Data & API Capabilities

```
✅ Create fully customizable APIs - Custom API endpoints
✅ Built-in database - NoCode-X native database
✅ Built-in media library - File storage and management
```

## 🛡 Security Features

**Enterprise-grade security included:**
```
✅ Built-in identity provider - User management & authentication
✅ Automatic audit log - Track all changes (who/when)
✅ Database encryption - At-rest encryption
✅ Application-level encryptions - Field-level encryption
✅ 95 score on SecurityScorecard - High security standards
```

## 🚀 Publishing & Version Management

```
✅ Custom domains - Connect your own domains
✅ Built-in DTAP/version mgmt - Full environment pipeline
   ├─ Development
   ├─ Test
   ├─ Acceptance
   └─ Production
```

## 💡 Working Within Tier 3 Limits

### Resource Monitoring

**Track usage:**
```
Workspace → Usage tab

Monitor:
├─ CPU minutes consumed
├─ Storage utilization
├─ Bandwidth usage
└─ Remaining AI credits
```

### Optimization Strategies

**CPU Minutes (5,000/month):**
```
Efficient usage:
├─ Use caching for frequently accessed data
├─ Optimize database queries
├─ Minimize nested action loops
├─ Use pagination for large datasets
├─ Schedule heavy jobs during off-peak hours

Example capacity:
~1,150,000 page loads/month (based on load testing)
~38,000 page loads/day
```

**Storage (100 GB):**
```
Management tips:
├─ Compress images before upload
├─ Use external storage for large files (S3, etc.)
├─ Archive old data
├─ Clean up unused media
└─ Monitor database growth
```

**Bandwidth (100 GB/month):**
```
Optimization:
├─ Enable CDN for static assets (automatic in production)
├─ Compress images and assets
├─ Use lazy loading for heavy content
├─ Cache API responses when possible
└─ Monitor high-traffic endpoints
```

**AI Credits (50,000 one-time):**
```
Conservation strategies:
├─ Use "Bring Your Own Key" (BYOK) when available
├─ Cache AI responses for repeated queries
├─ Optimize prompts to reduce token usage
├─ Use local/self-hosted models for simple tasks
└─ Monitor credit consumption per feature

Note: AI credits are consumed only when using NoCode-X AI provider.
Using your own API keys bypasses credit consumption.
```

### Scaling Beyond Tier 3

**Options if limits reached:**
```
1. Optimize current usage (see strategies above)
2. Purchase additional cores (regular pricing)
3. Use external services for heavy processing
4. Implement data archiving strategies
5. Consider multiple Tier 3 licenses for separate projects
```

### Best Practices for Tier 3

**Development:**
```
✅ DO:
├─ Plan resource-intensive features carefully
├─ Test in Development environment first
├─ Use Application Logs to monitor consumption
├─ Implement caching early
├─ Design for efficiency from start
└─ Monitor usage weekly

❌ DON'T:
├─ Ignore resource warnings
├─ Store unnecessary large files
├─ Run unoptimized heavy jobs frequently
├─ Waste AI credits on testing
└─ Skip monitoring until limit reached
```

**Team Collaboration (10 developers):**
```
Maximize efficiency:
├─ Use template libraries for consistency
├─ Implement design system early
├─ Create reusable components
├─ Share best practices
├─ Use version control effectively
└─ Document architectural decisions
```

## 🔍 Quick Tier 3 Checklist

**Monthly Review:**
- [ ] Check CPU minutes usage (target: <80%)
- [ ] Review storage utilization
- [ ] Monitor bandwidth consumption
- [ ] Track AI credit balance
- [ ] Optimize if approaching limits

**Development Planning:**
- [ ] Estimate resource needs for new features
- [ ] Plan for peak usage periods
- [ ] Implement caching strategy
- [ ] Design efficient data models
- [ ] Test resource consumption in Dev

**Team Management:**
- [ ] Assign developer seats efficiently
- [ ] Document resource ownership
- [ ] Train team on optimization
- [ ] Monitor individual usage if needed
- [ ] Plan for growth

---

## Tutorial: NoCode-X as Secure Backend for Any Frontend

Video: https://www.youtube.com/watch?v=FqrqaNdoVgc

Complete guide to using NoCode-X as a secure backend API for custom frontend applications (React example).

### Overview

**Goal:** Connect any frontend framework (React, Vue, Angular, etc.) to NoCode-X backend with secure OIDC authentication.

**Architecture:**
```
Frontend (React) ←OIDC→ NoCode-X (Authentication + API + Database)
```

### 1. Backend Setup in NoCode-X [01:27]

**Data Structure:**
```
Data Format: Person
Fields:
├─ first_name (Text)
├─ last_name (Text)
└─ email (Text)

Test Data: 20 sample records pre-loaded
```

**API Creation:**
```
API: Get Persons List
├─ Method: GET
├─ Authentication: Initially disabled (for testing)
└─ Returns: List of Person records
```

**Testing Without Auth:**
```
1. Create API endpoint
2. Disable "Authentication Required"
3. Test in browser/postman
4. Verify data returns correctly
```

### 2. Frontend Setup (React Example) [03:12]

**Basic Application Structure:**
```javascript
// React component structure
import { useState, useEffect } from 'react';

function App() {
  const [persons, setPersons] = useState([]);
  
  useEffect(() => {
    fetchPersons();
  }, []);
  
  const fetchPersons = async () => {
    const response = await fetch('https://your-app.nocode-x.com/api/persons');
    const data = await response.json();
    setPersons(data.content);
  };
  
  return (
    <div>
      <h1>People List</h1>
      <ul>
        {persons.map(person => (
          <li key={person.id}>
            {person.first_name} {person.last_name}
          </li>
        ))}
      </ul>
    </div>
  );
}
```

**Initial Result:**
```
✅ Data displays without authentication
✅ API is publicly accessible
⚠️ Not secure for production
```

### 3. OIDC Authentication Integration [05:12]

**NoCode-X Authentication Setup:**

Navigate to: **Authentication** tab
```
Configuration Options:
├─ Login Page Template → Customize UI
├─ Registration Page → Enable/disable
├─ Password Reset → Configure flow
└─ External Providers → Google, Microsoft, LinkedIn
```

**OIDC Library Selection:**
```
Recommended libraries:
├─ oidc-spa (used in tutorial)
├─ NextAuth.js (for Next.js)
├─ react-oidc-context
└─ Any OIDC-compatible library
```

**⚠️ Security Warning:**
```
❌ DON'T: Use methods requiring client_secret in frontend
   → Secret will be exposed and stolen

✅ DO: Use "Integrating front-end authentication" section
   → PKCE flow (no secret needed)
   → Secure token handling
```

### 4. OIDC Configuration [10:33]

**Three Required Parameters from NoCode-X:**

| Parameter | Location | Description |
|-----------|----------|-------------|
| **Issuer ID** | Workspace settings | Unique workspace identifier |
| **Client ID** | Authentication → Clients | Application identifier |
| **Home URL** | Redirect URL | Frontend URL (e.g., http://localhost:3000/) |

**Critical Configuration Step:**
```
In NoCode-X:
1. Go to Authentication settings
2. Add Redirect URL: http://localhost:3000/
3. ⚠️ Must match exactly (including trailing slash!)
4. Save configuration

Note: Mismatch causes authentication failure
```

**React OIDC Configuration:**
```javascript
// oidc-spa configuration
import { createOidc } from "oidc-spa";

export const { OidcProvider, useOidc } = createOidc({
  issuerUri: "https://your-workspace.nocode-x.com", // Issuer ID
  clientId: "your-client-id",                       // Client ID
  homeUrl: "http://localhost:3000/"                // Redirect URL
});
```

### 5. Login Logic Implementation [14:12]

**Authentication State Handling:**
```javascript
function App() {
  const { oidcTokens, login, isUserLoggedIn } = useOidc();
  
  if (!isUserLoggedIn) {
    return (
      <div>
        <p>Please log in to view data</p>
        <button onClick={() => login()}>Login</button>
      </div>
    );
  }
  
  // User is logged in - show protected content
  return <PersonsList />;
}
```

**Login Flow:**
```
1. User clicks "Login" button
2. oidc.login() called
3. Redirect to NoCode-X login page
4. User enters credentials
5. Redirect back to application
6. isUserLoggedIn = true
7. Access token available
```

### 6. Securing API with Access Token [17:19]

**Enable API Protection:**
```
In NoCode-X:
API → Edit → Authentication Required: ✅ ENABLED

Result: 
├─ Direct access returns 401 Unauthorized
├─ Token required in Authorization header
└─ Only authenticated users can access
```

**Token Injection in Frontend:**
```javascript
const fetchPersons = async () => {
  // Get access token from OIDC
  const accessToken = oidcTokens.accessToken;
  
  const response = await fetch('https://your-app.nocode-x.com/api/persons', {
    headers: {
      'Authorization': `Bearer ${accessToken}`
    }
  });
  
  if (response.ok) {
    const data = await response.json();
    setPersons(data.content);
  }
};
```

**Request Headers:**
```
GET /api/persons HTTP/1.1
Host: your-app.nocode-x.com
Authorization: Bearer eyJhbGciOiJSUzI1NiIs...
Content-Type: application/json
```

**Verification:**
```
Browser DevTools → Network tab:
├─ Request shows Authorization header
├─ Token is valid JWT
├─ Response: 200 OK with data
└─ No token: 401 Unauthorized
```

### 7. Authorization Rules (Advanced) [21:36]

**Role-Based Access:**
```
NoCode-X supports:
├─ User authentication (who are you?)
├─ Role assignment (what's your role?)
└─ API authorization (what can you access?)

Examples:
├─ Admin role → Full API access
├─ User role → Limited data access
└─ Guest role → Read-only access
```

**Implementation:**
```
Action: Check User Role
Condition: {{user.role}} == "admin"

Then: Allow full access
Else: Return limited data
```

### Complete Integration Checklist

**NoCode-X Backend:**
- [ ] Create Data Format with fields
- [ ] Add test data
- [ ] Generate API endpoint
- [ ] Configure Authentication settings
- [ ] Get Issuer ID, Client ID
- [ ] Add Redirect URL (exact match!)
- [ ] Enable "Authentication Required" on API

**Frontend Setup:**
- [ ] Install OIDC library (oidc-spa, etc.)
- [ ] Configure OIDC with 3 parameters
- [ ] Implement login/logout buttons
- [ ] Add authentication state handling
- [ ] Get access token from OIDC
- [ ] Add Authorization header to API calls
- [ ] Handle 401 errors gracefully

**Testing:**
- [ ] Test without auth (should fail with 401)
- [ ] Test login flow
- [ ] Test API with token (should succeed)
- [ ] Verify token in Network tab
- [ ] Test logout functionality
- [ ] Test error handling

### Best Practices

**Security:**
```
✅ DO:
├─ Always use HTTPS in production
├─ Store tokens securely (httpOnly cookies preferred)
├─ Implement token refresh
├─ Validate all API responses
├─ Handle authentication errors gracefully
└─ Use PKCE flow for SPAs

❌ DON'T:
├─ Expose client_secret in frontend
├─ Store tokens in localStorage (XSS risk)
├─ Skip HTTPS in production
├─ Ignore token expiration
└─ Trust client-side validation only
```

**Performance:**
```
✅ DO:
├─ Cache API responses when appropriate
├─ Implement loading states
├─ Use pagination for large datasets
├─ Minimize token refresh calls
└─ Optimize React re-renders

❌ DON'T:
├─ Call API on every render
├─ Fetch all data at once
├─ Ignore loading/error states
└─ Make synchronous token calls
```

### Common Issues & Solutions

**"Invalid redirect URI" Error:**
```
Cause: URL mismatch between frontend and NoCode-X config

Solution:
1. Check Redirect URL in NoCode-X (exact match)
2. Include trailing slash if configured
3. Verify protocol (http vs https)
4. Check for typos
```

**401 Unauthorized After Login:**
```
Cause: Token not being sent or expired

Solution:
1. Verify token is retrieved: oidcTokens.accessToken
2. Check header format: "Bearer " + token
3. Ensure token hasn't expired
4. Check API requires authentication (toggle enabled)
```

**CORS Errors:**
```
Cause: Frontend URL not allowed

Solution:
1. Add frontend domain to CORS settings
2. Check protocol and port
3. Verify in NoCode-X API settings
```

**Token Not Refreshing:**
```
Cause: Refresh token flow not configured

Solution:
1. Enable automatic refresh in OIDC config
2. Handle refresh errors
3. Redirect to login if refresh fails
```

### Extension: Other Frontend Frameworks

**Vue.js:**
```javascript
// Using vue-oidc-client
import { createOidcAuth } from 'vue-oidc-client';

const auth = createOidcAuth({
  authority: 'https://your-workspace.nocode-x.com',
  client_id: 'your-client-id',
  redirect_uri: 'http://localhost:3000/'
});
```

**Angular:**
```typescript
// Using angular-oauth2-oidc
import { OAuthService } from 'angular-oauth2-oidc';

export class AppComponent {
  constructor(private oauthService: OAuthService) {
    this.oauthService.configure({
      issuer: 'https://your-workspace.nocode-x.com',
      clientId: 'your-client-id',
      redirectUri: window.location.origin
    });
  }
}
```

**Vanilla JavaScript:**
```javascript
// Using oidc-client-ts
import { UserManager } from 'oidc-client-ts';

const userManager = new UserManager({
  authority: 'https://your-workspace.nocode-x.com',
  client_id: 'your-client-id',
  redirect_uri: 'http://localhost:3000/'
});
```

---

