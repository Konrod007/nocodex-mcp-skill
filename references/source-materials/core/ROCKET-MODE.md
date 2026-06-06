# Rocket Mode: AI App Generation

Rocket Mode is your AI assistant that translates business ideas into secure, working app foundations.

## 10-Step Process

1. **Application Description** - Name, tagline, feature list (write as actions: "Send email reminders" not "Notifications")
2. **Customer Journey** - Map trigger → steps → success for each persona (Guest, Organizer, Admin)
3. **Requirements** - Prioritize with Must/Should/Could (MoSCoW method)
4. **Design System** - Choose palette, fonts, spacing tokens, components with states
5. **Pages** - One page = one job with single primary CTA
6. **Test Users** - Create test accounts for different roles
7. **Database** - Define tables, fields, relationships, access rules
8. **Test Data** - Generate realistic sample data
9. **Root Page** - Build home page visual first, then add logic
10. **Other Pages** - Repeat: design → logic for each page

## Prompt Best Practices

### Good Prompts (Specific):
- "Rename app to 'EventPro' and make tone friendly and trustworthy"
- "Keep only booking, listing, and email reminders as Must; move analytics to Later"
- "Add Attendance as join table between Users and Events (user_id, event_id, status)"
- "Make 'Browse Events' the primary CTA and add three-step 'How it works'"

### Bad Prompts (Vague):
- "Make it better"
- "Add notifications"
- "Improve the design"

### Pro Tips:
- Be specific: "Adjust X to Y" works faster than general requests
- Less is faster: fewer features = quicker iteration
- Tie each feature to a real user goal
- Use MoSCoW: Must (essential), Should (desirable soon), Could (later)
- Include empty/error states in your requests
- Mobile-first: fewer steps, big buttons

## Resources

- [Quick Start Checklist](./QUICK-START.md)
- [Platform Overview](./PLATFORM-OVERVIEW.md)
- Official Docs: https://docs.nocode-x.com/nocode-x-platform/Rocket_Mode
