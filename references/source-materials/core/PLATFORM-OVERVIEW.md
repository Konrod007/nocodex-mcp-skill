# NoCode-X Platform Overview

## What This Skill Does

This skill provides comprehensive guidance for building applications with NoCode-X - a visual development platform with AI assistance. It covers Rocket Mode (AI app generation), Logic building with Actions, UI creation, Database design, and API integrations.

## How to Use This Skill

This skill is organized into two parts:

**No-Code Part** — Visual development without coding
- UI design, templates, navigation
- Database design, actions, logic
- State management, lifecycle events

**Low-Code Part** — Advanced integrations with code
- HTML components, JavaScript
- External APIs, n8n, OIDC
- Vector databases, payment systems

## When to Use

Use when:
- Building web applications without coding
- Creating CRUD applications with secure authentication
- Integrating external APIs (REST, webhooks)
- Automating workflows with Jobs and scheduled tasks
- Working with NoCode-X Rocket Mode AI assistant
- **Managing LTD License Resources** - Optimizing applications within AppSumo Tier 3 limits

## AI Assistant Note

**For users with AppSumo LTD Tier 3 License:**
When providing recommendations, always consider the fixed resource limits:
- 5,000 CPU minutes/month
- 100GB storage
- 100GB bandwidth/month  
- 50,000 AI credits (one-time)

Suggest optimizations like caching, efficient queries, and external storage for large files to stay within limits.

## Core Components

| Component | Purpose | Documentation |
|-----------|---------|---------------|
| **Rocket Mode** | AI assistant for vibe coding - generates full app foundation | [Rocket Mode Guide](https://docs.nocode-x.com/nocode-x-platform/Rocket_Mode) |
| **UI (User Interface)** | Visual page builder with drag-and-drop | [UI Documentation](https://docs.nocode-x.com/building-concepts/ui/) |
| **Logic/Actions** | Building blocks for app logic | [Actions Guide](https://docs.nocode-x.com/building-concepts/logic/actions) |
| **Action Triggers** | Events that execute actions (buttons, API calls, Jobs) | [Action Triggers](https://docs.nocode-x.com/building-concepts/logic/action-triggers) |
| **Database** | Custom data tables with relationships | [Data Documentation](https://docs.nocode-x.com/building-concepts/data/) |
| **API** | Custom endpoints and external integrations | [API Documentation](https://docs.nocode-x.com/building-concepts/api/) |
| **Jobs** | Background tasks and scheduled automation | [Jobs Documentation](https://docs.nocode-x.com/building-concepts/jobs/) |
| **Design System** | Tokens for colors, typography, spacing | [Design System](https://docs.nocode-x.com/building-concepts/design-system/) |

## Key Documentation Links

- **Main Documentation**: https://docs.nocode-x.com
- **Interactive Tutorials**: https://docs.nocode-x.com/how%20to/interactive%20manuals/
- **Building Concepts**: https://docs.nocode-x.com/building-concepts/
- **Security Guide**: https://docs.nocode-x.com/security/
- **Testing**: https://docs.nocode-x.com/testing/

## Detailed Guides

### No-Code Part (Visual Development)
| Topic | Description | File |
|-------|-------------|------|
| **UI Design & Layout** | Templates, navigation, responsiveness, mobile-first design | [references/ui-design.md](../references/ui-design.md) |
| **Data & Logic** | Dynamic data, conditionals, database integration, action testing | [references/data-logic.md](../references/data-logic.md) |
| **State & Lifecycle** | Global state (Blackboard), lifecycle events (On Load/Destroy), data security | [references/state-and-lifecycle.md](../references/state-and-lifecycle.md) |

### Low-Code Part (Advanced Integrations)
| Topic | Description | File |
|-------|-------------|------|
| **Integrations** | HTML components, n8n, external backends, OIDC auth, JavaScript | [references/integrations.md](../references/integrations.md) |
| **Advanced Features** | Vector databases, Telegram bots, payment systems, SaaS patterns | [references/advanced-features.md](../references/advanced-features.md) |

### Licensing & Resources
| Topic | Description | File |
|-------|-------------|------|
| **AppSumo LTD Tier 3** | Lifetime Deal license limits and optimization strategies | [guides/APPSUMO-LTD-TIER-3.md](../guides/APPSUMO-LTD-TIER-3.md) |
| **FAQ** | Common questions about pricing, ownership, and support | [guides/PHASE-2-ADVANCED.md](../guides/PHASE-2-ADVANCED.md) |

## File Structure

```
nocode-x/
├── SKILL.md                    # Main navigation file
├── core/
│   ├── PLATFORM-OVERVIEW.md    # This file
│   ├── QUICK-START.md          # Quick start checklist
│   └── ROCKET-MODE.md          # AI app generation guide
├── tutorials/
│   ├── VIDEO-TUTORIALS.md      # Video tutorial index
│   ├── MINDSHIFT-AUDIO.md      # 4-part Mindshift Audio tutorial
│   └── CRM-SERIES.md           # 4-part CRM development guide
├── guides/
│   ├── PHASE-1-PRODUCTION.md   # Jobs, Security, RBAC, DTAP
│   ├── PHASE-2-ADVANCED.md     # Design System, Hub, Testing, FAQ
│   └── APPSUMO-LTD-TIER-3.md   # Resource limits and optimization
└── references/
    ├── ui-design.md
    ├── data-logic.md
    ├── state-and-lifecycle.md
    ├── integrations.md
    └── advanced-features.md
```
