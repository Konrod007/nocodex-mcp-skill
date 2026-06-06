---
name: nocode-x
description: Create applications using NoCode-X visual development platform with AI assistance. Use Rocket Mode for app generation, build logic with Actions, create UI components, design databases, and integrate APIs. Includes prompt engineering best practices for effective AI collaboration.
license: MIT
compatibility: claw
version: 2.0
---

# NoCode-X Development Skill

## Overview

Comprehensive guidance for building applications with NoCode-X - a visual development platform with AI assistance.

**For AppSumo LTD Tier 3 Users:** This skill automatically considers your resource limits (5000 CPU min, 100GB storage, 100GB bandwidth, 50K AI credits) when providing recommendations.

## Quick Navigation

| Section | Description | File |
|---------|-------------|------|
| **Quick Start** | 10-step checklist to launch your first app | [core/QUICK-START.md](./core/QUICK-START.md) |
| **Platform Guide** | Core concepts and architecture | [core/PLATFORM-OVERVIEW.md](./core/PLATFORM-OVERVIEW.md) |
| **Rocket Mode** | AI app generation guide | [core/ROCKET-MODE.md](./core/ROCKET-MODE.md) |
| **Video Tutorials** | 23 step-by-step video guides | [tutorials/INDEX.md](./tutorials/INDEX.md) |
| **Mindshift Audio** | 4-part mobile app tutorial (1,797 lines) | [Part 1](./tutorials/MINDSHIFT-AUDIO-PART-1.md), [Part 2](./tutorials/MINDSHIFT-AUDIO-PART-2.md), [Part 3](./tutorials/MINDSHIFT-AUDIO-PART-3.md), [Part 4](./tutorials/MINDSHIFT-AUDIO-PART-4.md) |
| **CRM Series** | 5-part CRM tutorial (1,292 lines) | [Part 1](./tutorials/CRM-PART-1-EMAIL.md), [Part 2](./tutorials/CRM-PART-2-UPDATE.md), [Part 3](./tutorials/CRM-PART-3-REFACTORING.md), [Part 4](./tutorials/CRM-PART-4-CRUD.md), [Dashboard](./tutorials/CRM-PART-14-DASHBOARD.md) |
| **Production Guide** | Jobs, Security, RBAC, DTAP (818 lines) | [guides/PHASE-1-FULL.md](./guides/PHASE-1-FULL.md) |
| **Advanced Guide** | Design System, Hub, Testing, FAQ (1,669 lines) | [guides/PHASE-2-FULL.md](./guides/PHASE-2-FULL.md) |
| **LTD Tier 3** | Resource limits and optimization | [guides/APPSUMO-LTD-TIER-3.md](./guides/APPSUMO-LTD-TIER-3.md) |
| **UI Reference** | UI patterns and best practices | [references/ui-design.md](./references/ui-design.md) |
| **Data & Logic** | Database and action patterns | [references/data-logic.md](./references/data-logic.md) |
| **State & Security** | State management and security | [references/state-and-lifecycle.md](./references/state-and-lifecycle.md) |
| **Integrations** | HTML, n8n, OIDC, JavaScript | [references/integrations.md](./references/integrations.md) |
| **Advanced Features** | Vector DB, payments, SaaS | [references/advanced-features.md](./references/advanced-features.md) |

## When to Use

- Building web applications without coding
- Creating CRUD applications with secure authentication
- Integrating external APIs (REST, webhooks)
- Automating workflows with Jobs and scheduled tasks
- Working with NoCode-X Rocket Mode AI assistant
- Managing LTD License Resources within AppSumo Tier 3 limits

## Core Components

| Component | Purpose |
|-----------|---------|
| **Rocket Mode** | AI assistant for vibe coding |
| **UI** | Visual page builder with drag-and-drop |
| **Logic/Actions** | Building blocks for app logic |
| **Action Triggers** | Events that execute actions |
| **Database** | Custom data tables with relationships |
| **API** | Custom endpoints and integrations |
| **Jobs** | Background tasks and scheduled automation |
| **Design System** | Tokens for colors, typography, spacing |

## Official Documentation

- **Main Docs**: https://docs.nocode-x.com
- **Interactive Tutorials**: https://docs.nocode-x.com/how%20to/interactive%20manuals/
- **Building Concepts**: https://docs.nocode-x.com/building-concepts/
- **Security**: https://docs.nocode-x.com/security/

## License

MIT License - See LICENSE file for details

---

**Note:** NoCode-X is actively evolving. Check the official documentation for the latest features and updates.


---

## Core Documentation

### PLATFORM-OVERVIEW.md
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


### QUICK-START.md
# Quick Start Checklist

Get your first NoCode-X application up and running in 7 phases.

## Phase 1: Setup
- [ ] Create new application in NoCode-X
- [ ] Configure Design System (colors, fonts)
- [ ] Set up authentication (or use Vanilla Login plugin)

## Phase 2: Database
- [ ] Create Data Formats (tables)
- [ ] Define fields and relationships
- [ ] Generate test data

## Phase 3: UI
- [ ] Create Root Template with navigation
- [ ] Build Child Templates for pages
- [ ] Configure responsive design

## Phase 4: Logic
- [ ] Create Actions for business logic
- [ ] Set up Action Triggers
- [ ] Test with Action Tests

## Phase 5: API Development (Rapid)
- [ ] Use "Create CRUD from text" for quick API generation
- [ ] Test endpoints with Postman/curl
- [ ] Configure pagination and filters
- [ ] Add authentication to endpoints
- [ ] Customize Actions if needed

## Phase 6: Integration
- [ ] Configure external integrations
- [ ] Set up webhooks
- [ ] Test end-to-end flow

## Phase 7: Launch
- [ ] Test all user flows
- [ ] Configure custom domain
- [ ] Set up monitoring

## Next Steps

After completing this checklist:
1. Explore detailed tutorials in [tutorials/](../tutorials/) folder
2. Learn production-ready features in [guides/](../guides/) folder
3. Reference advanced patterns in [references/](../references/) folder

## Resources

- **Video Tutorials**: [VIDEO-TUTORIALS.md](../tutorials/VIDEO-TUTORIALS.md)
- **Platform Overview**: [PLATFORM-OVERVIEW.md](./PLATFORM-OVERVIEW.md)
- **Rocket Mode Guide**: [ROCKET-MODE.md](./ROCKET-MODE.md)


### ROCKET-MODE.md
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


---

## References

### ui-design.md
# NoCode-X: UI Design & Layout

> Руководство по дизайну интерфейса, шаблонам и навигации в NoCode-X
> На основе видео: https://www.youtube.com/watch?v=SBkcR7TvIkw и https://www.youtube.com/watch?v=YhTCkMu1npk

---

## Содержание

1. [Real-World Implementation (Mindshift Audio)](#real-world-implementation-mindshift-audio)
2. [Template Hierarchy](#template-hierarchy)
3. [Navigation Patterns](#navigation-patterns)
4. [Homepage Design](#homepage-design)
5. [Responsiveness](#responsiveness)
6. [Best Practices](#best-practices)

---

## Real-World Implementation (Mindshift Audio)

**Project:** Migrating hypnotherapy MVP to NoCode-X  
**Video:** https://www.youtube.com/watch?v=SBkcR7TvIkw

### Functional Blocks Implemented

**Phase 1 - Infrastructure:**
- **Authentication System:** Registration, login, password recovery pages
- **Design System:** Global colors and fonts for UI consistency
- **Routing Logic:** Navigation between pages
- **Data Collection:** Gathering input from fields (email, password, name) and passing to actions

### Technical Techniques

#### Visual Programming (UI/UX)

**Mobile-First Approach:**
- Start development with mobile view immediately
- Use Template Editor with Mobile View toggle [06:08]
- Test on actual mobile devices, not just responsive preview

**Layout Components:**

| Component | Use Case | Timestamp |
|-----------|----------|-----------|
| **Vertical List** | Stack elements vertically (forms, buttons) | [10:09] |
| **Horizontal List** | Row layout (e.g., checkbox + "I agree to terms") | [01:14:30] |

**Positioning Best Practices:**
- Use **Fit to content** for width/height instead of fixed pixels
- Elements adapt to content, not rigid pixel sizes [17:11]

**Hotkeys:**
- **Shift key:** Quick toggle between selection tool and page pan [05:20]
- Hold Shift to pan, release to select elements

#### Logic & Action Triggers

**Action Chains:**
- Logic built from chained functions
- Each function has execution order number [47:42]
- Chain flows sequentially through numbered steps

**Scope (Variable Visibility):**
- Data stored in "Scope" like a table (variable name → value)
- Subsequent functions in chain can access this data [53:51]
- Think of it as temporary storage between action steps

**Abstraction Pattern:**
- Extract repeating logic into separate actions
- Call via **Execute Action** to keep main schema clean [49:02]
- Example: Email sending logic reused across multiple flows

```
Main Action: User Registration
  ├─ Step 1: Validate input
  ├─ Step 2: Execute Action "Send Welcome Email" (abstracted)
  └─ Step 3: Redirect to dashboard

Abstracted Action: Send Welcome Email
  ├─ Step 1: Get email from Scope
  ├─ Step 2: Call email API
  └─ Step 3: Log sent email
```

### Expert Tips from Video

**1. Naming Conventions [44:22]**
```
❌ Bad: email_input_1, button_3, text_field_5
✅ Good: login_email_field, signup_submit_button, terms_checkbox

Why: AI assistant understands your structure better with clear names
```

**2. Design System First [08:16]**
```
Step 1: Configure colors in Design System before building pages
Step 2: Use design tokens throughout
Result: Change brand color once → updates everywhere automatically
```

**3. Use Plugins for Standard Tasks [41:33]**
```
Task: Login/Registration system
Manual: 2-3 hours building from scratch
Plugin: "Vanilla Login" → 5 minutes install

When to use plugins:
- Standard authentication flows
- Common UI patterns
- Repeated business logic
```

### Common Patterns

**Registration Flow:**
```
1. User enters email, password, name
2. Client-side validation (format checks)
3. Terms checkbox validation (must be checked) [21:20]
4. Server-side validation (unique email)
5. Create user record
6. Send welcome email (abstracted action)
7. Redirect to dashboard
```

**Mobile Form Layout:**
```
Container: Vertical List
  ├─ Horizontal List: [Logo] [App Name]
  ├─ Vertical List (Fit to content)
  │   ├─ Email Input Field
  │   ├─ Password Input Field
  │   └─ Name Input Field
  ├─ Horizontal List: [Checkbox] ["I agree to Terms"]
  └─ Submit Button
```

---

## Template Hierarchy

Video: https://www.youtube.com/watch?v=YhTCkMu1npk

Template inheritance — ключевая концепция для повторяющихся элементов.

### Root Template (Корневой)
- Содержит элементы, видимые на ВСЕХ страницах
- Например: навигационная панель, header, footer
- Изменения здесь → автоматически везде [05:16]

### Child Templates (Дочерние)
- Наследуют все элементы родителя
- Добавляют уникальный контент для конкретной страницы
- Любое изменение в Root автоматически отражается во всех дочерних [28:09]

**Преимущество:**
```
Задача: Добавить кнопку "Поддержка" в меню
Без иерархии: Открыть 10 страниц → добавить кнопку на каждую
С иерархией: Открыть Root Template → добавить кнопку один раз [28:09]
```

**Best Practice:**
```
Проверяй уровень иерархии перед созданием:
- Глобальные элементы (меню, логотип) → ТОЛЬКО в Root
- Уникальные элементы страницы → в Child Template
```

---

## Navigation Patterns

### Bottom Navigation (Нижнее меню)

**Стандарт для мобильных приложений** — меню "под большой палец".

**Структура:**
```
Main Container: Vertical List
  ├─ Content Area: Vertical List (flex-grow, scrollable)
  │   └─ [Весь контент страницы]
  └─ Bottom Menu: Horizontal List (fixed height, no scroll)
      ├─ Nav Item 1: [Icon] + [Label]
      ├─ Nav Item 2: [Icon] + [Label]
      ├─ Nav Item 3: [Icon] + [Label]
      └─ Nav Item 4: [Icon] + [Label]
```

**Ключевые настройки:**
- Content area: занимает всё доступное пространство
- Bottom menu: прижат к низу (fixed/sticky) [08:42]
- Content должен скроллиться, меню — нет [33:06]

**Кастомные SVG-иконки:**

Вместо стандартных иконок — кастомный SVG-код [19:33].

**Лайфхак с цветом:**
```svg
<!-- До -->
<svg stroke="#000000" fill="#000000">

<!-- После (гибкая стилизация) -->
<svg stroke="currentColor" fill="currentColor">
```
`currentColor` = наследует цвет текста/темы NoCode-X [21:54]

**Навигация:**
- Action: `Route to page`
- Target: нужный шаблон (например, Home, Profile, Settings) [30:11]

---

## Homepage Design

### Блоки на главной:

**Приветствие:**
```
Заголовок: "Hello [user_first_name]"
Placeholder: динамически заполняется данными пользователя [35:11]
```

**Баланс/Кредиты:**
```
Блок с информацией о доступных кредитах
Иконка + текст: "У вас 150 кредитов"
[36:56]
```

**Блок активности (Consistency):**
```
Переключатели: [7 дней] [28 дней]
Тип: Horizontal List с текстовыми элементами
Эффект: Hover state для активной кнопки [52:38]
```

---

## Responsiveness

### Min Size (Минимальный размер)
- Задавать минимальную ширину в пикселях
- Элементы не "схлопываются" на маленьких экранах [41:34]

### Wrap (Перенос)
- Родительский контейнер: `Wrap to multiple lines` = true
- Элементы в ряд на планшете → перенос на телефоне [42:54]

### Редактирование по устройствам
```
Верхняя панель редактора:
[📱] [📱💻] [💻] — переключение между breakpoint

Возможности:
- Разный размер шрифта для мобильного/десктопа
- Разная видимость элементов
- Разные отступы
[46:15]
```

---

## Best Practices

### Установка Homepage
```
Application Selector → Pencil icon (Edit)
→ Homepage dropdown → Select template
```
Теперь домен открывает эту страницу по умолчанию [31:16]

### Чек-лист разработки UI

- [ ] Создать Root Template с общими элементами
- [ ] Настроить Bottom Navigation (иконки + роутинг)
- [ ] SVG-иконки с `currentColor` для стилизации
- [ ] Content area со скроллингом
- [ ] Homepage с приветствием и плейсхолдерами
- [ ] Адаптивность: Min Size + Wrap
- [ ] Указать Homepage в настройках приложения
- [ ] Тест на мобильном устройстве

### Critical Implementation Elements

| Feature | Implementation | Video Ref |
|---------|---------------|-----------|
| **Credit System** | Track AI usage through user balance | [03:11] |
| **AI Integration (LLM)** | Connect module for content generation | [01:05] |
| **Audio Player** | HTML component for playing files | [03:18] |
| **MFA** | Biometry (Face/PIN) or Google Authenticator | [01:10:15] |
| **Data Validation** | Email validation, required field checks | [21:20] |

---

*Part of NoCode-X Skill | Video Tutorials: https://www.youtube.com/playlist?list=PLNoCode-X*


### data-logic.md
# NoCode-X: Data, Logic & Database

> Руководство по работе с данными, условной логикой и базой данных в NoCode-X
> На основе видео: https://www.youtube.com/watch?v=7iaPI0XaXkg

---

## Содержание

1. [Dynamic Data Population](#dynamic-data-population)
2. [Conditional Logic](#conditional-logic)
3. [Database Integration](#database-integration)
4. [Complex Logic Examples](#complex-logic-examples)
5. [Action Testing](#action-testing)
6. [Best Practices](#best-practices)

---

## Dynamic Data Population

**Video:** https://www.youtube.com/watch?v=7iaPI0XaXkg

### Плейсхолдеры → Реальные данные

**Trigger:** **On Load** (при загрузке страницы)

**Пример:**
```
Шаг 1: Создать заголовок "Welcome back, [user_first_name]"
Шаг 2: Добавить триггер On Load на шаблон
Шаг 3: Функция: Replace placeholder on title component
Шаг 4: Источник: Current user → first_name [04:36]

Результат: "Welcome back, [user_first_name]" → "Welcome back, Tristan" [03:12]
```

### Глобальный Scope
- `Current user` автоматически доступен в любом экшене
- Содержит все поля авторизованного пользователя
- Не нужен отдельный поиск в БД для базовых данных [04:36]

---

## Conditional Logic

### Branching (Ветвление)

Создание разных путей выполнения на основе условий.

```
Action: Check User
├─ Branch 1: IF user.name == "Tristan"
│   └─ Show alert: "Admin access granted"
└─ Branch 2: ELSE
    └─ Show message: "Welcome, user" [09:02]
```

### Hide/Show Elements

```
Функции:
- Hide element (скрыть компонент)
- Show element (показать компонент)

Use cases:
- Показывать админ-панель только для role == "admin" [13:07]
- Скрывать форму после успешной отправки
- Показывать loader во время загрузки
```

---

## Database Integration

### Создание таблиц (Data Formats)

```
Таблица: user_accounts
Поля:
- credits (Number) - баланс кредитов
- user_email (Email) - связь с аккаунтом
- last_active (Date)
[16:47]
```

### Поиск данных

```
Функция: Search one data record
Фильтр: user_email == Current user.email
Результат: Запись с балансом [20:02]

Вывод: Отобразить credits на экране
```

---

## Complex Logic Examples

### Consistency Tracker (GitHub-style)

**Сценарий:** Трекер активности (как GitHub contributions)

**Архитектура:**
```
Таблица: listened_events
Поля:
- user_email (Email)
- event_date (Date)
- event_type (String)
[01:34:01]
```

**Логика отображения:**
```
Trigger: On Load

Action: Display Activity
├─ Step 1: For Loop (7 или 28 итераций) [49:36]
│   ├─ Calculate date: Today - i days
│   ├─ Search: listened_events WHERE date == calculated_date AND user == current [01:37:10]
│   ├─ Branch:
│   │   ├─ IF found: Add template "Active Day" (закрашенный) [01:41:41]
│   │   └─ IF not found: Add template "Non-active Day" (пустой)
│   └─ Append to Horizontal List
└─ Step 2: Render list

Настройка Direction: Right to Left [59:57]
→ Текущий день всегда справа
```

**Переключение режимов:**
```
Кнопка "7 дней":
- Set variable: days_count = 7
- Reload activity block

Кнопка "28 дней":
- Set variable: days_count = 28
- Reload activity block [01:11:07]
```

---

## Action Testing

### Встроенное тестирование

```
Инструмент: Action Tests

Возможности:
- Запуск экшена с тестовыми параметрами
- Просмотр логов выполнения в реальном времени
- Проверка значений переменных на каждом шаге [45:12]

Пример:
Input: days = 14
Output: Logs показывают каждую итерацию цикла

Преимущество:
Не нужно перезагружать приложение для тестирования [46:14]
```

---

## Best Practices

### Форматирование дат
```
❌ Неправильно: Сравнивать полные timestamp
✅ Правильно: Приводить к YYYY-MM-DD перед сравнением

Почему: Избежать ошибок из-за часов/минут/секунд [01:36:42]
```

### Именование плейсхолдеров
```
❌ Bad: Title, Title 2, Title 3
✅ Good: Title_Welcome_Name, Title_Credits_Balance, Title_Streak_Count

Почему: В списке функций их можно отличить [02:13]
```

### Направление списка
```
For цикл: Today → Today-6 days
Horizontal List: Direction = Right to Left

Результат визуально:
← новые                               старые →
[Today] [Today-1] [Today-2] ... [Today-6]
[59:57]
```

---

## Чек-лист работы с данными

- [ ] Создать Data Format (таблицу) для хранения данных
- [ ] Связать с Current user через email или ID
- [ ] Добавить On Load триггер для заполнения плейсхолдеров
- [ ] Настроить Branching для условного отображения
- [ ] Использовать For Loop для перебора данных
- [ ] Форматировать даты перед сравнением (YYYY-MM-DD)
- [ ] Дать понятные имена компонентам с плейсхолдерами
- [ ] Протестировать экшен через Action Tests
- [ ] Проверить Reverse Direction для списков дат

---

*Part of NoCode-X Skill | Video Tutorial: https://www.youtube.com/watch?v=7iaPI0XaXkg*


### state-and-lifecycle.md
# NoCode-X: State Management & Lifecycle Events

> Руководство по управлению состоянием и жизненным циклом страниц в NoCode-X

---

## Содержание

1. [Lifecycle Events (События жизненного цикла)](#lifecycle-events-события-жизненного-цикла)
2. [Global State Management (Blackboard Pattern)](#global-state-management-blackboard-pattern)
3. [Data Security & Secrets](#data-security--secrets)
4. [Multi-level Encryption](#multi-level-encryption)

---

## Lifecycle Events (События жизненного цикла)

### On Load

**Когда срабатывает:** При загрузке/открытии страницы пользователем.

**Use Cases:**
- Инициализация данных (загрузка конфигурации чата)
- Проверка токена авторизации
- Заполнение плейсхолдеров данными пользователя
- Загрузка списков и таблиц

**Пример:**
```
Trigger: On Load
Action: Initialize Page
├─ Step 1: Fetch user configuration from Data Format
├─ Step 2: Replace placeholders with user data
├─ Step 3: Check authentication status
└─ Step 4: Load dynamic content
```

### On Destroy

**Когда срабатывает:** Когда пользователь покидает страницу (закрывает приложение или переходит на другую страницу).

**Use Cases:**
- Закрытие сессии
- Сохранение промежуточного состояния (черновики)
- Очистка временных данных
- Логирование времени проведенного на странице

**Пример:**
```
Trigger: On Destroy
Action: Cleanup Session
├─ Step 1: Save draft data to database
├─ Step 2: Clear sensitive data from Scope
├─ Step 3: Log session end time
└─ Step 4: Close WebSocket connections (if any)
```

### Другие события жизненного цикла

| Событие | Описание | Применение |
|---------|----------|------------|
| **On Visible** | Страница стала видимой (вкладка активна) | Обновление real-time данных |
| **On Hidden** | Страница скрыта (вкладка неактивна) | Пауза видео/аудио |
| **On Before Unload** | Перед закрытием/переходом | Предупреждение о несохраненных данных |

---

## Global State Management (Blackboard Pattern)

### Что такое Blackboard?

**Blackboard Pattern** — паттерн глобального состояния, где данные записываются в единое хранилище и автоматически становятся доступны всем компонентам и шаблонам.

**Преимущества:**
- ✅ Не нужно передавать параметры через URL
- ✅ Избавление от длинных цепочек связей
- ✅ Данные доступны во вложенных компонентах любого уровня
- ✅ Автоматическое обновление при изменении

### Как использовать State

**Запись в State:**
```
Action: Update User Balance
├─ Step 1: Calculate new balance
└─ Step 2: Write to State → user.balance = newValue
```

**Чтение из State:**
```
// В любом месте приложения:
State.user.balance → автоматически доступно

// В шаблоне:
[State.user.balance] → отображает текущее значение
```

### Примеры использования

**1. Обновление баланса:**
```
Сценарий: Пользователь делает запрос в чате
→ Списываются кредиты
→ Баланс обновляется в State
→ Все компоненты видят новое значение автоматически
```

**2. Глобальные настройки:**
```
State.app.theme = "dark"
State.app.language = "ru"
State.app.notifications_enabled = true
```

**3. Состояние авторизации:**
```
State.auth.isAuthenticated = true
State.auth.userRole = "admin"
State.auth.permissions = ["read", "write", "delete"]
```

### Сравнение: Scope vs State

| Характеристика | Scope | State (Blackboard) |
|----------------|-------|-------------------|
| **Область видимости** | Текущий Action | Все приложение |
| **Доступность** | Последующие шаги экшена | Любой компонент/шаблон |
| **Время жизни** | До конца экшена | Пока приложение открыто |
| **Использование** | Временные данные | Глобальное состояние |

---

## Data Security & Secrets

### Secret Fields (Секретные поля)

**Что это:** Специальная классификация полей для хранения чувствительных данных.

**Как настроить:**
```
1. Создать поле в Data Format
2. Field Settings → Classification → "Secret"
3. NoCode-X автоматически включает:
   - Шифрование на уровне приложения
   - Аудит изменений
   - Ограничение доступа к логам
```

### Уровни доступа

**Типы полей по классификации:**

| Классификация | Хранение | Доступ | Использование |
|---------------|----------|--------|---------------|
| **Public** | Обычное | Без ограничений | Имя, email |
| **Internal** | Обычное | Только внутри приложения | ID пользователя |
| **Confidential** | Шифрование | Только для админов | Номер телефона |
| **Secret** | Шифрование + аудит | Только через специальные функции | API ключи, пароли |

### Audit Log (Аудит)

**Что фиксируется:**
```
Событие: Изменение секретного значения
├─ Timestamp: 2024-01-15 14:32:18 UTC
├─ User: admin@company.com
├─ Action: UPDATE
├─ Field: api_key_stripe
├─ Old Value: sk_***789
└─ New Value: sk_***abc
```

**Важно для соответствия:**
- ✅ SOC 2
- ✅ GDPR
- ✅ HIPAA
- ✅ PCI DSS

---

## Multi-level Encryption

### Архитектура шифрования (Perfect Forward Security)

```
┌─────────────────────────────────────────┐
│         Layer 1: Application            │
│     (Данные шифруются приложением)      │
│         Encrypted Data Storage          │
└─────────────────────────────────────────┘
                    │
                    ▼ (Ключ для дешифровки)
┌─────────────────────────────────────────┐
│         Layer 2: Key Database           │
│    (База ключей, сама зашифрована)      │
│      Encrypted Keys Storage             │
└─────────────────────────────────────────┘
                    │
                    ▼ (Мастер-ключ)
┌─────────────────────────────────────────┐
│         Layer 3: Master Key             │
│    (Хранится в отдельном защищенном     │
│     хранилище - HSM / Cloud KMS)        │
└─────────────────────────────────────────┘
```

### Как это работает

**При записи данных:**
```
1. Приложение генерирует уникальный ключ шифрования
2. Данные шифруются этим ключом
3. Ключ шифрования сохраняется в Key Database (зашифрованный мастер-ключом)
4. Мастер-ключ никогда не покидает HSM
```

**При чтении данных:**
```
1. Запрос к Key Database
2. HSM расшифровывает ключ шифрования
3. Ключ используется для расшифровки данных
4. Ключ уничтожается из памяти
```

### Преимущества Perfect Forward Security

1. **Компрометация одного слоя ≠ компрометация всего**
2. **Даже при доступе к базе данных — данные нечитаемы**
3. **Ключи меняются автоматически**
4. **Нет единой точки отказа**

---

## Best Practices

### Когда использовать что

| Сценарий | Решение | Пример |
|----------|---------|--------|
| Временные данные в экшене | Scope | Промежуточный результат вычисления |
| Глобальное состояние приложения | State (Blackboard) | Тема оформления, баланс пользователя |
| Чувствительные данные | Secret Fields | API ключи, пароли |
| Инициализация страницы | On Load | Загрузка конфигурации |
| Очистка при выходе | On Destroy | Закрытие сессии |

### Security Checklist

- [ ] Все API ключи помечены как Secret
- [ ] Включен Audit Log для секретных полей
- [ ] Используется State для глобальных данных вместо передачи через URL
- [ ] On Destroy очищает чувствительные данные
- [ ] Регулярный просмотр Audit Log
- [ ] Доступ к секретам только через специализированные функции

### Пример интеграции

```
Сценарий: Настройка API интеграции

1. Хранение ключа:
   Data Format: integrations_config
   ├─ name: "Stripe"
   ├─ api_endpoint: "https://api.stripe.com"
   └─ api_key: [Secret Field] ← Шифруется + аудит

2. Использование в экшене:
   Action: Process Payment
   ├─ Step 1: Read from State → current_integration = "stripe"
   ├─ Step 2: Fetch config from Data Format
   ├─ Step 3: Get secret api_key (автоматически расшифровывается)
   └─ Step 4: Call Stripe API

3. Мониторинг:
   Audit Log → Видны все обращения к api_key
   Who: admin@company.com
   When: 2024-01-15 10:30:00
   What: READ stripe.api_key
```

---

*Part of NoCode-X Skill*


### integrations.md
# NoCode-X: Integrations & External Systems

> Руководство по интеграции HTML-компонентов, n8n и использованию NoCode-X как бэкенда
> На основе видео: https://www.youtube.com/watch?v=LuaRbmWhmpM и https://www.youtube.com/watch?v=FqrqaNdoVgc

---

## Содержание

1. [HTML Components](#html-components)
2. [n8n Integration](#n8n-integration)
3. [Configuration & Security](#configuration--security)
4. [State Management (Future)](#state-management-future)
5. [NoCode-X as Backend](#nocode-x-as-backend)
6. [Best Practices](#best-practices)

---

## HTML Components

**Video:** https://www.youtube.com/watch?v=LuaRbmWhmpM

### Возможности HTML-компонента

| Feature | Description | Timestamp |
|---------|-------------|-----------|
| **Pure HTML/CSS/JS** | Добавление чистого кода | [02:46] |
| **CDN Libraries** | Подключение внешних библиотек | [05:43] |
| **Dynamic Data** | Плейсхолдеры для параметров | [03:59] |

### Use Cases
- Кастомные UI элементы (календари, графики)
- Чаты и мессенджеры
- 3D визуализации (Three.js)
- Сложные формы с валидацией

### CDN Integration
```html
<!-- Подключение библиотеки через CDN -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/flatpickr/dist/flatpickr.min.css">
```
[05:43, 06:09]

---

## n8n Integration

### Building Chat Interface

**Структура чата на HTML:**
```html
<div class="chat-container">
  <!-- Messages Area -->
  <div id="messages" class="messages-area">
    <!-- Messages will appear here -->
  </div>
  
  <!-- Input Area -->
  <div class="input-area">
    <input type="text" id="message-input" placeholder="Type message...">
    <button id="send-btn">Send</button>
  </div>
</div>
```
[10:36]

### Отправка сообщения в n8n

```javascript
async function sendMessageToN8n(messageText) {
  const webhookUrl = '{{n8n_webhook_url}}'; // From NoCode-X parameter
  
  const response = await fetch(webhookUrl, {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify({
      message: messageText,
      user_id: '{{user_id}}',
      timestamp: new Date().toISOString()
    })
  });
  
  const data = await response.json();
  displayMessage(data.reply, 'bot');
}
```
[18:20]

### Инициализация чата

```javascript
document.addEventListener('DOMContentLoaded', () => {
  const sendBtn = document.getElementById('send-btn');
  const input = document.getElementById('message-input');
  
  // Send on button click
  sendBtn.addEventListener('click', () => {
    const message = input.value;
    if (message.trim()) {
      sendMessageToN8n(message);
      input.value = '';
    }
  });
  
  // Send on Enter key
  input.addEventListener('keypress', (e) => {
    if (e.key === 'Enter') {
      sendBtn.click();
    }
  });
});
```
[27:54]

---

## Configuration & Security

### Configuration Table

```
Table: mindshift_config
Fields:
- n8n_webhook_url (URL) - endpoint для n8n
- welcome_message (Text) - приветственное сообщение
- environment (Enum: development, production)
[36:02]
```

### Secret Fields

В NoCode-X можно пометить поле как **Secret**:
- ✅ Данные шифруются на уровне приложения
- ✅ Ведётся аудит изменений (кто, когда, что менял)
- ✅ Не отображаются в логах
[34:14]

```
Настройка:
1. Создать поле в Data Format
2. В настройках поля: Classification = "Secret"
3. NoCode-X автоматически включает шифрование
```

### Environments
- Development — для тестирования
- Production — для реальных пользователей
[36:16]

---

## State Management (Future)

**Анонсированная функция:**

```
State (Глобальное состояние):
- Доступно из любого экшена и шаблона
- Независимо от вложенности
- Обновление в одном месте → видно везде

Use cases:
- Обновление баланса после запроса в чате [21:20]
- Глобальные настройки приложения
- Состояние авторизации
- Тема оформления (dark/light)
```
[19:47]

---

## NoCode-X as Backend

**Video:** https://www.youtube.com/watch?v=FqrqaNdoVgc

### Project Goals
- Использование NoCode-X как полноценного бэкенда для фронтенда
- Аутентификация + API для внешних приложений

### Functional Blocks
- **Backend:** Data Format + API generation [01:43, 02:00]
- **Frontend:** React с OIDC библиотекой [03:27, 09:00]
- **Security:** Protected API + Access Tokens [17:55, 19:35]

### Technical Implementation

**NoCode-X Auth:** Workspace → Authentication [05:25]

**SPA Settings:** Не использовать Client Secret [07:42]

**Redirect URLs:** Доверенные URL для callback [12:08]

### React Integration

**OIDC Configuration:**
```javascript
const oidcConfig = {
  issuerId: 'your-workspace-id', // Unique workspace ID [10:33]
  clientId: 'your-client-id',
  homeUrl: 'http://localhost:3000/',
  redirectUri: 'http://localhost:3000/callback',
  // NO clientSecret for SPA!
};
```

**Environment Isolation:**
```javascript
// Development
const devConfig = {
  issuerId: 'nocode-x-dev-xxx',
  homeUrl: 'http://localhost:3000/'
};

// Production
const prodConfig = {
  issuerId: 'nocode-x-prod-yyy', // Different ID! [10:57]
  homeUrl: 'https://myapp.com/'
};
```

**Login Status Check:**
```javascript
import { useOidc } from '@axa-fr/react-oidc';

function App() {
  const { isAuthenticated } = useOidc();
  
  return (
    <div>
      {isAuthenticated ? (
        <Dashboard /> // Show content [14:22]
      ) : (
        <LoginButton /> // Show login
      )}
    </div>
  );
}
```

**API Call with Token:**
```javascript
async function fetchData() {
  // 1. Get token from OIDC
  const token = oidc.tokens.accessToken; // Bearer token [20:56]
  
  // 2. Call NoCode-X API
  const response = await fetch(
    'https://api.nocode-x.com/your-endpoint',
    {
      headers: {
        'Authorization': `Bearer ${token}`, // Secure! [19:35]
        'Content-Type': 'application/json'
      }
    }
  );
  
  const data = await response.json();
  return data;
}
```

### Architecture Overview

```
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│   React App     │────▶│   NoCode-X Auth  │     │   NoCode-X API  │
│   (Frontend)    │     │   (OIDC Server)  │     │   (Protected)   │
│                 │     │                  │     │                 │
│ - Login Button  │     │ - Custom UI      │     │ - Data Access   │
│ - API Calls     │     │ - Token Issuance │     │ - Business Logic│
│ - Token Storage │◀────│ - User Mgmt      │◀────│ - Database      │
└─────────────────┘     └──────────────────┘     └─────────────────┘
         │                                               ▲
         │         Authorization: Bearer <token>         │
         └───────────────────────────────────────────────┘
```

---

## Custom Auth Flows (OIDC)

### Custom Templates

NoCode-X позволяет полностью кастомизировать страницы аутентификации:

**Доступные для кастомизации страницы:**
- **Login Page** — страница входа
- **Registration Page** — страница регистрации
- **Reset Password Page** — восстановление пароля
- **Email Verification Page** — подтверждение email

**Как настроить:**
```
Workspace → Authentication → Templates
→ Select template to customize
→ Edit in Template Editor
```

**Преимущества:**
- ✅ Брендинг (логотип, цвета компании)
- ✅ Кастомные поля (дополнительные вопросы при регистрации)
- ✅ Локализация (перевод на нужный язык)
- ✅ React-приложение будет использовать ваш кастомный интерфейс [05:54]

### Identity Providers

Подключение внешних провайдеров аутентификации:

**Доступные провайдеры:**
- **Microsoft Entra ID** (Azure AD) — для корпоративных клиентов
- **Google** — Gmail/Google Workspace
- **LinkedIn** — для B2B приложений
- **GitHub** — для разработчиков
- **Apple** — Sign in with Apple (обязательно для iOS)

**Настройка:**
```
Workspace → Authentication → Identity Providers
→ Add Provider
→ Configure OAuth credentials
→ Map user attributes
```

**Поток:**
```
Пользователь → Кнопка "Sign in with Google"
→ Редирект на Google OAuth
→ Согласие на доступ
→ Редирект обратно в NoCode-X
→ Создание/обновление пользователя
→ JWT токен для доступа к API
```

### OIDC Configuration

**Настройки для Single Page Applications (SPA):**

```javascript
const oidcConfig = {
  // НЕ используйте Client Secret в браузере! [07:42]
  issuerId: 'your-workspace-id',
  clientId: 'your-client-id',
  redirectUri: 'https://yourapp.com/callback',
  responseType: 'token id_token',
  scope: 'openid profile email',
  
  // PKCE для безопасности (обязательно для SPA)
  usePKCE: true
};
```

**Важные эндпоинты:**
```
Authorization Endpoint: /oauth/authorize
Token Endpoint: /oauth/token
UserInfo Endpoint: /oauth/userinfo
Logout Endpoint: /oauth/logout
```

---

## Best Practices

### HTML Component Guidelines

```
✅ DO:
- Use for complex UI not available in standard widgets
- Connect libraries via CDN for advanced features
- Pass configuration via NoCode-X parameters
- Use Secret classification for API keys

❌ DON'T:
- Store API keys in plain text in code
- Hardcode URLs that change between environments
- Make the component too complex (hard to debug)
```

### Security Checklist

- [ ] API keys marked as Secret [34:05]
- [ ] Different configs for Dev/Prod environments
- [ ] Input validation in JavaScript
- [ ] HTTPS only for webhooks
- [ ] Audit log reviewed regularly

### Integration Checklist

- [ ] HTML component created with proper structure
- [ ] CSS styles applied
- [ ] JavaScript logic implemented
- [ ] CDN libraries loaded (if needed)
- [ ] Configuration table created
- [ ] Sensitive data marked as Secret
- [ ] On Load action fetches config
- [ ] Parameters passed to template
- [ ] n8n webhook tested
- [ ] Error handling implemented

### Backend Integration Checklist

**NoCode-X Backend:**
- [ ] Create Data Format for your entities [01:43]
- [ ] Generate test data
- [ ] Create API endpoint [02:00]
- [ ] Configure Authentication settings [05:25]
- [ ] Get issuerId (workspace ID) [10:33]
- [ ] Add Redirect URLs (localhost + production) [12:08]
- [ ] Set API to "Authentication required" [17:55]

**Frontend (React/Vue/Angular):**
- [ ] Install OIDC library (e.g., @axa-fr/react-oidc) [09:00]
- [ ] Configure OIDC with issuerId and clientId [10:33]
- [ ] Implement login/logout buttons
- [ ] Check auth status (isAuthenticated) [14:22]
- [ ] Get access token
- [ ] Add Bearer token to API calls [20:56]
- [ ] Handle token expiration

---

*Part of NoCode-X Skill | Video Tutorials: https://www.youtube.com/watch?v=LuaRbmWhmpM, https://www.youtube.com/watch?v=FqrqaNdoVgc*


### advanced-features.md
# NoCode-X: Advanced Features & Patterns

> Advanced topics: Vector databases, Telegram bots, payment systems, SaaS patterns

---

## Vector Database Integration (RAG, Semantic Search)

### Can NoCode-X Store Vectors Natively?

**No.** NoCode-X uses a traditional relational database, which is NOT optimized for high-dimensional vector operations.

**BUT** you can integrate external vector databases via HTTP API calls.

### Recommended Architecture

```
NoCode-X (logic) + Pinecone (vectors) + OpenAI (embeddings)
```

### Supported Vector Databases

| Database | Type | Integration | Best For |
|----------|------|-------------|----------|
| **Pinecone** | Managed SaaS | HTTP REST API | Production, scale |
| **Weaviate** | Self-hosted/Cloud | HTTP REST API | Flexibility, GraphQL |
| **Qdrant** | Self-hosted/Cloud | HTTP REST API | Open source, speed |
| **Supabase pgvector** | PostgreSQL extension | Via API | Simple setup |

### Use Cases

1. **Semantic Search** — Find documents by meaning, not keywords
2. **RAG (Retrieval-Augmented Generation)** — Feed relevant docs to LLM
3. **Recommendations** — "Similar to X" functionality
4. **Duplicate Detection** — Find similar images/text
5. **Knowledge Base** — AI-powered Q&A over documents

### Pinecone Integration Example

**Generate Embeddings:**
```bash
POST https://api.openai.com/v1/embeddings
Authorization: Bearer <OPENAI_API_KEY>

{
  "input": "Your text here",
  "model": "text-embedding-3-small"
}
```

**Store in Pinecone:**
```bash
POST https://<INDEX_HOST>/vectors/upsert
Api-Key: <PINECONE_API_KEY>

{
  "vectors": [{
    "id": "doc_123",
    "values": [0.0023, -0.0089, 0.1234, ...],
    "metadata": {
      "user_id": "user_456",
      "title": "Document Title"
    }
  }],
  "namespace": "user_456"
}
```

---

## Telegram Bot Integration

NoCode-X does NOT have a native Telegram node, but you can integrate using HTTP API calls.

### Architecture

```
User → Telegram Bot → NoCode-X API → Deepgram → Telegram Bot → User
```

### Setup

1. Create bot via @BotFather
2. Set up webhook in NoCode-X
3. Process voice messages

### Telegram API Endpoints

```bash
# Get file path
GET https://api.telegram.org/bot<TOKEN>/getFile?file_id=<FILE_ID>

# Download file
GET https://api.telegram.org/file/bot<TOKEN>/<file_path>

# Send message
POST https://api.telegram.org/bot<TOKEN>/sendMessage
{
  "chat_id": "<CHAT_ID>",
  "text": "<MESSAGE>"
}
```

### Deepgram Integration

```bash
POST https://api.deepgram.com/v1/listen?model=nova-3&smart_format=true
Authorization: Token <DEEPGRAM_API_KEY>
Content-Type: audio/ogg

# Response
{
  "results": {
    "channels": [{
      "alternatives": [{
        "transcript": "Hello, this is the transcribed text"
      }]
    }]
  }
}
```

### Voice Message Workflow

```
1. Receive webhook from Telegram
2. Get file_id from message
3. Download audio from Telegram
4. Send to Deepgram for transcription
5. Send result back to user
6. DELETE audio file (CRITICAL!)
```

---

## Payment Integration

### Available Integrations

| Integration | Type | Documentation |
|-------------|------|---------------|
| **Stripe** | Payment Gateway | Built-in |
| **Mailchimp** | Email Marketing | Via API |
| **MailJet** | Email Marketing | Via API |
| **YooKassa** | Payment (Russia/CIS) | Via HTTP API |

### Stripe (Native)

```
User → NoCode-X Page → Stripe Checkout → Webhook → Update user access
```

**Rocket Mode Prompt:**
```
Create a subscription system with:
- Stripe integration for payments
- Three tiers: Free, Pro ($9.99/month), Enterprise ($49/month)
- Subscription status tracking in database
- Webhook handler for payment.succeeded event
```

### YooKassa (via API)

**Create Payment:**
```bash
POST https://api.yookassa.ru/v3/payments
Authorization: Basic <BASIC_AUTH>

{
  "amount": {"value": "100.00", "currency": "RUB"},
  "payment_method_data": {"type": "bank_card"},
  "confirmation": {
    "type": "redirect",
    "return_url": "https://yoursite.com/success"
  },
  "metadata": {
    "user_id": "123",
    "order_id": "456"
  }
}
```

### Payment Database Schema (NoSQL)

```
users:
  - id: UUID
  - email: string
  - subscription_tier: enum (free, pro, enterprise)
  - subscription_status: enum (active, canceled, past_due)
  - credits_balance: integer

payments:
  - id: UUID
  - user_id: UUID (Reference)
  - amount: decimal
  - currency: string (RUB, USD, EUR)
  - status: enum (pending, succeeded, failed)
  - external_payment_id: string
```

---

## Credits & Tokens System

### Architecture

```
User Balance
  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
  │ Total       │  │ Used        │  │ Available   │
  │ Credits     │  │ Credits     │  │ = Total -   │
  └─────────────┘  └─────────────┘  └─────────────┘
```

### Credit Packages

| Package | Price | Credits | Price/Credit |
|---------|-------|---------|--------------|
| Starter | 99 ₽ | 100 | ~1 ₽ |
| Comfort | 599 ₽ | 1000 | ~0.6 ₽ |
| Maximum | 1999 ₽ | 5000 | ~0.4 ₽ |

### Credit Consumption Rules

| Feature | Cost (credits) | Calculation |
|---------|----------------|-------------|
| Voice Transcription | 1 | Per minute |
| AI Text Generation | 2-10 | Per 1000 tokens |
| Image Generation | 5-20 | Per image |
| API Call | 1 | Per request |

### Implementation Logic

```
1. Check balance ≥ cost BEFORE execution
2. Deduct credits (create pending transaction)
3. Execute action
4. Confirm transaction (or rollback on failure)
5. Notify user of balance update
```

---

## Complete SaaS Example

### Rocket Mode Prompt

```
Build a SaaS subscription system with:

1. USER MANAGEMENT:
   - Registration with email verification
   - Three subscription tiers with credit allowances
   - Credit balance system with purchase options

2. PAYMENT INTEGRATION:
   - Stripe integration for subscriptions
   - Credit package purchases (one-time)
   - Webhook handlers for payment events

3. CREDIT SYSTEM:
   - Daily credit allowance based on tier
   - Additional purchased credits
   - Credit consumption tracking per feature
   - Real-time balance display

4. FEATURES & LIMITS:
   - Free tier: limited usage
   - Pro tier: increased limits, priority support
   - Enterprise: unlimited, API access

5. NOTIFICATIONS:
   - Email when subscription renews
   - Warning at 20% daily limit
   - Alert when credits exhausted

6. ADMIN DASHBOARD:
   - View all users and their stats
   - Credit package management
   - Refund handling
```

---

## Troubleshooting

### Common Issues

**"Action not triggering"**
- Check if action is linked to a trigger
- Verify the action is not "dead"
- Check trigger conditions

**"API returns 401/403"**
- Verify API key in environment variables
- Check header format
- Ensure API key has permissions

**"Database query is slow"**
- Add indexes to frequently queried fields
- Use pagination for large datasets
- Avoid N+1 queries

**"Credits not deducting"**
- Check if credit check is BEFORE action execution
- Verify database transaction is committed
- Check if rollback occurs on error

---

## Security Best Practices

### Environment Variables
```
❌ NEVER: api_key = "sk_live_1234567890"
✅ ALWAYS: api_key = env.STRIPE_API_KEY
```

### Webhook Security
- Validate webhook signatures
- Use HTTPS-only webhook URLs
- Implement idempotency keys
- Log all webhook events

### File Upload Security
- Validate file types (whitelist)
- Scan uploads for malware
- Store files outside web root
- Generate random filenames

### Data Protection
- Encrypt sensitive data at rest
- Use HTTPS for all API communications
- Implement proper access controls
- Set data retention policies

---

## Server-side Code (Backend)

> ⚠️ **Beta/Planned Feature** — Проверьте актуальность в документации NoCode-X

### Возможности

NoCode-X планирует запуск исполнения кода на стороне сервера для сложной бизнес-логики, которую трудно реализовать визуальными нодами.

### Поддерживаемые языки

| Язык | Применение | Статус |
|------|------------|--------|
| **Python** | Data processing, ML, complex algorithms | Planned |
| **JavaScript** | API integrations, data transformations | Planned |

### Use Cases

**1. Сложные вычисления:**
```python
# Пример: Расчет сложной статистики
def calculate_user_metrics(data):
    """Calculate advanced user engagement metrics"""
    metrics = {
        'retention_rate': calculate_retention(data),
        'ltv': calculate_ltv(data),
        'churn_probability': predict_churn(data)
    }
    return metrics
```

**2. Интеграции с legacy-системами:**
```python
# Пример: Интеграция с ERP
import requests

def sync_with_erp(user_data):
    """Sync user data with corporate ERP"""
    response = requests.post(
        'https://erp.company.com/api/users',
        json=user_data,
        headers={'Authorization': f'Bearer {erp_token}'}
    )
    return response.json()
```

**3. Обработка файлов:**
```javascript
// Пример: Генерация PDF отчетов
const puppeteer = require('puppeteer');

async function generateReport(data) {
    const browser = await puppeteer.launch();
    const page = await browser.newPage();
    
    await page.setContent(createHTMLTemplate(data));
    const pdf = await page.pdf({ format: 'A4' });
    
    await browser.close();
    return pdf;
}
```

### Как использовать

**Вызов из Action:**
```
Action: Process Complex Logic
├─ Step 1: Prepare input data
├─ Step 2: Call Server Function
│   ├─ Function: calculate_metrics
│   ├─ Language: python
│   └─ Input: prepared_data
└─ Step 3: Process result
```

**Ограничения:**
- ⏱️ Timeout: 30 seconds per execution
- 📦 Memory: 512 MB per function
- 🔄 Concurrent: 10 parallel executions per app

### Безопасность

- Код выполняется в изолированном sandbox
- Нет доступа к файловой системе хоста
- Ограниченный network access (whitelist URLs)
- Автоматическое логирование всех вызовов

---

## Deployment Checklist

### Pre-Launch
- [ ] All API keys switched to production
- [ ] Webhook URLs point to production domain
- [ ] Database indexes created
- [ ] Error logging configured
- [ ] Backup strategy tested
- [ ] Rate limits enabled
- [ ] File size limits configured
- [ ] SSL certificate installed
- [ ] Terms of Service published
- [ ] Privacy Policy published

### Post-Launch
- [ ] Monitor error logs daily
- [ ] Check API rate limits
- [ ] Verify backup jobs running
- [ ] Review user feedback
- [ ] Monitor credit consumption

---

*Part of NoCode-X Skill*


---

## Guides

### PHASE-1-FULL.md
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



### PHASE-2-FULL.md
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



### APPSUMO-LTD-TIER-3.md
# AppSumo Lifetime Deal (LTD): License Tier 3

Resource limits and optimization strategies for AppSumo LTD users.

## Resource Limits

| Resource | Limit |
|----------|-------|
| **Developers** | 10 people |
| **CPU minutes** | 5,000/month |
| **Storage** | 100 GB |
| **Bandwidth** | 100 GB/month |
| **AI Credits** | 50,000 (one-time) |

## Included Features

All NoCode-X features included:
- Custom elements
- Hub components
- AI-assisted development
- Jobs/scheduler
- Full API capabilities
- Built-in database
- Media library
- Authentication & SSO
- Audit logging
- Encryption
- Custom domains
- DTAP/version management

## Optimization Strategies

### CPU Minutes
- Use caching
- Optimize database queries
- Implement pagination
- Schedule jobs during off-peak

### Storage
- Compress images
- Use external storage (S3)
- Archive old data
- Clean up unused media

### Bandwidth
- Enable CDN
- Compress assets
- Lazy loading
- Cache API responses

### AI Credits
- Use BYOK when available
- Cache AI responses
- Optimize prompts
- Use local models for simple tasks

## Detailed Documentation

Full documentation available in legacy file: `SKILL.md.legacy` (search for "AppSumo Lifetime Deal")

## Resources

- [Phase 1: Production](./PHASE-1-PRODUCTION.md)
- [Phase 2: Advanced](./PHASE-2-ADVANCED.md)
- [Platform Overview](../core/PLATFORM-OVERVIEW.md)


### INDEX.md
# Production & Advanced Guides

## Phase 1: Production-Ready Essentials

Complete guide for deploying production applications:

**File**: [PHASE-1-FULL.md](./PHASE-1-FULL.md) (818 lines)

### Contents:
1. **Jobs: Scheduled Automation**
   - Cron expressions
   - Frequency options
   - Common patterns

2. **Groups & Rights: RBAC**
   - Rights (technical privileges)
   - Roles (functional responsibilities)
   - Implementation steps

3. **Security**
   - Authentication (SSO, MFA)
   - Authorization
   - Auditability
   - Data protection
   - OWASP TOP 10 compliance

4. **Publishing & DTAP**
   - 4-stage pipeline (Dev → Test → Accept → Prod)
   - Version management
   - Environment promotion

## Phase 2: Advanced Features

Advanced platform features:

**File**: [PHASE-2-FULL.md](./PHASE-2-FULL.md) (1,669 lines)

### Contents:
1. **Design System**
   - Colors and tokens
   - Typography
   - Dark/Light mode

2. **Hub: Plugins & Integrations**
   - Public/Private Hub
   - Installing plugins
   - Creating plugins

3. **Testing**
   - Testing methods
   - Environment-based testing
   - Debugging with logs

4. **FAQ**
   - Getting started
   - Technical questions
   - Comparisons with other platforms
   - Vibe Coding philosophy

## AppSumo LTD Tier 3

Resource limits and optimization for LTD users:

**File**: [APPSUMO-LTD-TIER-3.md](./APPSUMO-LTD-TIER-3.md)

### Quick Reference:
- **CPU**: 5,000 minutes/month
- **Storage**: 100 GB
- **Bandwidth**: 100 GB/month
- **AI Credits**: 50,000 (one-time)

### Optimization strategies included

## Resources

- [Tutorials Index](../tutorials/INDEX.md)
- [Core Concepts](../core/)
- [Platform Overview](../core/PLATFORM-OVERVIEW.md)


---

## Tutorials

### MINDSHIFT-AUDIO-PART-1.md
## Tutorial: Building "Mindshift Audio" App (Part 1)

Video: https://www.youtube.com/watch?v=SBkcR7TvIkw

Complete step-by-step guide to building a mobile-first audio hypnotherapy application with AI-generated personalized content.

### 1. Project Concept [00:00]

**Idea:** Create a personalized audio self-help application for hypnotherapy sessions.

**Key Features:**
```
├─ AI-powered content generation based on user input
├─ Backend selects random background music (prevents habituation)
├─ Mobile-first responsive design
├─ Credit system for usage
├─ Custom audio player via HTML component
└─ Belief assessment system
```

**Architecture:**
```
Frontend (Mobile App UI)
        ↓
AI Processing (User input → Structured request)
        ↓
Backend (Generate audio + Random music selection)
        ↓
User receives unique personalized recording
```

### 2. Project Setup [03:43]

**Starting Fresh:**
```
Create New Application:
├─ Clean slate (no pre-built actions/templates)
├─ Mobile-first approach
└─ English language for international audience
```

**First Template: Login Page:**
```
Step 1: Create Template
├─ Name: "Login Page"
└─ Type: Authentication page

Step 2: Disable Authentication (Critical!)
Template Settings → Authentication Required: ❌ OFF
Why: Users can't access login page if auth is required
```

**Editor Navigation Tips:**
```
├─ Shift key: Toggle between selection and pan tools
├─ Ctrl + Scroll: Zoom in/out
├─ Space + Drag: Pan canvas
└─ 100% width/height: Full page containers
```

### 3. Design System Setup [07:38]

**Accessing Design System:**
```
Navigation: Design System tab

Benefits:
├─ Centralized color management
├─ Global typography control
├─ Automatic updates across all pages
└─ Brand consistency

Colors Defined:
├─ Primary: Main brand color
├─ Secondary: Accent color
├─ Background: Page background
├─ Surface: Cards, panels
└─ Text: Content colors
```

**Design Token Strategy:**
```
✅ DO: Use semantic names (Primary, not "Blue")
✅ DO: Set up Dark/Light mode variants
✅ DO: Test accessibility (contrast ratios)
✅ DO: Document color usage patterns
```

### 4. Login Page Layout [08:48]

**Container Structure:**
```
Root Container (Vertical List)
├─ Width: 100%
├─ Height: 100%
├─ Position: X=0, Y=0 (absolute)
└─ Alignment: Center (all items)

Child Elements:
├─ Logo (Image) - 70x70px, centered
├─ Title (Text) - "Welcome Back"
├─ Email Field (Input)
├─ Password Field (Input)
├─ Forgot Password (Link)
└─ Login Button (Primary action)
```

**Vertical vs Horizontal Lists:**
```
Vertical List:
├─ Elements stack top-to-bottom
├─ Use for: Forms, cards, content sections
└─ Spacing: Gap between items

Horizontal List:
├─ Elements side-by-side
├─ Use for: Navigation, button groups, headers
└─ Alignment: Left, center, right, space-between
```

**Input Fields:**
```
Label vs Placeholder:
├─ Label: Moves up when typing (floating)
├─ Placeholder: Disappears on input
└─ Recommendation: Use Labels for clarity

Configuration:
├─ Type: Email (for email validation)
├─ Type: Password (masked input)
├─ Required: Yes
└─ Style: Match design system
```

**Button Styling:**
```
Login Button:
├─ Text: "Login"
├─ Icon: Login icon (Google Font Icons)
├─ Border Radius: 12px (rounded corners)
├─ Background: Primary color
├─ Hover: Darker shade
└─ Full width on mobile
```

**Link Styling:**
```
Forgot Password Link:
├─ Font Size: 10px
├─ Color: Text secondary
├─ Alignment: Right

Hover State (On Hover):
├─ Text Decoration: Underline
├─ Cursor: Pointer (hand icon)
└─ Color: Primary (optional)
```

### 5. Login Logic Implementation [35:14]

**Workspace Configuration:**
```
Step 1: Go to Workspace Settings
Step 2: Select "Authentication" tab
Step 3: Choose your app for login handling
Step 4: Save configuration

Result: NoCode-X knows which app handles authentication
```

**Creating Login Action:**
```
Trigger: On Click (Login button)
Action Name: "Login"
Description: "Authenticates user with email and password"

Logic Flow:
1. Get value of field (Email)
   └─ Save to Variable Scope: "email"

2. Get value of field (Password)
   └─ Save to Variable Scope: "password"

3. Login function
   ├─ Email: {{email}}
   └─ Password: {{password}}

4. On Success → Route to Home Page
5. On Error → Show error message
```

**Variable Scope:**
```
Concept: Temporary storage during action execution

Structure (like a spreadsheet):
┌─────────────┬──────────────────┐
│ Name        │ Value            │
├─────────────┼──────────────────┤
│ email       │ user@example.com │
│ password    │ ********         │
│ user_id     │ 12345            │
└─────────────┴──────────────────┘

Usage:
├─ Store: Function results
├─ Pass: Between action steps
└─ Access: Via {{variable_name}}
```

**Naming Conventions:**
```
✅ GOOD Action Names:
├─ "Login User"
├─ "Validate Email Format"
├─ "Send Welcome Email"
└─ "Calculate Total Price"

❌ BAD Action Names:
├─ "Action 1"
├─ "Do stuff"
├─ "Process"
└─ "Handle click"

Why it matters:
├─ Clarity for future you
├─ Team collaboration
├─ AI assistant understanding
└─ Debugging and logs
```

### 6. Registration Page [01:03:23]

**Duplicating Template:**
```
Efficient approach:
1. Right-click "Login Page"
2. Select "Duplicate"
3. Rename to "Register"
4. Modify as needed

Benefits:
├─ Consistent styling
├─ Faster development
├─ Shared design patterns
└─ Easier maintenance
```

**Registration Fields:**
```
Additional Inputs:
├─ First Name (Text)
├─ Last Name (Text)
├─ Email (Email)
├─ Password (Password)
└─ Confirm Password (Password)
```

**Terms & Conditions:**
```
Layout: Horizontal List
├─ Slide Toggle (Checkbox)
│   └─ State: On/Off
├─ Text: "I agree to Terms of Service"
│   └─ Link to terms page

Logic:
├─ Toggle state stored in variable
├─ Registration blocked if not checked
└─ Show error: "Please accept terms"
```

**Email Verification Strategy:**
```
Option 1: Immediate verification
├─ User clicks link immediately
└─ Simpler flow

Option 2: Verification on first login (Recommended)
├─ Link sent after registration
├─ Valid for 10 minutes
├─ More secure (time-limited)
└─ Better UX (can explore first)

Configuration:
Settings → Authentication → Email Verification
```

### 7. Page Navigation [01:19:02]

**Internal Routing:**
```
Don't: Hard-code URLs
├─ Breaks when domain changes
├─ Difficult to maintain
└─ Not portable between environments

Do: Use Route to Page function
├─ Reference template by name
├─ Works across environments
├─ Maintains navigation history
└─ Automatic URL generation
```

**Implementing Navigation:**
```
From Login to Register:

1. Add On Click trigger to "Sign up" link
2. Create Action: "Go to Register"
3. Add function: Route to Page
4. Select Template: "Register"
5. Save and test

Implementation:
├─ Trigger: Click on "Sign up" link
├─ Action: Navigate to Register
├─ Method: Route to Page (Register)
└─ Result: URL updates, page loads
```

**Testing Navigation:**
```
Incognito Mode Testing:
├─ Tests clean session
├─ No cached data
├─ Simulates new user experience
└─ Catches auth issues early

Checklist:
├─ Login page loads without auth
├─ Click "Sign up" → Register page
├─ Register page loads correctly
├─ All elements styled properly
├─ Mobile responsive
└─ No console errors
```

### 8. Mobile-First Considerations

**Design Principles:**
```
Mobile-First Approach:
├─ Design for mobile screens first
├─ Progressive enhancement for desktop
├─ Touch-friendly targets (min 44px)
├─ Readable text (min 16px)
└─ Simplified navigation

Testing:
├─ Use browser dev tools (mobile view)
├─ Test on actual devices
├─ Check touch interactions
└─ Verify load times on mobile networks
```

**Responsive Patterns:**
```
Container Strategy:
├─ Max-width on desktop (centered)
├─ Full-width on mobile
├─ Padding adjustments
└─ Stack elements vertically on small screens

Typography:
├─ Scalable font sizes
├─ Readable line heights
├─ Adequate contrast
└─ Appropriate line lengths (45-75 chars)
```

### Best Practices from Tutorial

**Development Workflow:**
```
1. Plan structure (paper/wireframe)
2. Set up design system first
3. Build core templates
4. Implement logic incrementally
5. Test continuously
6. Iterate based on feedback
```

**Code Organization:**
```
✅ DO:
├─ Name everything clearly
├─ Group related elements
├─ Use consistent spacing
├─ Document complex logic
├─ Test edge cases
└─ Clean up unused elements

❌ DON'T:
├─ Leave default names
├─ Skip documentation
├─ Mix different patterns
├─ Ignore mobile view
├─ Forget error handling
└─ Rush to production
```

### Quick Mindshift Audio Checklist

**Part 1 Complete:**
- [ ] Project created (clean slate)
- [ ] Login page template created
- [ ] Authentication disabled on login page
- [ ] Design system configured
- [ ] Login form layout (logo, fields, button)
- [ ] Login action implemented
- [ ] Variable scope usage
- [ ] Registration page (duplicated + modified)
- [ ] Terms & conditions toggle
- [ ] Navigation between pages working
- [ ] Mobile responsive tested

**Part 2 Preview (Next Steps):**
- [x] Root template with navigation
- [x] Template hierarchy
- [x] Homepage with user greeting
- [x] Credit display
- [x] Consistency bar
- [x] Safety warnings
- [x] Part 3: Audio generation flow
- [x] Part 4: N8N chat integration
- [ ] Additional features (payments, advanced AI)

---



### MINDSHIFT-AUDIO-PART-2.md
## Tutorial: Building "Mindshift Audio" App (Part 2)

Video: https://www.youtube.com/watch?v=7iaPI0XaXkg

Continuing the mobile hypnotherapy app with template hierarchy, navigation, and homepage design.

### 1. Template Hierarchy Concept [00:07]

**Lesson Goals:**
```
Today's Plan:
├─ Create Homepage template
├─ Set up navigation structure
├─ Implement template hierarchy
└─ Begin audio generation (if time permits)
```

**Why Template Hierarchy Matters:**
```
❌ Without Hierarchy (Bad):
Each page duplicates:
├─ Navigation menu
├─ Header
├─ Footer
├─ Common styles
└─ Change needed? Update EVERY page!

✅ With Hierarchy (Good):
Root Template contains:
├─ Navigation (shared)
├─ Layout structure (shared)
├─ Common elements (shared)
└─ Changes apply to ALL child pages automatically
```

**Visual Structure:**
```
Root Template (Parent)
├─ Navigation Menu
├─ Header/Footer
└─ Content Area (dynamic)

Child Templates:
├─ Homepage ← Inherits Root + unique content
├─ New Session ← Inherits Root + unique content
└─ Session List ← Inherits Root + unique content
```

### 2. Creating Root Template (Navigation Structure) [05:47]

**Main Container Setup:**
```
Root Template Structure:

Vertical List (Main Container)
├─ Width: 100%
├─ Height: 100%
└─ Contains:
   ├─ Content Area (flexible)
   │  └─ Vertical List (grows to fill space)
   └─ Bottom Navigation
      └─ Horizontal List (fixed at bottom)
```

**Bottom Menu Design:**
```
Horizontal List (Bottom Navigation)
├─ Vertical Alignment: Bottom
├─ Height: Auto (fits content)
├─ Padding: Comfortable spacing
└─ Items: Icon buttons

Mobile UX Principle:
├─ Menu under thumbs (easy reach)
├─ Consistent across all pages
└─ Clear visual feedback
```

**Layout Configuration:**
```
Content Area:
├─ Flex Grow: Yes (takes remaining space)
├─ Overflow: Scroll (if content exceeds)
└─ Padding: Safe area margins

Bottom Navigation:
├─ Position: Sticky bottom
├─ Background: Solid color (content doesn't show through)
└─ Shadow: Subtle elevation
```

### 3. Custom SVG Icon Buttons [13:04]

**Creating Custom Buttons:**
```
Button Structure (Vertical List):
├─ Size: 60x60 pixels
├─ Border Radius: 25px (fully rounded)
├─ Background: Primary color
├─ Icon: SVG image (centered)
└─ Label: Text below (optional)

Why Custom vs Standard:
├─ Full control over styling
├─ Consistent sizing
├─ Custom animations
└─ Brand alignment
```

**SVG Integration:**

**Step 1: Get SVG Code**
```
Sources:
├─ Lucide icons (https://lucide.dev/)
├─ Heroicons (https://heroicons.com/)
├─ Font Awesome (SVG version)
└─ Custom designs

Example SVG:
<svg xmlns="http://www.w3.org/2000/svg" 
     width="24" height="24" 
     viewBox="0 0 24 24" 
     fill="none" 
     stroke="currentColor" 
     stroke-width="2">
  <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/>
  <polyline points="9 22 9 12 15 12 15 22"/>
</svg>
```

**Step 2: Make Color Dynamic**
```
Replace fixed colors with currentColor:

❌ Before (Fixed color):
stroke="#000000"
fill="#3B82F6"

✅ After (Dynamic):
stroke="currentColor"
fill="currentColor"

Benefit: Control color from NoCode-X Design System
```

**Step 3: Add to NoCode-X**
```
1. Create Image element
2. Select "SVG" option
3. Paste SVG code
4. Set Color: Uses Design System token
5. Size: Fit container or custom
```

**Menu Icons Setup:**
```
Bottom Navigation Items:
├─ Home (house icon)
│  └─ Route: Homepage
├─ New Session (plus/play icon)
│  └─ Route: New Session page
└─ List (list/history icon)
   └─ Route: Session List page

Each icon:
├─ Normal state: Primary color
├─ Active state: Highlighted
└─ Hover: Scale or opacity change
```

### 4. Navigation Logic [28:17]

**Setting Up Routes:**
```
For each menu button:

1. Add On Click trigger
2. Create Action: "Go to [Page]"
3. Function: Route to Page
4. Select: Target template
5. Test navigation

Example - Home Button:
Trigger: Click
Action: Navigate to Homepage
Route: Route to Page → Homepage
```

**Homepage Assignment:**
```
Critical Step:
1. Go to Application Settings
2. Find "Homepage" field
3. Select: "Homepage" template
4. Save

Result:
├─ Domain root (/) → Homepage
├─ "Play" button → Opens Homepage
└─ Default landing page set
```

### 5. Homepage Content Design [32:14]

**User Greeting:**
```
Text Element:
Content: "Welcome back, {{user.first_name}}"

Dynamic Data:
├─ Placeholder: {{user.first_name}}
├─ Source: Logged-in user data
└─ Fallback: "Guest" or empty

Styling:
├─ Font: Display/Heading size
├─ Weight: Bold
└─ Color: Text primary
```

**Credit Display Block:**
```
Structure (Horizontal List):
├─ Icon: Credit/coin icon
├─ Label: "Available Credits:"
└─ Value: {{user.credits}} (dynamic)

Design:
├─ Background: Card surface color
├─ Padding: 16px
├─ Border radius: 12px
└─ Shadow: Subtle elevation
```

**Responsive Grid Layout:**

**Challenge:** Show items side-by-side on tablet, stacked on phone

**Solution: Wrap + Min-Width**
```
Container: Horizontal List
├─ Wrap: Yes (Wrap to next line)
├─ Gap: 16px
└─ Items have Min-Width

Behavior:
Desktop/Tablet:
├─ Items fit side-by-side
└─ Stay in row

Mobile:
├─ Items exceed container width
├─ Min-width triggers wrap
└─ Stack vertically

Code Example:
├─ Item 1: Min-width 300px
├─ Item 2: Min-width 300px
└─ On phone (<600px): Stack
   On tablet (>600px): Side-by-side
```

### 6. Consistency Bar (Activity Indicator) [47:38]

**Concept:**
```
Visual indicator of user activity:
├─ Last 7 days activity
├─ Last 28 days activity
└─ Encourages regular usage
```

**Design Elements:**
```
Consistency Bar Structure:
├─ Title: "Your Consistency"
├─ Period Toggle: 7 days | 28 days
├─ Activity Visualization:
│  ├─ Grid of squares (like GitHub contributions)
│  ├─ Color intensity = activity level
│  └─ Tooltip on hover (date + details)
└─ Stats: Total sessions, streak

Period Selector Buttons:
├─ Font: Mulish (consistent)
├─ Active: Filled background
├─ Inactive: Outlined
└─ Hover: Slight scale or color change
```

**Implementation Options:**
```
Option 1: Grid of colored squares
├─ Each square = one day
├─ Color intensity = sessions count
└─ Simple, visual, motivating

Option 2: Progress bars
├─ Bar per week
├─ Fill percentage = completion
└─ Clear comparison

Option 3: Calendar view
├─ Mini calendar grid
├─ Checkmarks on active days
└─ Familiar interface
```

**Styling Period Buttons:**
```
Button States:

Normal (Inactive):
├─ Background: Transparent
├─ Border: 1px solid primary
├─ Text: Primary color
└─ Border radius: 8px

Active:
├─ Background: Primary color
├─ Border: 1px solid primary
├─ Text: White (on primary)
└─ Font weight: Bold

Hover:
├─ Scale: 1.05
├─ Shadow: Subtle elevation
└─ Transition: 200ms ease
```

### 7. Safety Warnings [55:17]

**Important for Hypnotherapy App:**
```
Safety Message:
"⚠️ Do not listen to generated audio while driving
or operating heavy machinery"

Purpose:
├─ User safety
├─ Legal protection
├─ Professional responsibility
└─ Regulatory compliance
```

**Design Implementation:**
```
Warning Banner:
├─ Background: Warning/Error color (subtle)
├─ Icon: Alert triangle
├─ Text: Clear, concise warning
├─ Position: Prominent but not intrusive
└─ Dismissible: Optional (user can close)

Visual Style:
├─ Left border accent (4px)
├─ Rounded corners (8px)
├─ Padding: 12-16px
└─ Font size: Small but readable
```

**Additional Warnings:**
```
Consider adding:
├─ Medical disclaimer
├─ Age restrictions
├─ Privacy notice
└─ Emergency contacts
```

### Part 2 Complete Architecture

**Template Hierarchy:**
```
Root Template
├─ Bottom Navigation (shared)
│  ├─ Home → Homepage
│  ├─ New Session → Session Page
│  └─ List → History Page
└─ Content Area (dynamic)

Homepage (Child of Root)
├─ Welcome message
├─ Credit display
├─ Consistency bar
└─ Safety warning
```

**Navigation Flow:**
```
User Login
    ↓
Homepage (greeting + dashboard)
    ↓
[Bottom Menu Navigation]
├─ Home (current)
├─ New Session (create audio)
└─ List (history)
```

### Best Practices from Part 2

**Template Organization:**
```
✅ DO:
├─ Create Root template first
├─ Define shared elements once
├─ Use meaningful template names
├─ Test hierarchy changes carefully
├─ Document parent-child relationships
└─ Keep Root template focused on layout

❌ DON'T:
├─ Duplicate navigation on each page
├─ Put unique content in Root
├─ Skip setting Homepage
├─ Ignore mobile navigation UX
└─ Forget to test all routes
```

**SVG Icon Tips:**
```
✅ DO:
├─ Use currentColor for flexibility
├─ Optimize SVG code (remove unnecessary)
├─ Consistent icon size
├─ Test on different backgrounds
└─ Keep stroke width consistent

❌ DON'T:
├─ Use fixed colors in SVG
├─ Oversized icons (waste space)
├─ Mix different icon styles
├─ Forget hover/active states
└─ Skip accessibility labels
```

**Responsive Design:**
```
✅ DO:
├─ Use Wrap for flexible grids
├─ Set min-width breakpoints
├─ Test on actual devices
├─ Consider thumb zones (mobile)
└─ Maintain touch target sizes (44px+)

❌ DON'T:
├─ Hard-code widths
├─ Ignore landscape orientation
├─ Make buttons too small
├─ Clutter mobile interface
└─ Forget safe areas (notch, home indicator)
```

### Quick Mindshift Audio Part 2 Checklist

**Root Template:**
- [ ] Root template created
- [ ] 100% width/height vertical list
- [ ] Bottom navigation (horizontal list)
- [ ] Content area (flexible)
- [ ] Menu aligned to bottom

**Navigation:**
- [ ] Custom icon buttons (60x60px, rounded)
- [ ] SVG icons with currentColor
- [ ] Three menu items (Home, New, List)
- [ ] Route actions configured
- [ ] Homepage assigned in settings

**Homepage Content:**
- [ ] Welcome message with user name
- [ ] Credit display block
- [ ] Consistency bar visualization
- [ ] Period toggle (7/28 days)
- [ ] Responsive layout (wrap + min-width)

**Safety:**
- [ ] Safety warning banner
- [ ] Appropriate warning color
- [ ] Clear message text

**Testing:**
- [ ] Navigation works between pages
- [ ] Root template applies to all children
- [ ] Mobile responsive (phone + tablet)
- [ ] Icons display correctly
- [ ] User data shows dynamically

**Part 3 Preview:**
- [x] Dynamic placeholders & Action Triggers
- [x] Conditionals & branching logic
- [x] User credits system (database)
- [x] Consistency calendar (activity tracking)
- [x] Template loops (For Loop)
- [x] 7 vs 28 days toggle

**Part 4 Preview:**
- [x] N8N integration
- [x] HTML Component chat
- [x] AI assistant setup

---



### MINDSHIFT-AUDIO-PART-3.md
## Tutorial: Building "Mindshift Audio" App (Part 3)

Video: https://www.youtube.com/watch?v=7iaPI0XaXkg&t=1s (Homepage Dynamic Content)

Setting up dynamic content on the homepage with placeholders, conditionals, database integration, and activity tracking calendar.

### 1. Placeholders & Action Triggers [00:06]

**Dynamic Header Setup:**
```
Replace static text with dynamic placeholders

Before: "Welcome back, User!"
After: "Welcome back, {{user_first_name}}!"
```

**OnLoad Action: populate welcoming header:**
```
Trigger: Page Load (OnLoad)
Action: Populate Welcoming Header

Logic:
1. Get current user data
2. Extract first_name from Variable Scope
3. Replace placeholder in title component

Result: Personalized greeting for each user
```

**Placeholder Syntax:**
```
Available placeholders:
├─ {{user.first_name}} - User's first name
├─ {{user.email}} - User's email
├─ {{user.id}} - User ID
├─ {{credits.balance}} - Credit balance
└─ Any template parameter or database field
```

### 2. Conditionals (Branching Logic) [05:58]

**Conditional Logic in Actions:**
```
Use Case: Show different messages based on user

Condition Block:
IF {{user.first_name}} == "Tristan"
├─ THEN: Show special welcome message
└─ ELSE: Show standard welcome

Implementation:
1. Add Condition block in Action
2. Set comparison operator (equals)
3. Define true/false branches
4. Different UI updates for each path
```

**Conditional UI Display:**
```
Show/Hide Elements Based on Conditions:

Example: Warning message for specific user
├─ Condition: user.email == "admin@example.com"
├─ True: Show warning banner
└─ False: Show standard greeting

Visual Result:
Different UI states without creating separate pages
```

**Practical Applications:**
```
✅ Show admin panel only for admins
✅ Display different content for premium users
✅ Hide features for free tier users
✅ Personalized onboarding flows
✅ Conditional form fields
```

### 3. User Credits System [15:25]

**Data Format: user_account:**
```
Fields:
├─ credits (Number) - Credit balance
└─ user_email (Email) - Link to user account

Purpose: Track user's available credits for audio generation
```

**Database Relationship:**
```
Linking Credits to User:

user_account table:
├─ user_email: "user@example.com" (unique identifier)
├─ credits: 150
└─ last_updated: timestamp

Current User:
├─ email: "user@example.com" (matching key)
├─ first_name: "John"
└─ id: "12345"

Connection: user_account.user_email = Current User.email
```

**OnLoad Action: Fetch User Credits:**
```
Action: Load User Credits
Trigger: Page Load

Step 1: Search one data record
├─ Data Format: user_account
├─ Filter: user_email = {{Current User.email}}
└─ Result: User's credit record

Step 2: Set template parameter
├─ Parameter: user_credits
├─ Value: {{Found Record.credits}}
└─ Now available as {{user_credits}} placeholder

Step 3: Update UI
├─ Replace placeholder in credit display
└─ Show: "Available Credits: {{user_credits}}"
```

### 4. Activity Tracking System [23:53]

**Data Format: listened_event:**
```
Purpose: Track each audio listening session

Fields:
├─ user_email (Email) - Who listened
├─ listened_date (DateTime) - When listened
└─ audio_id (Text) - Which audio

Benefits:
├─ User activity history
├─ Consistency tracking
├─ Analytics
└─ Gamification (streaks)
```

**Recording Activity:**
```
Action: Record Listening Event
Trigger: Click "Listen" button

Steps:
1. Create listened_event record
   ├─ user_email: {{Current User.email}}
   ├─ listened_date: {{Current DateTime}}
   └─ audio_id: {{Selected Audio ID}}

2. Update user credits (decrement)
   ├─ Get current credits
   ├─ Subtract 1
   └─ Save back to database

3. Refresh credit display
   └─ Execute "Load User Credits" action
```

### 5. Dynamic Consistency Calendar [27:49]

**Template Hierarchy for Calendar:**
```
Main Template (Homepage)
└─ Consistency Calendar Section
   └─ Template: consistency_template (reusable)
      ├─ Parameter: amount_of_days (7 or 28)
      └─ Generates day cells dynamically

Day Templates:
├─ active_day - Green/filled (activity recorded)
└─ non_active_day - Bordered (no activity)
```

**Creating Day Templates:**
```
Template: active_day
├─ Visual: Green background
├─ Icon: Checkmark
└─ Size: 40x40px rounded square

Template: non_active_day
├─ Visual: Transparent with border
├─ Icon: Empty or dot
└─ Same size for consistency
```

**For Loop Implementation:**
```
Action: Generate Calendar
Trigger: Page Load or Period Toggle

Loop: For i from 0 to (amount_of_days - 1)
├─ Calculate date: Today - i days
├─ Check database for listened_event
│  ├─ Filter: user_email = current user
│  └─ AND listened_date = calculated date
├─ IF record found:
│  └─ Add active_day template
└─ ELSE:
   └─ Add non_active_day template

Result: Visual calendar showing activity history
```

**Date Calculation Logic:**
```
For each day in loop:
├─ Day 0: Today (current date)
├─ Day 1: Today - 1 day (yesterday)
├─ Day 2: Today - 2 days
└─ Day N: Today - N days

Check: Does listened_event exist for this date?
├─ Yes → Active day (green)
└─ No → Inactive day (border)
```

### 6. Period Toggle (7 vs 28 Days) [01:11:52]

**Template Parameters:**
```
Template: consistency_template
Parameter: amount_of_days
Default: 7

Usage: Controls how many day cells to generate
```

**Toggle Implementation:**
```
Buttons:
├─ "7 Days" button
│  └─ On Click: Set parameter = 7
└─ "28 Days" button
   └─ On Click: Set parameter = 28

Action: Change Period
Steps:
1. Set value of template parameter
   ├─ Parameter: amount_of_days
   └─ Value: 7 or 28 (from button)

2. Execute "Generate Calendar" action
   └─ Re-renders with new count
```

**Responsive Layout:**
```
Challenge: 28 days in one row = too wide

Solution: Wrap property
Container: Horizontal List
├─ Wrap: Yes (elements wrap to next line)
├─ Min-width: 40px per day
└─ Result: Grid layout (4 rows × 7 days)

Visual:
┌─────────────────────┐
│ ○ ○ ○ ○ ○ ○ ○      │ ← Week 1
│ ● ● ● ○ ○ ○ ○      │ ← Week 2
│ ○ ○ ○ ○ ○ ○ ○      │ ← Week 3
│ ○ ○ ○ ○ ○ ○ ○      │ ← Week 4
└─────────────────────┘
● = Active day (listened)
○ = Inactive day
```

**Button Styling:**
```
Active Period Button:
├─ Background: Primary color
├─ Text: White
└─ Bold font

Inactive Period Button:
├─ Background: Transparent
├─ Border: 1px solid primary
└─ Text: Primary color
```

### Complete Part 3 Flow

**User Journey:**
```
1. Login → Homepage loads
2. OnLoad Actions execute:
   ├─ Populate user name ({{first_name}})
   ├─ Load credit balance
   └─ Generate consistency calendar
3. User sees:
   ├─ "Welcome back, John!"
   ├─ "Credits: 150"
   └─ Activity calendar (7 or 28 days)
4. User clicks "28 Days"
   └─ Calendar re-renders with 28 days
5. User clicks "Listen"
   ├─ Activity recorded in database
   ├─ Credit decremented
   └─ Calendar updates (today becomes active)
```

### Best Practices from Part 3

**Database Design:**
```
✅ DO:
├─ Use email as unique identifier
├─ Separate data formats for different purposes
├─ Track timestamps for analytics
├─ Link data via matching fields
└─ Index frequently queried fields

❌ DON'T:
├─ Store credits in user profile (mix concerns)
├─ Use user ID if email is more practical
├─ Forget to set up relationships
└─ Ignore data validation
```

**Dynamic Content:**
```
✅ DO:
├─ Use OnLoad for initial data fetch
├─ Combine placeholders with static text
├─ Refresh data after actions
├─ Show loading states
└─ Handle empty/null data gracefully

❌ DON'T:
├─ Hard-code user-specific data
├─ Skip error handling
├─ Overload single action
└─ Ignore performance (too many queries)
```

**Template Reusability:**
```
✅ DO:
├─ Create small, focused templates
├─ Use parameters for customization
├─ Build component libraries
├─ Document template purposes
└─ Test in isolation

❌ DON'T:
├─ Create monolithic templates
├─ Skip parameter documentation
├─ Duplicate similar templates
├─ Ignore parent-child relationships
```

### Quick Mindshift Audio Part 3 Checklist

**Placeholders & Actions:**
- [ ] User greeting with {{first_name}} placeholder
- [ ] OnLoad action created
- [ ] Replace placeholders function configured
- [ ] Test with different users

**Conditionals:**
- [ ] Condition block added
- [ ] True/false branches configured
- [ ] UI updates for each case
- [ ] Test with different conditions

**Credits System:**
- [ ] user_account data format created
- [ ] credits field (Number)
- [ ] user_email field (Email)
- [ ] OnLoad action to fetch credits
- [ ] Credit display on homepage

**Activity Tracking:**
- [ ] listened_event data format created
- [ ] Fields: user_email, listened_date, audio_id
- [ ] Action to record listening
- [ ] Credit decrement logic

**Consistency Calendar:**
- [ ] consistency_template created
- [ ] active_day template (green)
- [ ] non_active_day template (bordered)
- [ ] For Loop to generate days
- [ ] Date calculation logic
- [ ] Database check for each day
- [ ] Template switching (active/inactive)

**Period Toggle:**
- [ ] amount_of_days parameter
- [ ] 7 Days button
- [ ] 28 Days button
- [ ] Toggle actions
- [ ] Wrap layout for grid
- [ ] Visual feedback (active button state)

---



### MINDSHIFT-AUDIO-PART-4.md
## Tutorial: Building "Mindshift Audio" App (Part 4)

Video: https://www.youtube.com/watch?v=kR2hC0Lp4aA (N8N Integration)

Integrating N8N AI assistant via HTML Component with secure configuration management.

### 1. HTML Component Overview [00:06]

**The Power of HTML Component:**
```
NoCode-X HTML Component allows:
├─ Pure HTML markup
├─ External JavaScript (CDN)
├─ External CSS (CDN)
├─ Custom JavaScript execution
├─ Pre-load and Post-load scripts
└─ Placeholder substitution from database

Use Cases:
├─ Custom chat interfaces
├─ Advanced calendars
├─ Data visualizations (D3.js, Chart.js)
├─ Third-party widgets
├─ Complex interactive components
└─ N8N agent integration
```

**Script Execution Timing:**
```
Before Component Load:
├─ Setup code
├─ Configuration variables
└─ Library initialization

After Component Load:
├─ DOM manipulation
├─ Event listeners
├─ Dynamic content
└─ API calls
```

**Placeholder System:**
```
Dynamic Data Injection:

HTML/JS Code:
"Welcome {{user.first_name}}!"

NoCode-X substitutes:
├─ {{user.first_name}} → "John"
├─ {{user.id}} → "12345"
├─ {{config.n8n_url}} → "https://..."
└─ Any template parameter or database value

Security:
├─ Automatic escaping
├─ XSS protection
└─ Safe substitution
```

### 2. Chat Interface Structure [09:37]

**HTML Layout:**
```html
<!-- Chat Container -->
<div id="chat-container">
  <!-- Message Area -->
  <div id="message-area">
    <!-- Messages appear here -->
  </div>
  
  <!-- Input Area -->
  <div id="input-area">
    <input type="text" id="chat-input" placeholder="Type message...">
    <button id="send-button">Send</button>
  </div>
</div>
```

**CSS Styling:**
```css
/* Container */
#chat-container {
  display: flex;
  flex-direction: column;
  height: 100%;
  background: {{design.surface_color}};
}

/* Message Area */
#message-area {
  flex: 1;
  overflow-y: auto;
  padding: 16px;
}

/* Input Area */
#input-area {
  display: flex;
  padding: 12px;
  border-top: 1px solid {{design.border_color}};
}

#chat-input {
  flex: 1;
  padding: 12px;
  border: 1px solid {{design.border_color}};
  border-radius: 8px;
}

#send-button {
  margin-left: 8px;
  padding: 12px 24px;
  background: {{design.primary_color}};
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}
```

**Dynamic Colors via Placeholders:**
```
Benefits:
├─ Consistent with Design System
├─ Automatic theme switching (Light/Dark)
├─ Single source of truth
└─ No hard-coded values
```

### 3. JavaScript Logic for N8N [16:50]

**Core Functions:**

**addMessage():**
```javascript
function addMessage(text, sender) {
  const messageArea = document.getElementById('message-area');
  const messageDiv = document.createElement('div');
  
  messageDiv.className = `message ${sender}`;
  messageDiv.textContent = text;
  
  messageArea.appendChild(messageDiv);
  messageArea.scrollTop = messageArea.scrollHeight;
}
```

**sendMessageToN8N():**
```javascript
async function sendMessageToN8N(message) {
  const n8nWebhookUrl = '{{config.n8n_url}}';
  const userId = '{{user.id}}';
  
  try {
    const response = await fetch(n8nWebhookUrl, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        message: message,
        user_id: userId,
        timestamp: new Date().toISOString()
      })
    });
    
    const data = await response.json();
    
    if (data.response) {
      addMessage(data.response, 'agent');
    }
  } catch (error) {
    console.error('Error:', error);
    addMessage('Sorry, something went wrong.', 'system');
  }
}
```

**Event Listeners:**
```javascript
document.addEventListener('DOMContentLoaded', function() {
  const sendButton = document.getElementById('send-button');
  const chatInput = document.getElementById('chat-input');
  
  // Send on button click
  sendButton.addEventListener('click', function() {
    const message = chatInput.value.trim();
    if (message) {
      addMessage(message, 'user');
      sendMessageToN8N(message);
      chatInput.value = '';
    }
  });
  
  // Send on Enter key
  chatInput.addEventListener('keypress', function(e) {
    if (e.key === 'Enter') {
      sendButton.click();
    }
  });
  
  // Show welcome message
  addMessage('{{config.welcome_message}}', 'agent');
});
```

### 4. Secure Configuration (Secrets) [32:31]

**Data Format: Mindshift Config:**
```
Purpose: Store sensitive configuration

Fields:
├─ n8n_webhook_url (Secret)
├─ welcome_message (Text)
├─ max_tokens (Number)
└─ model_version (Text)
```

**Secret Field Benefits:**
```
When "Secret" enabled:

Encryption:
├─ Application-level encryption
├─ Master keys in separate database
├─ Keys encrypted with another layer
└─ Even DB breach = encrypted noise

Audit Trail:
├─ Who changed the value
├─ When it was changed
├─ Previous values (versioning)
└─ IP address and context

Environment Separation:
├─ Dev environment: Dev webhook URL
├─ Prod environment: Prod webhook URL
└─ Automatic switching per environment
```

**Setting Up Secret:**
```
Step 1: Create Data Format
├─ Name: "Mindshift Config"
├─ Field: "n8n_url"
├─ Type: Text
└─ Secret: ✅ ENABLED

Step 2: Add Configuration Record
├─ Go to Data section
├─ Create new record
├─ Enter N8N webhook URL
└─ Save (automatically encrypted)
```

### 5. OnLoad Action for Configuration [37:03]

**Action: fetchChatConfiguration:**
```
Trigger: On Load (Chat page)
Name: "Fetch Chat Configuration"

Logic Flow:

Step 1: Search config record
Function: Search one data record
├─ Data Format: Mindshift Config
├─ Filter: Active = true
└─ Result: Config object

Step 2: Set template parameters
Function: Set value of template parameter
├─ Parameter: n8n_url
├─ Value: {{Config.n8n_url}}
└─ Secret: Automatically decrypted

Step 3: Set user parameters
Function: Set value of template parameter
├─ Parameter: user_id
├─ Value: {{Current User.ID}}

Step 4: Set welcome message
Function: Set value of template parameter
├─ Parameter: welcome_message
└─ Value: {{Config.welcome_message}}
```

**Parameter Flow:**
```
Database (Encrypted)
       ↓
On Load Action
       ↓
Template Parameters
       ↓
HTML Component Placeholders
       ↓
JavaScript Variables
```

### 6. Testing the Integration [45:50]

**Verification Steps:**
```
1. Page loads
   ├─ On Load action executes
   ├─ Parameters populated
   ├─ Welcome message appears
   └─ No console errors

2. User sends message
   ├─ Message appears in chat
   ├─ POST request to N8N
   ├─ Loading indicator (optional)
   └─ Response received

3. Agent responds
   ├─ N8N processes message
   ├─ AI generates response
   ├─ Response displayed in chat
   └─ Context maintained
```

**Expected Behavior:**
```
User: "Hello"
Agent: "Hi! I'm your Mindshift assistant. 
       What area of your life or business 
       would you like to work on today?"

User: "I want to improve my confidence"
Agent: "Great choice! Let's explore what 
       specific situations trigger your 
       confidence challenges..."
```

**Troubleshooting:**
```
Issue: No welcome message
Check:
├─ On Load action enabled?
├─ Config record exists?
├─ Placeholder syntax correct?
└─ Check Application Logs

Issue: Messages not sending
Check:
├─ N8N URL correct?
├─ Webhook active in N8N?
├─ CORS configured?
└─ Network tab for errors

Issue: No agent response
Check:
├─ N8N workflow running?
├─ AI node configured?
├─ Response format correct?
└─ N8N execution logs
```

### Best Practices for N8N Integration

**Security:**
```
✅ DO:
├─ Store webhook URLs as Secrets
├─ Use HTTPS only
├─ Validate all inputs
├─ Implement rate limiting
├─ Monitor API calls
└─ Rotate credentials periodically

❌ DON'T:
├─ Hard-code URLs in JavaScript
├─ Expose API keys
├─ Skip input validation
├─ Ignore error handling
└─ Log sensitive data
```

**Performance:**
```
✅ DO:
├─ Show loading indicators
├─ Implement timeouts
├─ Cache responses when appropriate
├─ Optimize N8N workflow
├─ Use CDN for static assets
└─ Minimize HTML component size

❌ DON'T:
├─ Block UI during requests
├─ Make synchronous calls
├─ Ignore slow connections
├─ Load unnecessary libraries
└─ Forget to debounce inputs
```

**UX:**
```
✅ DO:
├─ Clear visual feedback
├─ Typing indicators
├─ Message timestamps
├─ Error messages in UI
├─ Retry mechanisms
└─ Context preservation

❌ DON'T:
├─ Silent failures
├─ Confusing error messages
├─ Lost context on refresh
├─ Unclear agent vs user messages
└─ No indication of processing
```

### Quick Mindshift Audio Part 4 Checklist

**HTML Component:**
- [ ] Chat page template created
- [ ] HTML Component added
- [ ] Chat structure (container, messages, input)
- [ ] CSS styling with placeholders
- [ ] JavaScript functions (addMessage, sendMessage)
- [ ] Event listeners (click, Enter key)
- [ ] Placeholders for dynamic data

**Configuration:**
- [ ] Mindshift Config data format created
- [ ] n8n_url field marked as Secret
- [ ] Config record with webhook URL
- [ ] Welcome message configured

**Action Setup:**
- [ ] On Load action created
- [ ] Search config record step
- [ ] Set template parameters (URL, user, message)
- [ ] Action tested in development

**Integration:**
- [ ] N8N workflow created
- [ ] Webhook node configured
- [ ] AI agent node added
- [ ] Response format set
- [ ] Testing completed

**Security:**
- [ ] Secret field enabled
- [ ] HTTPS enforced
- [ ] Input validation
- [ ] Error handling
- [ ] Audit trail verified

---

**Note:** NoCode-X is actively evolving. Check the official documentation for the latest features and updates.


### CRM-PART-1-EMAIL.md
## Part 1 (CRM Series): AI Integration for Email Automation

Video: https://www.youtube.com/watch?v=g22GjR6RDjk

### 1. Project Goals

**Main Goal:** Add AI functionality to the CRM system for generating personalized client emails.

**Key Tasks:**
- Configure data transfer for selected user into template parameters
- Implement LLM (Large Language Model) request using client context and their needs
- Process and display structured AI response in the interface

### 2. Functional Blocks

**Template Parameters Setup:**
- Create `selected_row` variable (object) that stores clicked row data [10:54]
- This makes client data available to the generation button

**Input Interface:**
- Add text field for describing client needs (customer needs)
- Add generation button [13:53]

**AI Integration:**
- Configure **LLM completion request** action to form OpenAI request [28:07]
- Can use built-in AI credits or your own API token

**JSON Parsing:**
- Extract specific field (email body) from LLM JSON response [45:53]
- Convert JSON string to object for easy field access

**Dynamic UI:**
- Initially hide result text field (Style → Hidden)
- Show field only after receiving AI response [40:20]
- Configure `Fit content` and `Overflow Y: Visible` for auto-resizing [52:27]

### 3. Technical Implementation

**State Management (Template Parameters):**

To make selected client data available to the generation button, store it in template "memory":

```
Event: Click on table row
Action: Set value of template parameter

Parameter: selected_row
Value: Row Data (the entire row object)
```
[17:58]

**AI Prompt Construction:**

System Prompt (sets AI role and format):
```
You are a Sales Assistant. 
Generate a personalized email based on client information.
Return response STRICTLY in JSON format:
{
  "subject": "email subject line",
  "email_body": "full email text",
  "tone": "professional/friendly"
}
```
[32:11]

User Prompt (dynamic with placeholders):
```
Hi, I am writing to {{first_name}} from {{country}}. 
Their needs are: {{needs}}
```
[29:08]

**Processing AI Response:**

Step 1: LLM returns JSON string
```
Action: LLM completion request
├─ Model: GPT-4 (or built-in)
├─ System Prompt: [role definition]
├─ User Prompt: [dynamic with placeholders]
└─ Output: JSON text string
```

Step 2: Convert String to Object
```
Action: Convert string to object
Input: {{LLM response}}
Output: Structured object
```
[46:10]

Step 3: Create Data Format for easy access
```
Data Format: AI_Response
Fields:
- subject (Text)
- email_body (Text)  
- tone (Text)
```
[47:14]

Step 4: Display result
```
Action: Set value of input field
Target: AI result text field
Source: {{AI_Response.email_body}}
```

Step 5: Show hidden element
```
Action: Show element
Target: AI result text field
```
[40:20]

**Action Chain Sequence:**
```
1. LLM completion request → Get AI response
2. Convert string to object → Parse JSON
3. Create object from data format → Structure data
4. Set value of input field → Display email body
5. Show element → Reveal result field
```

### 4. Important Development Tips

**Using NoCode-X AI Credits:**
```
Option A: Use built-in tokens (no API key needed)
Option B: Insert your own OpenAI API token

⚠️ Built-in credits are convenient for prototyping
```
[33:48]

**Structured Responses:**
```
✅ GOOD: Always ask AI to return JSON
   Benefits:
   - Automate next steps (API calls, database updates)
   - Extract specific fields easily
   - Enable conditional logic based on response

❌ BAD: Just display raw AI text
   Limitations:
   - Manual processing required
   - No automation possible
   - Unpredictable format
```
[32:57]

**Debugging with Application Logs:**
```
If AI returns errors:
1. Go to Application Logs
2. Check full request/response text
3. Look for formatting errors
4. Verify JSON structure
```
[22:05]

### Best Practices

**Data vs Object:**
```
Object  → Pure data (JSON)
         Example: {"name": "John", "country": "USA"}

Data    → Database record with metadata
         Includes: created_at, ID, updated_at, etc.
```
[11:59]

**Column Visibility:**
```
To hide ID in table but use it in logic:
1. Name column code exactly as DB field (e.g., "ID")
2. Uncheck "Visible" checkbox
3. ID remains available for logic but hidden from users
```
[09:45]

**Dynamic UI Pattern:**
```
1. Create result field (Style → Hidden)
2. Placeholder for AI output
3. On generation complete → Show element action
4. Field appears with content
```

### Common Patterns

**Pattern: AI Email Generator:**
```
User Flow:
1. Click client row → selected_row populated
2. Enter needs in text field
3. Click Generate button
4. AI processes: client data + needs → email
5. Result field appears with generated email
6. User can edit and send
```

**Pattern: Structured AI Response:**
```
Prompt Engineering:
├─ System prompt: Define role + output format
├─ User prompt: Dynamic data with placeholders
└─ Required: Always specify JSON structure

Post-Processing:
1. Convert string to object
2. Create data format matching JSON structure
3. Access fields via dot notation
4. Use in subsequent actions
```

### Quick AI Integration Checklist

**Setup:**
- [ ] Create `selected_row` template parameter (object type)
- [ ] Configure row click handler to set selected_row
- [ ] Add needs input field
- [ ] Add generation button
- [ ] Create hidden result field (Style → Hidden)

**AI Configuration:**
- [ ] Create system prompt (role + JSON format requirement)
- [ ] Create user prompt with placeholders for client data
- [ ] Configure LLM completion request action
- [ ] Test prompt in AI Playground if available

**Response Handling:**
- [ ] Add "Convert string to object" action
- [ ] Create data format matching AI JSON response
- [ ] Configure field mapping (AI fields → UI fields)
- [ ] Add "Show element" action for result field
- [ ] Set result field to auto-resize (Fit content + Overflow Y: Visible)

**Testing:**
- [ ] Test with sample client data
- [ ] Check Application Logs for errors
- [ ] Verify JSON parsing works correctly
- [ ] Test edge cases (empty fields, special characters)
- [ ] Validate email format and content quality

---



### CRM-PART-2-UPDATE.md
## Part 2 (CRM Series): Update Operation (CRUD - Edit Profile)

Video: https://www.youtube.com/watch?v=ewPwyMr9YNo

### 1. Project Goals

**Main Goal:** Implement the profile editing process and save changes to the database (the "U" in CRUD).

**Key Tasks:**
- Hide detail panel by default and show only when user is selected
- Unlock input fields when "Edit" button is clicked
- Collect modified data and update database record when "Save Changes" is clicked

### 2. UI Logic (Interface Management)

**Dynamic Panel Display:**
```
Initial State:
├─ Profile detail panel: Hidden (Style → Hidden)
└─ Trigger: onclick on table row

Action: Show element
└─ Target: Profile detail panel
```
[02:19]

**Edit Mode:**
```
Initial State:
├─ Input fields: Disabled (read-only view)
└─ Edit button: Visible

On Edit Click:
├─ Enable input fields (Enable input fields)
├─ Enable save button (Enable button)
└─ Enable cancel button
```
[05:13]

### 3. Backend Logic (Update Process)

Updating records in NoCode-X is a multi-step process requiring precision:

**Step 1: Get Record ID**
```
Source: Template parameter selected_row
Extract: ID field

Action: Get value from template parameter
Parameter: selected_row
Field: ID
```
[19:15]

**Step 2: Find Current Record**
```
Action: Search one data record
Criteria: ID = {{selected_row.ID}}
Result: Current database record
```
[17:47]

**Step 3: Create Copy (Payload)**
```
Action: Create/update object
├─ Copy all fields from found record
├─ This becomes the "update payload"
└─ Preserve original data structure
```
[22:08]

**Step 4: Modify Values**
```
Action: Update an object
Target: The payload object
Changes:
├─ country = {{country_input.value}}
├─ first_name = {{first_name_input.value}}
└─ last_name = {{last_name_input.value}}
```
[22:42]

**Step 5: Save to Database**
```
Action: Update a data record
├─ Data Format: User
├─ Record ID: {{selected_row.ID}}
└─ Body: {{updated_payload_object}}
```
[24:27]

**Step 6: Visual Feedback**
```
Action: Disable input fields
Action: Disable save button
Result: Visual confirmation that changes saved
```
[24:45]

**Complete Action Chain:**
```
Event: Click "Save Changes"

1. Get ID from selected_row
2. Search for current record by ID
3. Create copy object from record
4. Update copy with new field values
5. Save updated object to database
6. Disable fields (visual feedback)
7. Show success message (optional)
```

### 4. Important Implementation Tips

**Using Record ID:**
```
✅ GOOD: Use ID for record matching
   - Unique, never changes
   - Fast database lookup
   - Reliable for updates

Implementation:
1. Add ID column to table
2. Make it hidden if needed
3. Always include in row data
4. Use in search/update actions
```
[09:45]

**Data Caching:**
```
⚠️ WARNING: Browser caches database views

After updating record:
→ Click "Refresh Data" in database panel
→ Browser may show stale data otherwise
→ Always refresh to see latest version
```
[28:06]

**Template Parameters for State:**
```
Use Template Parameters to share state:
├─ selected_row: Currently selected user
├─ is_editing: Edit mode flag (optional)
└─ Any other page-level variables

Benefits:
- Accessible to all buttons on page
- Persists during page session
- Clean separation of concerns
```
[16:08]

### Best Practices

**Name Structure Handling:**
```
Scenario: Database stores first/last separately
          UI shows combined name

Option A (Workaround):
→ Parse combined name on save
→ Split into first/last
→ Risk: Ambiguous parsing

Option B (Better):
→ Separate input fields for first/last
→ Clear mapping to database
→ Better data structure
```
[12:10]

**User Feedback Pattern:**
```
After Save:
1. Disable all input fields
2. Disable save button
3. Show success notification
4. Update table data (refresh)

This signals: "Changes saved, view updated"
```
[24:45]

**Defensive Programming:**
```
Always validate before update:
├─ Check ID exists
├─ Verify record found
├─ Validate input data
└─ Handle errors gracefully
```

### Common Patterns

**Pattern: Edit-Save-Cancel Flow:**
```
Initial State:
├─ Fields disabled
├─ Edit button visible
└─ Save/Cancel hidden

On Edit:
├─ Enable fields
├─ Hide Edit button
└─ Show Save & Cancel

On Save:
├─ Update database
├─ Disable fields
├─ Show Edit button
└─ Hide Save & Cancel

On Cancel:
├─ Revert to original values
├─ Disable fields
├─ Show Edit button
└─ Hide Save & Cancel
```

**Pattern: Optimistic Updates:**
```
1. Update UI immediately
2. Send update to backend
3. If error → rollback UI
4. If success → keep changes

Benefits:
- Faster perceived performance
- Better UX
- Requires error handling
```

### Quick CRUD Update Checklist

**UI Setup:**
- [ ] Detail panel hidden by default
- [ ] Show element on row click
- [ ] Input fields initially disabled
- [ ] Edit button visible by default
- [ ] Save/Cancel buttons hidden initially

**Logic Setup:**
- [ ] Template parameter selected_row (object type)
- [ ] Row click handler to set selected_row
- [ ] Edit button: Enable inputs + toggle buttons
- [ ] Cancel button: Revert values + disable inputs

**Save Action Chain:**
- [ ] Get ID from selected_row parameter
- [ ] Search one data record by ID
- [ ] Create object from record (copy)
- [ ] Update object with new field values
- [ ] Update data record in database
- [ ] Disable inputs (visual feedback)
- [ ] Refresh table data (optional)

**Testing:**
- [ ] Test edit → save flow
- [ ] Test edit → cancel flow
- [ ] Verify database updates
- [ ] Check ID is correctly used
- [ ] Test with edge cases (empty fields)
- [ ] Verify visual feedback works

---



### CRM-PART-3-REFACTORING.md
## Part 3 (CRM Series): UI Refactoring & Data Synchronization

Video: https://www.youtube.com/watch?v=iiKW0qK8mVM

### 1. Project Goals

**Main Goal:** Improve the data update process (Update) in the CRM system through UI refactoring and table synchronization.

**Key Tasks:**
- Split "Full Name" field into two separate inputs: "First Name" and "Last Name" for structured storage [01:00]
- Implement synchronous Data Table update immediately after saving changes
- Demonstrate action refactoring process to support new fields

### 2. Functional Blocks

**UI Refactoring:**
- Replace single name input with two separate fields (First Name, Last Name) [10:29]

**Save Logic Update:**
- Read values from both new fields
- Overwrite corresponding object properties in database (payload.first_name, payload.last_name) [16:43]

**Table Synchronization:**
- Automatically reload data into table immediately after successful save [18:21]

### 3. Technical Implementation

**Working with Split Fields:**

Previously used unreliable RegEx to split full name string [06:18]:
```
❌ BAD: RegEx pattern on combined name
   - Fragile parsing
   - Edge cases (middle names, hyphenated names)
   - Data quality issues
```

New approach with separate fields [23:18]:
```
✅ GOOD: Direct field mapping
   
Row Click Handler:
├─ Set value: first_name_input = row_data.first_name
└─ Set value: last_name_input = row_data.last_name
```

**Complex Object Update:**
```
Action: Update an object
Target: payload
Fields to update:
├─ first_name = {{first_name_input.value}}
├─ last_name = {{last_name_input.value}}
├─ country = {{country_dropdown.value}}
└─ lead_source = {{lead_source_input.value}}
```
[15:28]

⚠️ **Critical:** Field names must exactly match JSON object property names in database [16:31]

**Table Refresh via Execute Action:**

To show changes in list immediately after clicking "Save":

```
Action Chain on Save:

1. Get ID from selected_row
2. Search one data record
3. Create/update object (copy)
4. Update object with new values
5. Update data record
6. Disable inputs
7. ⭐ Execute Action ← NEW STEP
   ├─ Action: Load CRM Data (onload action)
   └─ Execution: Synchronously
```
[19:50]

**Critical Setting - Clear Data Table:**
```
In "Load CRM Data" action:
Function: Add list of objects to data table
├─ Clear data table: TRUE ⭐
└─ Why: Ensures full refresh, not append

❌ Clear: False → Appends new rows to existing (duplicates!)
✅ Clear: True → Wipes table, loads fresh data
```
[19:02]

**Synchronous vs Asynchronous:**
```
Execute Action Mode:
├─ Synchronously: Wait for completion before next step
└─ Asynchronously: Continue immediately, run in background

For table refresh:
→ Use Synchronously
→ Guarantees updated data before UI updates
→ Prevents race conditions
```
[20:24]

### 4. Important Development Tips

**Caching During Debug:**
```
⚠️ Always click "Refresh Data" in database admin panel
→ Interface may show stale cached data
→ Browser caches database views
→ Force refresh to see latest changes
```
[28:06]

**Logic Abstraction:**
```
Extract reusable actions:
├─ "Load CRM Data" → Called from:
│  ├─ Page onload
│  ├─ After save
│  └─ After delete
└─ Benefits:
   - Single source of truth
   - Consistent data loading
   - Easy maintenance
```
[19:30]

**Naming Conventions for Speed:**
```
✅ GOOD: Prefix input fields
detail_field_first_name
detail_field_last_name
detail_dropdown_country

Benefits:
- Easy search in element picker
- Group related elements
- Faster development
```
[13:29]

**NoCode-X Terminology:**
```
Actions = Flows = Logic Chains
Think of them as:
├─ Business logic containers
├─ Reusable workflows
└─ Event handlers

An action can:
├─ Respond to triggers (click, load, API call)
├─ Execute other actions
└─ Contain conditional logic
```
[12:50]

### Best Practices

**Field Naming Alignment:**
```
Database Field     UI Element Code          Action Reference
─────────────────────────────────────────────────────────────
first_name    →    detail_field_first_name  →  first_name
last_name     →    detail_field_last_name   →  last_name
country       →    detail_dropdown_country  →  country
```

**Complete Save & Refresh Pattern:**
```
Save Action:
1. Validate inputs (optional)
2. Get record ID
3. Fetch current record
4. Create payload object
5. Update all fields in payload
6. Save to database
7. Disable edit mode
8. ⭐ Execute "Load Data" action (Sync)
9. Show success notification
```

**Avoiding Common Mistakes:**
```
❌ Don't: Append to table without clearing
   → Creates duplicate rows

❌ Don't: Use async execution for dependent actions
   → Race conditions, stale data

❌ Don't: Manually split combined names
   → Use separate fields from start

✅ Do: Always clear table before reload
✅ Do: Use sync execution for data dependencies
✅ Do: Structure data properly in database
```

### Common Patterns

**Pattern: Master-Detail with Live Sync:**
```
User Flow:
1. Click row → Load details
2. Click Edit → Enable fields
3. Modify data → Click Save
4. Save to DB → Refresh table
5. See updated data immediately

Implementation:
├─ Table: Shows all records
├─ Detail Panel: Edits selected record
├─ Save Action: Updates DB + refreshes table
└─ Result: Seamless UX
```

**Pattern: Reusable Data Loading:**
```
Action: "Load CRM Data"
Trigger: None (called by other actions)

Steps:
1. Clear data table
2. Fetch all records
3. Add to data table
4. Apply filters (optional)

Called from:
├─ Page onload
├─ After create
├─ After update
└─ After delete
```

### Quick Refactoring & Sync Checklist

**UI Refactoring:**
- [ ] Replace combined field with separate inputs
- [ ] Update element naming convention (prefix)
- [ ] Update row click handler to set both fields
- [ ] Test individual field loading

**Logic Updates:**
- [ ] Update "Update an object" with new fields
- [ ] Verify field names match database JSON
- [ ] Test save with new field structure
- [ ] Verify data saves correctly

**Table Synchronization:**
- [ ] Create/extract "Load Data" action
- [ ] Set "Clear data table" to TRUE
- [ ] Add "Execute Action" at end of save
- [ ] Set execution to Synchronously
- [ ] Test: Edit → Save → See changes in table

**Optimization:**
- [ ] Review naming conventions
- [ ] Extract reusable actions
- [ ] Add loading states (optional)
- [ ] Test edge cases (empty fields, long names)

---



### CRM-PART-4-CRUD.md
## Part 4 (CRM Series): Create & Delete Operations (Complete CRUD)

Video: http://www.youtube.com/watch?v=DTcI8okVEjw

### 1. Implementation of Create Function

Adding a new user in NoCode-X is implemented through creating an empty record followed by editing:

**Create Button:**
```
Element: Icon button (create_user)
Location: Top of dashboard
Style: Primary/Brand
```
[03:08]

**Data Creation Action:**
```
Action: Create User

Step 1: Create data
├─ Data Format: User
├─ Name: {{Unique Identifier}} ← UUID for uniqueness
└─ Fields: Empty (will be filled after creation)
```
[07:30]

**Handling Required Fields:**
```
Problem: Database fields set to Nullable: False
Result: Cannot create empty record → Error

Solution for Prototype:
├─ Set Required: False
└─ Set Nullable: True

⚠️ Note: For production, implement proper validation
```
[09:28]

**Sorting for Convenience:**
```
Problem: New empty row gets lost at bottom of list

Solution: Sort by Last Name on Load
├─ Empty values appear at top
├─ Easy to find and edit new records
└─ Natural alphabetical order for filled records

Implementation:
Action: Load CRM Data (On Load)
└─ Sort by: last_name (Ascending)
```
[12:23]

**Complete Create Flow:**
```
User Flow:
1. Click "Create" button
2. Empty record created with UUID name
3. Table refreshes (empty row at top)
4. User clicks new row
5. Detail panel opens with empty fields
6. User fills data and saves
7. Record updated with real values
```

### 2. Implementation of Delete Function

Deleting records happens through the detail panel of selected user:

**Delete Button:**
```
Element: Button
Style: Error (red color)
Location: Detail panel footer
Icon: Trash/Delete icon
```
[16:08]

**Delete Logic:**

**Step 1: Extract ID from Metadata**
```
Action: Get value from object
Source: {{selected_row}}
Key: ID
Result: Record identifier

⚠️ Important: ID is metadata, not in payload!
```
[17:31]

**Step 2: Delete from Database**
```
Action: Delete a data record
├─ Data Format: User
└─ Record ID: {{ID from step 1}}

Result: Permanent deletion
```
[21:16]

**Step 3: Refresh UI**
```
Action: Execute Action
├─ Action: Load CRM Data (onload)
├─ Mode: Synchronously
└─ Result: Deleted user disappears from table
```
[21:24]

**Complete Delete Flow:**
```
Action Chain: Delete User

1. Get ID from selected_row (metadata)
2. Delete data record by ID
3. Execute "Load CRM Data" action
4. Detail panel hides (optional)
5. Show success notification (optional)
```

### 3. Important Technical Details

**Metadata vs Payload:**
```
Object Structure:
┌─────────────────────────────────────┐
│  METADATA          │  PAYLOAD       │
├─────────────────────────────────────┤
│  • ID              │  • first_name  │
│  • Created At      │  • last_name   │
│  • Updated At      │  • country     │
│  • Created By      │  • lead_source │
│  • Version         │  • Custom      │
│                    │    fields      │
└─────────────────────────────────────┘

Access:
├─ Metadata: Get value from object → Key: "ID"
└─ Payload: Direct field access ({{object.field}})
```
[17:58]

**ID Access Issue:**
```
Problem: ID not visible in variable scope/Scope list
Reason: ID is metadata, not payload content

Solution:
Function: Get value from object
Object: {{selected_row}}
Key: "ID" (type manually)
```

**UI Synchronization:**
```
Rule: Any data change requires table refresh

Apply to:
├─ Create → Refresh table
├─ Update → Refresh table
└─ Delete → Refresh table

Implementation:
Execute Action → "Load CRM Data"
(Clear: True, Sync: True)
```
[21:24]

**Debugging Common Errors:**
```
Error: "value argument was null"
Causes:
├─ Blocks not connected in action
├─ Missing source object
├─ Empty variable reference
└─ Wrong field name

Fix: Check Application Logs for exact location
```
[22:02]

### Best Practices

**Record Status Pattern:**
```
For new users, automatically set status:

Action: Create User
├─ Create data (empty)
├─ Update object immediately
│  └─ status = "New" or "Draft"
└─ Save with status

Benefits:
- Distinguish incomplete profiles
- Filter by status in table
- Workflow management
```

**Delete Confirmation Pattern:**
```
For production apps, add confirmation:

Flow:
1. Click Delete
2. Show confirmation popup
   ├─ "Are you sure?"
   ├─ Cancel button
   └─ Confirm Delete button
3. Only on confirm → Execute delete

Implementation:
├─ Modal/Popup component
├─ Pass selected_row to popup
└─ Delete action inside popup
```

**Complete CRUD Architecture:**
```
CRUD Operations in CRM:
┌──────────────────────────────────────────┐
│  C - Create   │  Create data + UUID      │
│  R - Read     │  Load data + Display     │
│  U - Update   │  Update record + Refresh │
│  D - Delete   │  Delete + Refresh        │
└──────────────────────────────────────────┘

Shared Pattern:
All operations → Execute "Load CRM Data"
(Clear: True, Sync: True)
```

### Common Patterns

**Pattern: Full CRUD Dashboard:**
```
Components:
├─ Data Table (list view)
├─ Detail Panel (edit view)
├─ Create Button (top toolbar)
├─ Edit Button (detail panel)
├─ Save Button (detail panel)
├─ Delete Button (detail panel)
└─ Refresh Button (optional)

Actions:
├─ On Load: Load CRM Data
├─ Create: Create + Refresh
├─ Update: Update + Refresh
└─ Delete: Delete + Refresh
```

**Pattern: Draft State Management:**
```
New Records:
1. Create with UUID name
2. Auto-set status = "Draft"
3. User edits in detail panel
4. On save → status = "Active"
5. Filter table to hide drafts (optional)
```

**Pattern: Soft Delete (Advanced):**
```
Instead of hard delete:
1. Add "deleted" boolean field
2. Add "deleted_at" timestamp
3. "Delete" sets these fields
4. Filter table: deleted = false
5. Keep data for recovery
```

### Complete CRUD Checklist

**Create Implementation:**
- [ ] Add create button (top of dashboard)
- [ ] Create "Create User" action
- [ ] Use UUID for unique naming
- [ ] Set Required: False, Nullable: True (prototype)
- [ ] Add sort by last_name (On Load)
- [ ] Test: Click create → See empty row at top
- [ ] Execute "Load CRM Data" after create

**Delete Implementation:**
- [ ] Add delete button (detail panel, Error style)
- [ ] Create "Delete User" action
- [ ] Get ID from selected_row metadata
- [ ] Delete data record by ID
- [ ] Execute "Load CRM Data" after delete
- [ ] Test: Delete → Row disappears from table

**UI Polish:**
- [ ] Add loading states
- [ ] Show success notifications
- [ ] Consider delete confirmation popup
- [ ] Handle empty states (no users)
- [ ] Add status field for new records
- [ ] Test all CRUD operations end-to-end

**Production Considerations:**
- [ ] Add validation for required fields
- [ ] Implement delete confirmation
- [ ] Add error handling
- [ ] Consider audit logging
- [ ] Add bulk operations (optional)

---



### CRM-PART-14-DASHBOARD.md
 ## Part 14: CRM Dashboard (AI-Generated)
 
 Video: http://www.youtube.com/watch?v=NCROc3uob68
 
 ### 1. Project Goals
 
 **Main Goal:** Build a functional CRM dashboard prototype in one session.
 
 **Key Tasks:**
 - Generate page design with AI
 - Set up data structure for users with test records
 - Implement data loading into Data Table
 - Interactive detail view: Update user info in side panel on row click [00:44]
 
 ### 2. Functional Blocks
 
 **AI Generation:**
 - Use text prompt to create dashboard layout with table and details window [02:00]
 
 **Data Structure:**
 ```
 Data Format: User
 Fields:
 - first_name (Text)
 - last_name (Text)
 - gender (Enum)
 - lead_source (Text)
 - profile_photo (Image URL)
 - country (Text)
 ```
 [05:14]
 
 **Test Data:**
 - Generate 5 random users for testing [09:47]
 
 **Data Binding:**
 - Display data in text fields and image component [28:12]
 
 ### 3. Technical Implementation
 
 **Container Hierarchy:**
 ```
 Main Container: Horizontal List
 ├─ Left Panel (50%): Data Table
 └─ Right Panel (50%): User Details
 ```
 [15:01]
 
 **Layout Settings:**
 - Use "Space between" to align elements to edges [13:42]
 
 **Loading Data (On Load):**
 ```
 Action: Load Users
 
 Step 1: Fetch a list of data records
 └─ Get all users from database [17:50]
 
 Step 2: Add list of objects to data table
 └─ Populate table with fetched data [19:26]
 
 ⚠️ Important: Delete default rows and columns first! [22:01]
 ```
 
 **Row Click Handler (On Click):**
 ```
 Event: On Click on table row
 Parameters automatically created:
 - Row Code (ID of clicked row)
 - Row Data (object with row data) [28:32]
 
 Action: Update Detail View
 
 Step 1: Configure Row Data parameter
 ├─ Switch from Free Input to Parameter Input
 ├─ Define fields: first_name, last_name, country, etc.
 └─ This tells NoCode-X the data structure [32:35]
 
 Step 2: Update UI elements
 ├─ Set value of input field (for form elements)
 ├─ Set text on text element (for layout elements)
 └─ Use Row Data fields as source [38:20]
 ```
 
 **Combining Strings:**
 ```
 Function: Replace placeholders
 Text field: "{{first_name}} {{last_name}}"
 
 Result: "John Smith" (combined from two fields)
 ```
 [41:39]
 
 ### 4. Important Development Tips
 
 **Media Library:**
 ```
 Upload images via Media section
 Each photo gets a URL
 Store URL in user's profile_photo field
 ```
 [46:55]
 
 **Debugging with Logs:**
 ```
 Function: Write to application log
 Use to check what data is passed on click
 Best way to debug data flow
 ```
 [31:39]
 
 **Element Types:**
 ```
 Know the difference:
 - Form elements (input fields) → Use "Set value of input field"
 - Layout elements (text blocks) → Use "Set text on text element"
 ```
 [38:10]
 
 ### Best Practices
 
 **⚠️ Don't Click Auto-Layout:**
 ```
 Never click "Arrange blocks hierarchically" in action editor
 Unless you want your carefully placed blocks to be rearranged!
 ```
 [39:18]
 
 **Centering the Canvas:**
 ```
 If screen goes black when navigating to template:
 → Click "eye" icon → "Center"
 → Returns canvas to center of view
 ```
 [24:51]
 
 **Row Data Configuration:**
 ```
 ❌ Bad: Leave Row Data as "Free Input"
 ✅ Good: Switch to "Parameter Input" and define structure
 
 Why: NoCode-X needs to know field names to show them in dropdowns
 ```
 [32:35]
 
 ### Common Patterns
 
 **Pattern: Master-Detail View**
 ```
 Left side: Data Table (list of records)
 Right side: Details panel (selected record info)
 
 Interaction:
 1. Click row in table
 2. Row Data captured automatically
 3. Details panel updated with selected user data
 ```
 
 **Pattern: Editable Profile**
 ```
 Right panel contains:
 - Profile photo (image)
 - Name fields (inputs)
 - Country (dropdown)
 - Save button
 
 On Save: Update database record
 ```
 
 ### Quick CRM Dashboard Checklist
 
 **Design:**
 - [ ] Generate layout with AI prompt
 - [ ] Set up Horizontal List container
 - [ ] Configure left/right panels
 - [ ] Add Data Table to left panel
 - [ ] Add detail components to right panel
 
 **Data:**
 - [ ] Create User Data Format
 - [ ] Generate test data (5+ users)
 - [ ] Upload profile photos to Media
 - [ ] Add photo URLs to user records
 
 **Logic:**
 - [ ] On Load: Fetch and populate table
 - [ ] Delete default table rows/columns
 - [ ] On Row Click: Capture Row Data
 - [ ] Configure Row Data structure
 - [ ] Update detail fields from Row Data
 - [ ] Test with Write to log
 
 **Polish:**
 - [ ] Use Replace placeholders for combined fields
 - [ ] Add loading states
 - [ ] Test all interactions
 - [ ] Check mobile responsiveness
 
---



### PART-7-AUTHENTICATION.md
## Part 7: Authentication & Custom Login Pages

Video: https://www.youtube.com/watch?v=mR3dXcyO-R4

### 1. Enabling Authentication

**Goal:** Require authentication for accessing application or specific pages.

**Page-level Protection:**
```
Template Editor → Settings → Authentication required = true
```
[01:28]

**Global Protection via Template Hierarchy:**
```
Root Template → Authentication required = true
  └─ All Child Templates inherit protection automatically
```
[03:18]

**Best Practice:**
```
❌ Bad: Enable auth on every page manually
✅ Good: Enable once in Root Template

Result: All new pages automatically protected, no security holes
```

### 2. User Management

**User Types:**
- **Developers** — Build the application
- **Users** — Use the application
[04:08]

**Creating Users (Manual):**

| Setting | Description |
|---------|-------------|
| **Verified email** | Mark email as already confirmed |
| **Temporary password** | Force password change on first login |
| **MFA** | Require OTP (Google Authenticator) |
| **WebAuthn** | Biometric auth (Face ID, fingerprint, USB tokens) |
[05:49, 06:29]

### 3. Custom Login Page (Vanilla Login Plugin)

**Installation:**
```
Hub → Search "Vanilla Login" → Install
```
[09:25]

**What you get:**
- Login page template
- Registration page template
- Password reset template
- Email verification template
- All logic pre-built!

**Customization:**
```
Edit templates like regular pages:
- Change colors
- Modify button radius
- Add your logo
- Adjust layout
```
[10:35]

**Activation:**
```
Company Settings → Authentication
→ Set custom templates:
  - Login: My Custom Login Template
  - Register: My Custom Register Template
  - Reset Password: My Custom Reset Template
```
[12:35]

### 4. Logout Implementation

**Simple as:**
```
Button: "Logout"
On Click → Execute Action: Logout

That's it! [15:05]
```

### Best Practices

**Security Hierarchy:**
```
Always configure base security in Root Template:
✅ Prevents accidental unprotected pages
✅ New pages automatically inherit protection
✅ Single point of control
```

**Use Plugins for Speed:**
```
Don't build login forms from scratch:
✅ Install Vanilla Login (5 minutes)
✅ Customize for your brand
✅ Get all auth flows working immediately

Time saved: 3-4 hours of development
```

**MFA Recommendation:**
```
For critical applications:
✅ Enable MFA/WebAuthn at account creation
✅ Recommend Google Authenticator
✅ Support Face ID / fingerprint on mobile

Security level: Enterprise-grade
```

### Security Checklist

- [ ] Root Template has "Authentication required"
- [ ] All pages inherit protection (check Child Templates)
- [ ] Vanilla Login plugin installed and customized
- [ ] Custom templates activated in Company Settings
- [ ] MFA/WebAuthn enabled for admin accounts
- [ ] Logout button implemented
- [ ] Password reset flow tested
- [ ] Email verification working

---



### PART-8-DATA-TABLES.md
## Part 8: Data Tables (Master-Detail Interface)

Video: http://www.youtube.com/watch?v=ElP1CFe6iRQ

### 1. Data Table Features

**Визуализация данных:**
- Табличный вид с заголовками и строками
- Сортировка (Sort) по любой колонке
- Поиск/фильтрация (Filter)
- Пагинация (Paging) для больших данных [00:21]

**Стилизация:**
- Границы, отступы, тени
- Шрифты и цвета
- Эффекты при наведении (Hover) [06:13]

**Скрытые колонки:**
```
Можно создать колонку "ID" (не видна пользователю)
Используется для логики (например, переход к деталям)
[05:30]
```

### 2. Dynamic Table Management (Actions)

**Доступные функции:**

| Function | Description | Timestamp |
|----------|-------------|-----------|
| **Add Column** | Добавить колонку динамически | [08:27] |
| **Enable/Disable Filter** | Включить/выключить поиск | [09:24] |
| **Enable/Disable Paging** | Включить/выключить пагинацию | [09:24] |
| **Assign Data to Cell** | Заполнить конкретную ячейку | [12:20] |
| **Clear Rows** | Очистить все данные | [45:11] |

### 3. Loading Data from Database

**Алгоритм загрузки:**

**Step 1: Fetch Data**
```
Action: Load Persons
├─ Step 1: Fetch a list of data records (from Data Format)
│   └─ Result: List of persons with ID, Name, Email, etc.
└─ Step 2: Process each record
```
[17:45]

**Step 2: Loop Through Records**
```
For Each: person in fetched_list
  └─ Add Row to Data Table
      ├─ Row Code: person.ID (уникальный идентификатор) [23:12]
      ├─ First Name: person.first_name
      ├─ Last Name: person.last_name
      └─ Email: person.email
```
[19:47, 22:14]

**Важно:**
```
❌ Bad: Использовать индекс строки как Row Code
✅ Good: Использовать ID записи из базы данных

Почему: ID уникален и не меняется при сортировке/фильтрации
```
[23:12]

### 4. Master-Detail Interface

**Сценарий:** Таблица → Клик → Страница деталей

**Step 1: On Click Event**
```
Data Table Event: On Click
Parameters automatically available:
- Row Code (ID строки)
- Column Code (какая колонка кликнута)
- Row Data (все данные строки)
```
[26:13]

**Step 2: Action Parameters**
```
Action: Open Person Details
Parameters (Input):
- ID (UUID)
- First Name (Text)
- Last Name (Text)
- Email (Email)

Source: Row Data from table [32:35]
```

**Step 3: Navigation**
```
Action: Navigate to Details
├─ Step 1: Route to page "Person Details"
│   └─ URL Parameter: id = {{ID}}
└─ Step 2: Pass all row data
```
[41:17]

**Step 4: Detail Page**
```
Page: Person Details
Trigger: On Load

Action: Load Details
├─ Step 1: Get URL parameter "id"
├─ Step 2: Fetch one data record WHERE id = URL.id
└─ Step 3: Display person details
```
[37:31]

### 5. Best Practices

**Naming:**
```
❌ Bad: Table, Column1, Column2
✅ Good: PersonsTable, FirstNameColumn, EmailColumn

Почему: Легче понять логику при настройке [54:35]
```

**Case Sensitivity:**
```
❌ Bad: person.FIRST_NAME или person.first_Name
✅ Good: person.first_name (точно как в Data Format)

Почему: Поля чувствительны к регистру [39:37]
```

**Performance:**
```
При загрузке данных:
✅ Используйте пагинацию на уровне БД
✅ Limit: 50-100 записей за раз
❌ Не загружайте тысячи записей сразу

Почему: Не перегружайте интерфейс [18:02]
```

### Common Patterns

**Pattern 1: Simple List**
```
On Load:
1. Fetch list (limit 50)
2. For Each → Add Row
3. Enable Filter + Paging
```

**Pattern 2: Master-Detail**
```
On Load:
1. Fetch list
2. For Each → Add Row

On Row Click:
1. Get Row Code (ID)
2. Route to Detail Page with ID

Detail Page On Load:
1. Get ID from URL
2. Fetch one record
3. Display details
```

**Pattern 3: Editable Table**
```
On Load:
1. Fetch data
2. For Each → Add Row with editable cells

On Cell Change:
1. Get Row Code + Column Code
2. Update database record
3. Refresh table
```

---



### PART-9-OPENAI-CHATBOT.md
## Part 9: OpenAI Chatbot (LLM Wrapper)

Video: http://www.youtube.com/watch?v=DyrJvtozQW0

### 1. Setup Requirements

**Prerequisites:**
- ✅ NoCode-X account (free)
- ✅ OpenAI account + API token [01:25]

**Required Plugins:**

| Plugin | Purpose | Install |
|--------|---------|---------|
| **OpenAI Integration** | Connect to GPT models | Hub → OpenAI Integration [00:58] |
| **Vanilla Chatbot** | Ready-made chat UI components | Hub → Vanilla Chatbot [01:19] |

### 2. API Configuration

**Create OpenAI Config:**
```
Data Format: openai_config
Fields:
- api_token (Text, Secret) ← Your OpenAI API key
- model (Enum: gpt-3.5-turbo, gpt-4) ← Model selection
- temperature (Number, default: 0.7) ← Creativity level
```
[01:44]

### 3. Chat Interface (Templates)

**Vanilla Chatbot provides:**

**Chat Bubbles:**
- Incoming messages (bot)
- Outgoing messages (user)
- Fully customizable: colors, fonts, avatars [02:17]

**Chat Component:**
- Message input field
- Send button
- Messages list (Vertical List)
- Scrollable container [03:06]

### 4. Message Sending Logic

**Action: Send Message**

```
Trigger: On Click (Send Button)

Step 1: Get Value
├─ Get text from input field
└─ Clear input field [05:42]

Step 2: Display User Message
└─ Add message bubble to list (outgoing) [06:13]

Step 3: Show Typing Indicator
└─ Add "Bot is typing..." animation [06:42]

Step 4: Fetch AI Answer (ASYNC)
├─ Call OpenAI API with user message
├─ Mode: Asynchronous with front-end answer [08:12]
└─ Wait for response
[07:44]

Step 5: Display Bot Response
├─ Remove typing indicator
├─ Extract: choices[0].message.content [15:17]
└─ Add bot message bubble to list [16:23]
```

### 5. OpenAI API Integration

**Fetch Answer Action Configuration:**

```
API: OpenAI Chat Completions
Endpoint: https://api.openai.com/v1/chat/completions

Headers:
Authorization: Bearer {{config.api_token}}
Content-Type: application/json

Body:
{
  "model": "gpt-3.5-turbo",
  "messages": [
    {
      "role": "user",
      "content": "{{user_message}}"
    }
  ],
  "temperature": 0.7
}
```
[13:01, 13:34]

**Response Processing:**
```
Response structure:
{
  "choices": [
    {
      "message": {
        "role": "assistant",
        "content": "Bot's response text"
      }
    }
  ]
}

Extract: choices[0].message.content
[15:17]
```

### 6. Advanced Features & Customization

**Not Just Text:**
```
Bot can respond with:
✅ Images (image URLs)
✅ Videos
✅ Buttons (quick replies)
✅ Forms (collect data)
✅ Cards (rich content)
```
[18:38]

**Embed Anywhere:**
```
Any NoCode-X chatbot can be embedded:
→ External websites
→ Web applications
→ Mobile apps (via WebView)

Via simple HTML embed code
[19:19]
```

### Best Practices

**Async Mode:**
```
❌ Synchronous: UI freezes while waiting for AI
✅ Asynchronous: UI responsive, shows typing indicator

Always use: Asynchronous with front-end answer [08:12]
```

**UI Controls:**
```
✅ Disable "Send" button while bot is typing
✅ Prevent multiple simultaneous requests
✅ Show clear loading states

Why: Avoid message confusion [07:23]
```

**Error Handling:**
```
Add checks for:
- API errors (rate limit, invalid token)
- Network failures
- Empty responses

Example error message:
"Sorry, I couldn't process your request. Please try again."
```

### Complete Chatbot Checklist

**Setup:**
- [ ] OpenAI account + API token
- [ ] Install OpenAI Integration plugin
- [ ] Install Vanilla Chatbot plugin
- [ ] Create OpenAI Config data format
- [ ] Store API token as Secret

**UI:**
- [ ] Customize chat bubble colors
- [ ] Set up message list container
- [ ] Style input field and send button
- [ ] Add avatar images (optional)

**Logic:**
- [ ] Create "Send Message" action
- [ ] Configure OpenAI API call
- [ ] Set up typing indicator
- [ ] Add error handling
- [ ] Disable send button during processing

**Testing:**
- [ ] Test basic conversation
- [ ] Test error scenarios
- [ ] Check mobile responsiveness
- [ ] Verify async behavior

---



### PART-10-LLM-AUTOMATION.md
## Part 10: LLM Automation (Execute AI Task)

Video: http://www.youtube.com/watch?v=M7xglymj__I

### 1. Project Goals

**Main Goal:** Show how to integrate LLM (AI) into NoCode-X apps for content generation automation.

**Example:** Web page that accepts user text prompt and displays AI-generated SVG image.

### 2. Functional Blocks

**Interface Creation:**
- Prompt input field
- "Generate SVG" button
- Image component for result display

**Logic Setup (Action):**
1. Read text from input
2. Send request to AI
3. Clean response (extract XML/SVG)
4. Display SVG in image component

### 3. Execute AI Task (Technical Details)

**Function: Execute an AI task**

**Task Description (System Prompt):**
```
"Create an SVG based on description: [user_description]"
```
[04:42]

**Expected Output Format:**
```
"Respond with SVG code only, without any additional text"
```
[05:39]

**Model Selection:**
```
Easy switching between models:
- GPT-3.5 Turbo (fast, cheap)
- GPT-4o (high quality)
- DeepSeek (alternative)
- Other models...
```
[08:01]

### 4. Processing AI Response

**Problem:** AI often adds explanatory text or markdown (```xml ... ```)

**Solution:**

**Step 1: Extract XML**
```
Function: Extract XML from LLM response
- Removes markdown formatting
- Strips explanatory text
- Returns clean SVG/XML code
```
[06:20]

**Step 2: Display SVG**
```
Function: Set the SVG of an image element
- Target: Image component on page
- Value: Cleaned SVG code from Step 1
```
[06:53]

### 5. Complete Action Flow

```
Action: Generate SVG

Trigger: On Click (Generate Button)

Step 1: Get Input
├─ Read prompt from input field
└─ Store in Scope → user_prompt

Step 2: Execute AI Task
├─ Function: Execute an AI task
├─ Description: "Create SVG: {{user_prompt}}"
├─ Expected output: "SVG code only"
├─ Model: GPT-4o (or selected model)
└─ Store result → raw_ai_response
[04:42, 05:18, 08:01]

Step 3: Clean Response
├─ Function: Extract XML from LLM response
├─ Input: raw_ai_response
└─ Output: clean_svg_code
[06:20]

Step 4: Display Result
├─ Function: Set the SVG of an image element
├─ Target: svg_display_component
└─ Value: clean_svg_code
[06:53]
```

### 6. Observability & Debugging

**Application Logs:**
```
NoCode-X has built-in application logs showing:
- Exact prompt sent to model
- Raw AI response (including DeepSeek "reasoning" phase)
- Execution timestamps
- Error details

Access: Application → Logs
```
[09:19]

**Why it's critical:**
- Debug prompt engineering
- See model "thinking" process
- Catch API errors
- Optimize token usage

### 7. Using Placeholders

**Dynamic Prompts:**
```
Description field can use Scope variables:

"Create SVG of {{animal}} in {{style}} style, 
with {{color}} color scheme"

Variables from Scope:
- animal: "cat"
- style: "minimalist"
- color: "blue"

Resulting prompt:
"Create SVG of cat in minimalist style, 
with blue color scheme"
```
[05:18]

### Best Practices

**Model Selection:**
```
Simple tasks / prototyping:
✅ GPT-3.5 Turbo (fast, cheap)

High quality / complex details:
✅ GPT-4o (better accuracy)

Example: If model draws cat with one ear,
switch to GPT-4o [08:07]
```

**Response Cleaning:**
```
Always use Extract XML function:
✅ Handles markdown (```xml ... ```)
✅ Removes explanatory text
✅ Validates SVG structure

Don't parse manually!
```

**Prototyping Speed:**
```
Full AI service creation:
- Design UI: 3 minutes
- Configure AI Task: 5 minutes
- Test & debug: 2 minutes

Total: ~10 minutes for working prototype!
```

### Use Cases

**Content Generation:**
- SVG icons/logos
- Code snippets
- Text content
- Email templates

**Data Processing:**
- Text summarization
- Translation
- Classification
- Extraction

**Creative Tasks:**
- Image descriptions
- Story generation
- Marketing copy
- Social media posts

### Quick Start Template

```
Component Structure:
├─ Vertical List (container)
│   ├─ Text Input (prompt field)
│   ├─ Button ("Generate")
│   ├─ Image (SVG display area)
│   └─ Text (status/error messages)

Action: Generate Content
1. Get input value
2. Execute AI Task
3. Extract XML/clean response
4. Set image/component value
5. Show success/error message
```

---



### PART-11-EMAIL-MAILJET.md
## Part 11: Email Automation (Mailjet)

Video: https://www.youtube.com/watch?v=MFg_1AfjXzA

### 1. Mailjet Setup

**Prerequisites:**
- ✅ Mailjet account (free): mailjet.com [01:05]
- ✅ API credentials from API Key Management [01:25]
- ✅ Sender email/domain in "Allow list" [03:06]

**Configuration Data Format:**
```
Data Format: mailjet_config
Fields (all Secret):
- api_key (Secret)
- api_secret (Secret)
- sender_email (Email)
- error_notification_email (Email) [03:39]
```
[02:12]

### 2. Installing Mailjet Plugin

**From Hub:**
```
Hub → Search "Mailjet" → Install
```
[01:51]

### 3. Scenario 1: Raw HTML Email

**Use case:** Simple notifications, alerts

**Action: Send HTML Mail**
```
Function: Send HTML mail (from plugin)

Parameters:
- To: recipient@example.com
- Subject: Dynamic via action parameters [06:30]
- HTML/Text: Email content (HTML or plain text) [05:37]
```
[04:40]

**Testing:**
```
Use built-in "Test Action" tool:
- Enter test parameters manually
- Check result without leaving editor
- Debug before production use
```
[05:56, 06:04]

### 4. Scenario 2: Mailjet Templates

**Use case:** Rich emails (newsletters, password reset)

**Step 1: Create Template in Mailjet**
```
Mailjet Dashboard:
→ Transactional Templates
→ Create template (e.g., "Celebration")
→ Add variables: [[var:first_name]], [[var:date]]
```
[09:56]

**Step 2: Prepare Data in NoCode-X**
```
Action: Prepare Template Data

Step 1: Create object
{
  "first_name": "John",
  "date": "2024-01-15",
  "link": "https://app.com/confirm"
}
```
[11:44]

**Step 3: Send Template Email**
```
Function: Send template mail

Parameters:
- Template ID: 123456 (from Mailjet)
- Template Variables: prepared_object
- To: recipient@example.com
```
[12:35, 13:13]

### 5. Dynamic Data Integration

**Data Sources:**
```
Email content can include:
✅ Database records (user names, dates)
✅ API responses (order details, tracking numbers)
✅ Form submissions (contact requests)
✅ Calculated values (totals, discounts)
```
[01:14:33]

**Conditional Sending:**
```
Trigger examples:
- User registered → Send welcome email
- Order completed → Send receipt
- Password reset requested → Send reset link
- Daily at 9 AM → Send digest
```

### Best Practices

**Testing:**
```
✅ Always use "Test Action" first
✅ Check email rendering in different clients
✅ Verify spam score
✅ Test with real data samples

Don't skip testing before production! [06:04]
```

**Security:**
```
✅ Store API keys as Secret fields
✅ Never hardcode credentials
✅ Use error notification email
✅ Monitor send logs

Why: Protect credentials from leaks
```

**Error Handling:**
```
Mailjet Configuration:
→ Set "Error mail address"
→ Get notified of template errors
→ Monitor delivery rates

Handle errors gracefully:
- Retry failed sends
- Log errors for debugging
- Notify admins of issues
```
[03:39]

### Common Email Patterns

**Pattern 1: Welcome Email**
```
Trigger: User registered
Action: Send Welcome Email
├─ Template: "Welcome" (Mailjet)
├─ Variables: {first_name, login_link}
└─ To: user.email
```

**Pattern 2: Password Reset**
```
Trigger: Reset requested
Action: Send Reset Link
├─ Generate token
├─ Template: "Password Reset"
├─ Variables: {reset_link, expiry_time}
└─ To: user.email
```

**Pattern 3: Notification**
```
Trigger: Event occurred
Action: Send Notification
├─ HTML: Dynamic content
├─ Subject: "New notification"
└─ To: user.email
```

### Complete Email Setup Checklist

**Mailjet Account:**
- [ ] Create account
- [ ] Get API Key and Secret
- [ ] Add sender to Allow list
- [ ] Set up error notification email

**NoCode-X:**
- [ ] Install Mailjet plugin
- [ ] Create mailjet_config data format
- [ ] Store API credentials as Secret
- [ ] Configure sender email

**Templates (if using):**
- [ ] Create templates in Mailjet
- [ ] Add variables [[var:name]]
- [ ] Test templates in Mailjet preview
- [ ] Note template IDs

**Actions:**
- [ ] Create send email actions
- [ ] Test with "Test Action" tool
- [ ] Add error handling
- [ ] Set up triggers (On Event, Schedule)

**Testing:**
- [ ] Send test emails
- [ ] Check different email clients
- [ ] Verify spam folder (not there!)
- [ ] Monitor delivery rates

---

## Last Updated

This skill was created based on NoCode-X documentation dated **February 16, 2026** and video tutorials.

**Key Source URLs:**
- Main docs: https://docs.nocode-x.com
- Rocket Mode: https://docs.nocode-x.com/nocode-x-platform/Rocket_Mode
- Interactive Manuals: https://docs.nocode-x.com/how%20to/interactive%20manuals/
- Building Concepts: https://docs.nocode-x.com/building-concepts/
- Security: https://docs.nocode-x.com/security/

**External References:**
- Telegram Bot API: https://core.telegram.org/bots/api
- Deepgram Documentation: https://developers.deepgram.com/docs
- Stripe Documentation: https://stripe.com/docs
- YooKassa API: https://yookassa.ru/docs
- No-code Payment Integration: https://apix-drive.com/en/blog/other/no-code-payment-integration
- Pinecone Vector DB: https://docs.pinecone.io/
- OpenAI Embeddings: https://platform.openai.com/docs/guides/embeddings
- Weaviate Vector DB: https://weaviate.io/developers/weaviate
- Qdrant Vector DB: https://qdrant.tech/documentation/

**Video Tutorials:**
- Part 1 (Auth & Logic): https://www.youtube.com/watch?v=SBkcR7TvIkw
- Part 2 (Homepage & Navigation): https://www.youtube.com/watch?v=YhTCkMu1npk
- Part 3 (Dynamic Data & Database): https://www.youtube.com/watch?v=7iaPI0XaXkg
- Part 4 (HTML Components & n8n): https://www.youtube.com/watch?v=LuaRbmWhmpM
- Part 5 (Secure Backend): https://www.youtube.com/watch?v=FqrqaNdoVgc
- Part 6 (Rapid API Development): https://www.youtube.com/watch?v=nnd5BV6z5Ao
- Part 7 (Authentication & Custom Login): https://www.youtube.com/watch?v=mR3dXcyO-R4
- Part 8 (Data Tables): http://www.youtube.com/watch?v=ElP1CFe6iRQ
- Part 9 (OpenAI Chatbot): http://www.youtube.com/watch?v=DyrJvtozQW0
- Part 10 (LLM Automation): http://www.youtube.com/watch?v=M7xglymj__I
- Part 11 (Email Automation - Mailjet): https://www.youtube.com/watch?v=MFg_1AfjXzA
- Part 12 (Web Crawler with Pinecone): http://www.youtube.com/watch?v=Bmy-B1zVBIk
- Part 13 (Email with Mailchimp): https://www.youtube.com/watch?v=MtX9828RZkE

---



### PART-12-PINECONE.md
## Part 12: Web Crawler & RAG with Pinecone

Video: http://www.youtube.com/watch?v=Bmy-B1zVBIk

### 1. Core Concepts (RAG & Vector Databases)

**Pinecone:**
Vector database that stores information as vectors — ideal for AI tasks [00:29]

**RAG (Retrieval Augmented Generation):**
Concept where AI (LLM) searches vector storage and uses retrieved information to answer user questions [00:44]

### 2. Setup & Configuration

**Pinecone Assistant:**
- Create assistant in Pinecone
- Get API key [01:40]

**NoCode-X Plugin:**
```
Hub → Search "Pinecone Website Crawler" → Install
```
[02:27]

**Scrape Config Data Format:**
```
Data Format: scrape_config
Fields:
- pinecone_api_key (Secret) - API key
- assistant_name (Text) - Assistant name
- max_pages (Number) - Max pages to crawl (e.g., 200) [05:13]
- scrape_links (Boolean) - Follow internal links
```
[03:21]

### 3. Scraping Process

**Initiate Crawling:**
```
Create record in Scrape Request table:
- url: "https://nocode-x.com"
- status: "pending"
```
[06:09]

**Engine Workflow:**
```
1. Download HTML from URL
2. Extract text content
3. Convert to Markdown
4. Upload to Pinecone Assistant
5. Index for semantic search
```
[06:54]

**Result:**
All website pages become "knowledge" for the AI assistant

### 4. Extracting Structured Data

**Instead of just chatting with bot:**
Get data in strict format (JSON) using your schema

**Step 1: Create Data Format**
```
Website Information:
- company_name (Text)
  Description: "Company name from homepage or about page"
  
- email (Email)
  Description: "Contact email, may be on contact page or in footer"
  
- phone (Text)
  Description: "Phone number with country code"
  
- social_links (List)
  Description: "Links to LinkedIn, Twitter, Facebook"
  
- products (List of Objects)
  Description: "Products or services offered"
```
[15:06, 15:34]

**Step 2: Fetch Structured Data**
```
Action: Extract Website Info

Function: Fetch website information from assistant
Parameters:
- Assistant: Your Pinecone assistant
- URL: Website to analyze
- Output Format: Website Information (Data Format)
```
[14:20]

**AI Uses Field Descriptions:**
```
Detailed descriptions help AI find correct data:
❌ Bad: "Email"
✅ Good: "Contact email address, usually found on contact page or footer, may be obfuscated"
```
[15:34, 20:27]

### 5. Automation & API

**Creating API Endpoint:**
```
Create endpoint in 30 seconds:
- Input: URL parameter
- Action: Fetch website info from assistant
- Output: JSON with extracted data

Result: POST /extract → Returns {company, email, phone, products}
```
[23:31]

**Automation Example:**
```
After extracting email:
1. Save to database
2. Send automated email to company
3. Add to CRM
4. Notify sales team
```
[13:55]

### Best Practices

**Handling Protection:**
```
Some sites obfuscate emails:
✅ Add hints in field descriptions
✅ Specify alternative locations
✅ Mention expected domains

Example: "Email may be on contact page, 
about page, or footer. Look for @company.com"
```
[20:27]

**Customization:**
```
All plugins are Blueprints (чертежи):
✅ Modify logic
✅ Combine with other APIs
✅ Change prompts
✅ Add preprocessing
```
[22:12]

**Limits:**
```
✅ Always set Max pages limit
✅ Start small (10-20 pages)
✅ Monitor API usage
✅ Check crawl duration

Why: Avoid infinite crawling and extra costs [05:13]
```

### Use Cases

**Lead Generation:**
- Crawl competitor websites
- Extract contact information
- Enrich CRM data automatically

**Content Aggregation:**
- Collect articles from news sites
- Index documentation
- Build knowledge bases

**Market Research:**
- Analyze product catalogs
- Compare pricing
- Monitor changes over time


### PART-13-MAILCHIMP.md
 ## Part 13: Email with Mailchimp (Mandrill)
 
 Video: https://www.youtube.com/watch?v=MtX9828RZkE
 
 ### 1. Mailchimp/Mandrill Setup
 
 **Mailchimp uses Mandrill for API-based email:**
 
 **Sender Domain:**
 - Add and verify your domain
 - Confirm ownership via email link
 - Configure DNS records (DKIM and DMARC) [01:55]
 - Status must be "Authenticated" [02:23]
 
 **API Key:**
 - Create in Mandrill settings
 - Demo accounts have domain restrictions [02:45]
 
 ### 2. NoCode-X Configuration
 
 **Install Plugin:**
 ```
 Hub → Search "Mailchimp API Plugin" → Install
 ```
 [01:27]
 
 **Configuration Data Format:**
 ```
 Data Format: mailchimp_config
 Fields:
 - api_key (Secret) - Mandrill API key
   (Automatically encrypted) [03:37]
 ```
 
 ### 3. Send Email Action
 
 **Function: Mailchimp: Send new message**
 ```
 Parameters (Request):
 - text: Email body (text version) [05:38]
 - subject: Email subject
 - from_email: Sender address (must be verified domain) [06:04]
 - to: Array of objects with email and type [06:27]
 ```
 [04:46]
 
 **Example Request:**
 ```json
 {
   "text": "Hello! This is your notification.",
   "subject": "Welcome",
   "from_email": "noreply@yourdomain.com",
   "to": [
     {
       "email": "user@example.com",
       "type": "to"
     }
   ]
 }
 ```
 
 ### 4. Testing & Debugging
 
 **Built-in Tester:**
 ```
 Create "Test cases" in NoCode-X:
 - Save parameter sets
 - Run tests with one click
 - No UI building required
 ```
 [08:06]
 
 **Application Logs:**
 ```
 Check logs for detailed error codes:
 - recipient-domain-mismatch: Wrong domain on demo account
 - invalid-sender: Unverified sender domain
 - quota-exceeded: API limits reached
 ```
 [09:07]
 
 ### 5. Additional Plugin Features
 
 **Beyond simple sending:**
 
 | Feature | Description |
 |---------|-------------|
 | **Get template and info** | Retrieve template details |
 | **Get user info** | Manage user data |
 | **Add new template** | Create templates via API |
 [04:53]
 
 ### Best Practices
 
 **DNS Configuration:**
 ```
 Critical for deliverability:
 ✓ DKIM records configured
 ✓ DMARC policy set
 ✓ Domain authenticated
 ✓ SPF record added
 
 Why: Prevents spam folder delivery
 ```
 [01:55, 02:23]
 
 **Demo Account Limitations:**
 ```
 Free/demo accounts restricted to:
 ✓ Verified sender domains only
 ✓ Limited number of recipients
 ✓ No high-volume sending
 
 For production: Upgrade to paid plan [09:42]
 ```
 
 **Security:**
 ```
 Always use Secret fields for:
 ✓ API keys
 ✓ Authentication tokens
 ✓ Passwords
 
 Never hardcode credentials!
 ```
 
 ### Mailchimp vs Mailjet Comparison
 
 | Feature | Mailchimp/Mandrill | Mailjet |
 |---------|-------------------|---------|
 | **Templates** | Advanced (drag-drop) | Built-in |
 | **API** | Mandrill (separate) | Direct |
 | **Free tier** | Limited (demo) | Generous |
 | **DNS setup** | Required (DKIM/DMARC) | Simpler |
 | **Best for** | Marketing campaigns | Transactional |
 
 ### Complete Mailchimp Setup Checklist
 
 **Mailchimp/Mandrill:**
 - [ ] Create account
 - [ ] Add sender domain
 - [ ] Verify domain ownership
 - [ ] Configure DKIM/DMARC records
 - [ ] Domain status: "Authenticated"
 - [ ] Create Mandrill API key
 
 **NoCode-X:**
 - [ ] Install Mailchimp API Plugin
 - [ ] Create mailchimp_config data format
 - [ ] Store API key as Secret
 - [ ] Configure sender email
 
 **Email Logic:**
 - [ ] Create send email action
 - [ ] Set up test cases
 - [ ] Test with verified domain
 - [ ] Check Application Logs
 - [ ] Handle error scenarios
 
 **Production:**
 - [ ] Upgrade from demo (if needed)
 - [ ] Monitor deliverability
 - [ ] Check spam scores
 - [ ] Set up bounce handling
 
 ---
 


### BONUS-RAPID-API.md
## Bonus: Rapid API Development (AI-Powered)

Video: https://www.youtube.com/watch?v=nnd5BV6z5Ao

### Generate API from Text Description

**Самый быстрый способ создать бэкенд (< 5 минут):**

**Шаг 1:** В разделе **API** выберите **"Create CRUD from text"**

**Шаг 2:** Опишите таблицу на естественном языке:
```
"Создать таблицу для студентов с полями:
- имя (текст)
- фамилия (текст)
- дата рождения (дата)
- средний балл (число)"
```
[01:46]

**Шаг 3:** ИИ автоматически создаёт:
- ✅ Data Format (схему данных)
- ✅ Подбирает типы полей (Text, Date, Number)
- ✅ 5 эндпоинтов:
  - `POST` — Create (создание)
  - `GET` — Read Single (получение по ID)
  - `PUT` — Update (обновление)
  - `DELETE` — Delete (удаление)
  - `GET` — Find (список с фильтрами)
[03:10]

### Testing Endpoints

**Примеры запросов:**

**Create (POST):**
```bash
curl -X POST https://api.nocode-x.com/students \
  -H "Content-Type: application/json" \
  -d '{
    "first_name": "Tristan",
    "last_name": "Smith",
    "birth_date": "1995-03-15",
    "gpa": 4.5
  }'
```
[04:03]

**Read Single (GET):**
```bash
curl https://api.nocode-x.com/students/123
```
[05:17]

**Update (PUT):**
```bash
curl -X PUT https://api.nocode-x.com/students/123 \
  -H "Content-Type: application/json" \
  -d '{"gpa": 4.8}'
```
[09:50]

**Delete (DELETE):**
```bash
curl -X DELETE https://api.nocode-x.com/students/123
```
[10:26]

### Advanced Search & Filtering

**GET List с параметрами:**

**Пагинация:**
```bash
# Получить 2-ю страницу, по 10 записей
GET /students?page=2&amount=10
```
[06:29]

**Фильтрация:**
```bash
# Поиск по имени
GET /students?first_name=Tristan

# Средний балл больше 4.0
GET /students?gpa__gt=4.0

# Фамилия содержит "son"
GET /students?last_name__contains=son
```
[07:14, 08:16]

**Доступные операторы:**

| Оператор | Описание | Пример |
|----------|----------|--------|
| `=` | Равно (по умолчанию) | `?name=John` |
| `__gt` | Greater than (больше) | `?gpa__gt=4.0` |
| `__lt` | Less than (меньше) | `?age__lt=18` |
| `__contains` | Содержит подстроку | `?email__contains=gmail` |

### Customization

**Каждый эндпоинт = визуальный Action:**

```
API Endpoint "Create Student"
  └─ Action: Create Student Logic
      ├─ Step 1: Validate input data
      ├─ Step 2: Check permissions (RBAC)
      ├─ Step 3: Create record in database
      └─ Step 4: Return success response
```
[11:19]

**Можно изменить:**
- ✅ Добавить проверку прав доступа
- ✅ Интегрировать с внешними сервисами
- ✅ Добавить валидацию
- ✅ Изменить формат ответа

### ⚠️ Security Warning

```
❌ По умолчанию: API открытые (Public)
✅ Обязательно: Включить Authentication required!

Настройка:
1. Открыть API endpoint
2. Settings → Authentication required = true
3. Save
```

### Best Practices

**Быстрый старт (MVP):**
```
1. Описать таблицу текстом (2 мин)
2. Сгенерировать API (1 мин)
3. Протестировать в Postman (2 мин)
Итого: 5 минут на полноценный бэкенд!
```

**Продакшн:**
- Всегда включайте аутентификацию
- Настраивайте rate limiting
- Добавляйте валидацию в Action
- Используйте фильтры для больших данных

---



### INDEX.md
# Video Tutorials Index

Complete video course on building with NoCode-X.

## Mindshift Audio Series (Parts 1-4)

Complete mobile hypnotherapy application tutorial:

| Part | Topic | Video | Guide |
|------|-------|-------|-------|
| **Part 1** | Auth & Login Pages | [YouTube](https://www.youtube.com/watch?v=SBkcR7TvIkw) | [Detailed Guide](./MINDSHIFT-AUDIO-PART-1.md) |
| **Part 2** | Homepage & Navigation | [YouTube](https://www.youtube.com/watch?v=YhTCkMu1npk) | [Detailed Guide](./MINDSHIFT-AUDIO-PART-2.md) |
| **Part 3** | Dynamic Data & Credits | [YouTube](https://www.youtube.com/watch?v=7iaPI0XaXkg) | [Detailed Guide](./MINDSHIFT-AUDIO-PART-3.md) |
| **Part 4** | N8N Integration & AI Chat | [YouTube](https://www.youtube.com/watch?v=LuaRbmWhmpM) | [Detailed Guide](./MINDSHIFT-AUDIO-PART-4.md) |

**Total**: 1,797 lines of detailed documentation

## CRM Development Series (Parts 1-4)

Complete CRM with AI features:

| Part | Topic | Video | Guide |
|------|-------|-------|-------|
| **Part 1** | AI Email Automation | [YouTube](https://www.youtube.com/watch?v=g22GjR6RDjk) | [Detailed Guide](./CRM-PART-1-EMAIL.md) |
| **Part 2** | Update Operation | [YouTube](https://www.youtube.com/watch?v=ewPwyMr9YNo) | [Detailed Guide](./CRM-PART-2-UPDATE.md) |
| **Part 3** | UI Refactoring | [YouTube](https://www.youtube.com/watch?v=iiKW0qK8mVM) | [Detailed Guide](./CRM-PART-3-REFACTORING.md) |
| **Part 4** | Create & Delete (CRUD) | [YouTube](http://www.youtube.com/watch?v=DTcI8okVEjw) | [Detailed Guide](./CRM-PART-4-CRUD.md) |
| **Bonus** | CRM Dashboard (AI-Generated) | [YouTube](http://www.youtube.com/watch?v=NCROc3uob68) | [Detailed Guide](./CRM-PART-14-DASHBOARD.md) |

**Total**: 1,292 lines of detailed documentation

## Original Tutorial Series (Parts 5-14)

| Part | Topic | Video | Guide |
|------|-------|-------|-------|
| **Part 5** | Secure Backend for Frontend | [YouTube](https://www.youtube.com/watch?v=FqrqaNdoVgc) | [Core Guide](../core/ROCKET-MODE.md) |
| **Part 6** | Rapid API Development | [YouTube](https://www.youtube.com/watch?v=nnd5BV6z5Ao) | [Bonus Guide](./BONUS-RAPID-API.md) |
| **Part 7** | Authentication & Login | [YouTube](https://www.youtube.com/watch?v=mR3dXcyO-R4) | [Detailed Guide](./PART-7-AUTHENTICATION.md) |
| **Part 8** | Data Tables | [YouTube](http://www.youtube.com/watch?v=ElP1CFe6iRQ) | [Detailed Guide](./PART-8-DATA-TABLES.md) |
| **Part 9** | OpenAI Chatbot | [YouTube](http://www.youtube.com/watch?v=DyrJvtozQW0) | [Detailed Guide](./PART-9-OPENAI-CHATBOT.md) |
| **Part 10** | LLM Automation | [YouTube](http://www.youtube.com/watch?v=M7xglymj__I) | [Detailed Guide](./PART-10-LLM-AUTOMATION.md) |
| **Part 11** | Email Automation (Mailjet) | [YouTube](https://www.youtube.com/watch?v=MFg_1AfjXzA) | [Detailed Guide](./PART-11-EMAIL-MAILJET.md) |
| **Part 12** | Web Crawler (Pinecone) | [YouTube](http://www.youtube.com/watch?v=Bmy-B1zVBIk) | [Detailed Guide](./PART-12-PINECONE.md) |
| **Part 13** | Email (Mailchimp) | [YouTube](https://www.youtube.com/watch?v=MtX9828RZkE) | [Detailed Guide](./PART-13-MAILCHIMP.md) |

## Quick Navigation

- **Beginners**: Start with [Mindshift Audio Part 1](./MINDSHIFT-AUDIO-PART-1.md)
- **CRM Development**: Start with [CRM Part 1](./CRM-PART-1-EMAIL.md)
- **Backend/API**: See [Bonus Rapid API](./BONUS-RAPID-API.md)
- **Integrations**: See Parts [9](./PART-9-OPENAI-CHATBOT.md), [10](./PART-10-LLM-AUTOMATION.md), [11-13](./PART-11-EMAIL-MAILJET.md)

## Resources

- [Platform Overview](../core/PLATFORM-OVERVIEW.md)
- [Quick Start](../core/QUICK-START.md)
- [Production Guides](../guides/)


---

## Execution

### helpik-bot/README.md
# Helpik.me Bot Configuration

## Environment Variables

Copy `.env.example` to `.env` and fill in your values:

```bash
# Telegram
TELEGRAM_BOT_TOKEN=your_bot_token_from_botfather

# AI Services
OPENROUTER_API_KEY=your_openrouter_key
DEEPGRAM_API_KEY=your_deepgram_key
WESPER_API_URL=https://your-wesper-server.com/api
WESPER_API_KEY=your_wesper_key

# Payments (optional for testing)
STRIPE_SECRET_KEY=sk_test_...
STRIPE_WEBHOOK_SECRET=whsec_...
YOOKASSA_SHOP_ID=your_shop_id
YOOKASSA_SECRET_KEY=your_secret_key

# Database (NoCode-X webhook endpoint)
NOCODE_X_WEBHOOK_URL=https://your-app.nocode-x.com/webhook
```

## NoCode-X Setup

### 1. Create Data Tables

Use the schema in: `.sisyphus/notepads/helpik-full-development/database-schema.md`

Create these tables in order:
1. users
2. credits
3. operations
4. payments
5. costs
6. utm_tags
7. rate_limits
8. ai_models_usage
9. daily_stats
10. traffic_stats

### 2. Create Actions

See `actions/` directory for action specifications.

### 3. Setup Webhook

1. Get your webhook URL from NoCode-X
2. Set it in environment variables
3. Configure Telegram webhook:
   ```
   https://api.telegram.org/bot<TOKEN>/setWebhook?url=<WEBHOOK_URL>
   ```

## AI Service Integrations

### OpenRouter
- Endpoint: `https://openrouter.ai/api/v1/chat/completions`
- Models: `anthropic/claude-3.5-sonnet`, `openai/gpt-4o`
- Cost tracking: Automatic via costs table

### Deepgram (Voice Transcription)
- Endpoint: `https://api.deepgram.com/v1/listen`
- Model: `nova-3`
- Fallback from Wesper

### Wesper (Primary Voice)
- Your private Whisper server
- Must implement: `POST /transcribe` endpoint
- Input: `{ "audio_url": "...", "language": "ru" }`
- Output: `{ "transcription": "..." }`

## Rate Limiting

- Limit: 10 requests per minute per user
- Implementation: rate_limits table + CheckRateLimit action
- Reset: Every minute via Job

## Daily Reports

- Generated at 6:00 AM daily
- Format: Text with emojis (see specification)
- Metrics: Users, Finance, Generations, Traffic

## Commands

### User Commands
- `/start` - Registration + 10 free credits
- `/help` - List commands and prices
- `/balance` - Show balance
- `/summarize [text]` - Summarize (1💎)
- `/analyze [conversation]` - Analyze (2💎)
- `/voice` - Voice to text (2💎)
- `/rewrite [text]` - Rewrite (1💎)
- `/reply [context]` - Generate reply (2💎)
- `/formulate [idea]` - Formulate thought (1💎)
- `/buy` - Purchase credits
- `/coupon CODE` - Apply coupon
- `/delete_my_data` - Delete all data (GDPR)

### Admin Commands
- `/admin_report [today/yesterday/week]` - Daily report
- `/admin_stats [users/finance/marketing/models]` - Statistics
- `/admin_coupon_create [type] [value] [max_uses] [days]` - Create coupon
- `/admin_user_list` - List users
- `/admin_user_delete [id]` - Delete user

## Testing

### Manual Testing Checklist
- [ ] Registration gives 10 credits
- [ ] Each AI function deducts correct amount
- [ ] Rate limiting blocks after 10/min
- [ ] Payments add credits
- [ ] Coupons work (all 5 types)
- [ ] Daily report generates
- [ ] Data deletion works

## Deployment

1. Setup NoCode-X tables
2. Create all Actions
3. Configure environment variables
4. Set Telegram webhook
5. Test all flows
6. Monitor daily reports

## Support

For issues with NoCode-X platform: https://docs.nocode-x.com
For AI integration issues: Check OpenRouter/Deepgram docs


### helpik-bot/IMPLEMENTATION-GUIDE.md
# Helpik.me — Complete Implementation Guide

> Полное руководство по настройке всех Actions в NoCode-X

---

## Wave 2: Core AI Integrations

### 1. OpenRouter Integration (Task 10)

**Action Name**: `CallOpenRouter`

**Purpose**: HTTP запрос к OpenRouter API для генерации текста

#### Input Parameters:
| Parameter | Type | Required | Default |
|-----------|------|----------|---------|
| model | String | Yes | "anthropic/claude-3.5-sonnet" |
| system_prompt | String | Yes | — |
| user_message | String | Yes | — |
| max_tokens | Number | No | 2000 |

#### Output:
| Field | Type | Description |
|-------|------|-------------|
| success | Boolean | Успешность запроса |
| response | String | Сгенерированный текст |
| usage.input_tokens | Number | Входные токены |
| usage.output_tokens | Number | Выходные токены |
| usage.total_cost | Number | Стоимость в $ |
| error | String | Сообщение об ошибке |

#### HTTP Configuration:
```
Method: POST
URL: https://openrouter.ai/api/v1/chat/completions
Timeout: 30 seconds
Retry: 3 attempts with exponential backoff (1s, 2s, 4s)
```

#### Headers:
```
Authorization: Bearer {{OPENROUTER_API_KEY}}
Content-Type: application/json
HTTP-Referer: https://helpik.me
X-Title: HelpikBot
```

#### Request Body:
```json
{
  "model": "{{model}}",
  "messages": [
    {"role": "system", "content": "{{system_prompt}}"},
    {"role": "user", "content": "{{user_message}}"}
  ],
  "max_tokens": {{max_tokens}},
  "temperature": 0.7
}
```

#### Response Parsing:
```javascript
// Success case (status 200)
{
  success: true,
  response: response.choices[0].message.content,
  usage: {
    input_tokens: response.usage.prompt_tokens,
    output_tokens: response.usage.completion_tokens,
    total_cost: response.usage.cost || 0
  },
  error: null
}

// Error case
{
  success: false,
  response: null,
  usage: null,
  error: "AI service timeout" | "Rate limited" | error.message
}
```

#### Error Handling:
1. **Timeout (30s)**: Return error "AI service timeout"
2. **429 (Rate limit)**: Wait 1s, retry (max 3 total attempts)
3. **5xx (Server error)**: Retry with backoff (max 3 attempts)
4. **4xx (Client error)**: Return error message, no retry
5. **Network error**: Retry once

#### Cost Logging:
After successful call, create record in `costs` table:
- operation_id: (current operation ID)
- ai_model: {{model}}
- cost_type: "INPUT"
- tokens_used: usage.input_tokens
- cost_rub: (calculate from $ cost)

---

### 2. Wesper Integration (Task 11)

**Action Name**: `TranscribeAudioWesper`

**Purpose**: Транскрибация аудио через приватный Whisper сервер (primary)

#### Input:
| Parameter | Type | Description |
|-----------|------|-------------|
| audio_url | String | URL к аудио файлу (OGG от Telegram) |
| language | String | "ru" или "auto" |

#### Output:
| Field | Type | Description |
|-------|------|-------------|
| success | Boolean | Успешность |
| transcription | String | Транскрибированный текст |
| processing_time | Number | Время обработки (сек) |
| error | String | Ошибка (null если success) |

#### HTTP Configuration:
```
Method: POST
URL: {{WESPER_API_URL}}/transcribe
Timeout: 10 seconds
Retry: 0 (no retry, immediate fallback)
```

#### Headers:
```
Authorization: Bearer {{WESPER_API_KEY}}
Content-Type: application/json
```

#### Request Body:
```json
{
  "audio_url": "{{audio_url}}",
  "language": "{{language}}"
}
```

#### Expected Response:
```json
{
  "transcription": "Привет, как дела?",
  "processing_time": 2.3,
  "language": "ru"
}
```

#### Fallback Logic:
```
IF timeout OR error:
  1. Log failure (for monitoring)
  2. Call Action: TranscribeAudioDeepgram
  3. Return Deepgram result
ELSE:
  Return Wesper result
```

---

### 3. Deepgram Integration (Task 12)

**Action Name**: `TranscribeAudioDeepgram`

**Purpose**: Fallback транскрибация через Deepgram API

#### Input:
| Parameter | Type | Description |
|-----------|------|-------------|
| audio_url | String | URL к аудио файлу |
| language | String | "ru" |

#### Output:
| Field | Type | Description |
|-------|------|-------------|
| success | Boolean | Успешность |
| transcription | String | Текст |
| confidence | Number | Уверенность (0-1) |
| duration | Number | Длительность (сек) |
| error | String | Ошибка |

#### HTTP Configuration:
```
Method: POST
URL: https://api.deepgram.com/v1/listen?model=nova-3&smart_format=true&language={{language}}
Timeout: 30 seconds
Retry: 2 attempts
```

#### Headers:
```
Authorization: Token {{DEEPGRAM_API_KEY}}
Content-Type: application/json
```

#### Request Body:
```json
{
  "url": "{{audio_url}}"
}
```

#### Response Parsing:
```javascript
{
  success: response.results ? true : false,
  transcription: response.results?.channels[0]?.alternatives[0]?.transcript || "",
  confidence: response.results?.channels[0]?.alternatives[0]?.confidence || 0,
  duration: response.metadata?.duration || 0,
  error: error?.message || null
}
```

---

### 4-9. AI Actions (Tasks 13-18)

#### Action: SummarizeText (Task 13)

**Cost**: 1💎

**Flow**:
1. CheckRateLimit(user_id)
2. IF rate limit exceeded → return error
3. CheckBalance(user_id, 1)
4. IF balance < 1 → return error "Недостаточно кредитов"
5. CallOpenRouter(
   - model: "anthropic/claude-3.5-sonnet"
   - system_prompt: "Сделай краткое содержание текста на русском языке. Выдели главные тезисы."
   - user_message: {{text}}
   - max_tokens: 500
   )
6. IF success:
   - DeductCredits(user_id, 1, "SUMMARIZE")
   - LogOperation(user_id, "SUMMARIZE", "claude-3.5", 1, input_length, output_length, "SUCCESS")
   - Return response
7. ELSE:
   - LogOperation(user_id, "SUMMARIZE", "claude-3.5", 1, input_length, 0, "ERROR", error)
   - Return error

#### Action: AnalyzeConversation (Task 14)

**Cost**: 2💎

**System Prompt**:
```
Проанализируй переписку. Определи:
1. Тон общения (формальный/неформальный, дружелюбный/враждебный)
2. Ключевые мысли каждого собеседника
3. Основной конфликт или тема
4. Рекомендации по ответу

Формат ответа:
Тон: [описание]
Ключевые мысли:
- [участник 1]: ...
- [участник 2]: ...
Конфликт/Тема: [описание]
Рекомендации: [советы]
```

**Flow**: Same as SummarizeText, but cost=2

#### Action: VoiceToText (Task 15)

**Cost**: 2💎

**Flow**:
1. CheckRateLimit(user_id)
2. CheckBalance(user_id, 2)
3. TranscribeAudioWesper(audio_url, "ru")
4. IF Wesper fails → TranscribeAudioDeepgram(audio_url, "ru")
5. IF transcription successful:
   - Call SummarizeText on transcription
   - DeductCredits(user_id, 2, "VOICE")
   - LogOperation(user_id, "VOICE", model_used, 2, ...)
   - Delete audio file (HTTP DELETE to audio_url)
   - Return {transcription, summary}
6. ELSE:
   - Log error
   - Return error

#### Action: RewriteText (Task 16)

**Cost**: 1💎

**Styles**:
- SHORTER: "Сократи текст, сохранив смысл"
- CLEARER: "Перепиши текст более понятно и ясно"
- POLITE: "Сделай текст более вежливым и тактичным"
- PROFESSIONAL: "Сделай текст более деловым и формальным"

**Flow**: Same pattern, cost=1

#### Action: GenerateReply (Task 17)

**Cost**: 2💎

**Tones**:
- FRIENDLY: "Сгенерируй дружелюбный ответ"
- PROFESSIONAL: "Сгенерируй профессиональный ответ"
- APOLOGETIC: "Сгенерируй извиняющийся ответ"

**System Prompt Template**:
```
На основе контекста переписки сгенерируй подходящий ответ.
Тон: {{tone}}

Контекст:
{{context}}

Ответ должен быть вежливым, по существу и соответствовать тону.
```

#### Action: FormulateThought (Task 18)

**Cost**: 1💎

**System Prompt**:
```
Помоги сформулировать мысль. Пользователь знает, что хочет сказать, 
но не может подобрать слова. Преврати сырую идею в связный, 
вежливый и понятный текст.

Сырая идея: {{raw_idea}}

Сформулируй красиво:
```

---

## Wave 3: Business Logic

### 10. Rate Limiting (Task 19)

**Action Name**: `CheckRateLimit`

**Purpose**: Проверка лимита 10 запросов/мин на пользователя

**Input**:
- user_id: UUID

**Output**:
- allowed: Boolean (true if under limit)
- remaining: Number (requests remaining)
- reset_at: DateTime (when limit resets)

**Algorithm**:
```javascript
// 1. Get current minute timestamp
const currentMinute = floor(now() / 60000) * 60000;

// 2. Search rate_limits table
const record = SearchOne(
  table: "rate_limits",
  filter: user_id == {{user_id}} AND window_start == currentMinute
);

// 3. If no record - create new
if (!record) {
  CreateRecord("rate_limits", {
    user_id: {{user_id}},
    request_count: 1,
    window_start: currentMinute
  });
  return { allowed: true, remaining: 9, reset_at: currentMinute + 60000 };
}

// 4. If record exists
if (record.request_count >= 10) {
  return { allowed: false, remaining: 0, reset_at: currentMinute + 60000 };
}

// 5. Increment count
UpdateRecord("rate_limits", record.id, {
  request_count: record.request_count + 1
});

return { 
  allowed: true, 
  remaining: 10 - (record.request_count + 1),
  reset_at: currentMinute + 60000 
};
```

**Job: ResetRateLimits**:
- Frequency: Every minute
- Action: Delete records from rate_limits where window_start < current_minute - 5

### 11. DeductCredits (Task 20)

**Action Name**: `DeductCredits`

**Input**:
- user_id: UUID
- amount: Number
- operation_type: Enum

**Output**:
- success: Boolean
- new_balance: Number
- error: String

**Algorithm**:
```javascript
// 1. Get credits record
const credits = SearchOne("credits", { user_id: {{user_id}} });

// 2. Check if subscription is active
if (credits.subscription_until > now()) {
  // User has unlimited subscription - no deduction
  return { success: true, new_balance: credits.balance, error: null };
}

// 3. Check balance
if (credits.balance < {{amount}}) {
  return { success: false, new_balance: credits.balance, error: "Insufficient credits" };
}

// 4. Deduct
UpdateRecord("credits", credits.id, {
  balance: credits.balance - {{amount}},
  total_used: credits.total_used + {{amount}}
});

// 5. Log operation
CreateRecord("operations", {
  user_id: {{user_id}},
  type: {{operation_type}},
  cost: {{amount}},
  status: "SUCCESS"
});

return { success: true, new_balance: credits.balance - {{amount}}, error: null };
```

### 12. AddCredits (Task 21)

**Action Name**: `AddCredits`

**Input**:
- user_id: UUID
- amount: Number
- source: Enum (PAYMENT, COUPON)

**Output**:
- success: Boolean
- new_balance: Number

**Algorithm**:
```javascript
const credits = SearchOne("credits", { user_id: {{user_id}} });

UpdateRecord("credits", credits.id, {
  balance: credits.balance + {{amount}},
  total_purchased: credits.total_purchased + {{amount}}
});

return { success: true, new_balance: credits.balance + {{amount}} };
```

### 13-14. Payment Integrations (Tasks 22-23)

#### Stripe (Native NoCode-X)

Use built-in Stripe integration:
1. Configure Stripe keys in NoCode-X settings
2. Create payment link with metadata:
   - user_id: {{user_id}}
   - tariff_id: {{tariff_id}}
3. User pays via Stripe Checkout
4. Webhook "payment_intent.succeeded" triggers AddCredits

#### ЮKassa (HTTP API)

**Action Name**: `CreateYookassaPayment`

**HTTP Configuration**:
```
Method: POST
URL: https://api.yookassa.ru/v3/payments
Headers:
  Authorization: Basic {{base64(SHOP_ID:SECRET_KEY)}}
  Content-Type: application/json
Idempotence-Key: {{uuid}}
```

**Request Body**:
```json
{
  "amount": {
    "value": "{{amount}}.00",
    "currency": "RUB"
  },
  "payment_method_data": {
    "type": "bank_card"
  },
  "confirmation": {
    "type": "redirect",
    "return_url": "https://t.me/{{bot_username}}"
  },
  "metadata": {
    "user_id": "{{user_id}}",
    "credits": "{{credits}}"
  },
  "description": "{{credits}} кредитов для Helpik"
}
```

### 15. Webhook Handlers (Task 24)

**Stripe Webhook**:
- Event: `payment_intent.succeeded`
- Action: Extract metadata.user_id and metadata.credits → Call AddCredits

**ЮKassa Webhook**:
- Event: `payment.waiting_for_capture`
- Action: Capture payment → AddCredits

**Telegram Webhook**:
- Endpoint: NoCode-X API endpoint
- Action: Parse message → Route to command handler

### 16-18. Coupons (Tasks 25-27)

**Action: ValidateCoupon**
```javascript
const coupon = SearchOne("coupons", { code: {{code}}, is_active: true });

if (!coupon) return { valid: false, error: "Купон не найден" };
if (coupon.valid_until < now()) return { valid: false, error: "Купон истёк" };
if (coupon.used_count >= coupon.max_uses) return { valid: false, error: "Купон исчерпан" };

const existing = SearchOne("coupon_usages", { 
  coupon_id: coupon.id, 
  user_id: {{user_id}} 
});
if (existing) return { valid: false, error: "Купон уже использован" };

return { valid: true, coupon: coupon };
```

**Action: ApplyCoupon**
```javascript
const validation = ValidateCoupon({{code}}, {{user_id}});
if (!validation.valid) return validation;

const coupon = validation.coupon;

// Apply based on type
if (coupon.type == "FREE_CREDITS") {
  AddCredits({{user_id}}, coupon.value, "COUPON");
} else if (coupon.type == "WEEK_UNLIMITED") {
  UpdateCreditsSubscription({{user_id}}, "WEEK", now() + 7 days);
} else if (coupon.type == "MONTH_UNLIMITED") {
  UpdateCreditsSubscription({{user_id}}, "MONTH", now() + 30 days);
}
// PERCENT_DISCOUNT and FIXED_DISCOUNT applied during payment

// Mark as used
UpdateRecord("coupons", coupon.id, { used_count: coupon.used_count + 1 });
CreateRecord("coupon_usages", {
  coupon_id: coupon.id,
  user_id: {{user_id}},
  used_at: now()
});

return { success: true };
```

---

## Wave 4: GDPR

### 19. DeleteUserData (Task 29)

**Action Name**: `DeleteUserData`

**Algorithm**:
```javascript
// 1. Delete all user-related records
DeleteAll("operations", { user_id: {{user_id}} });
DeleteAll("payments", { user_id: {{user_id}} });
DeleteAll("utm_tags", { user_id: {{user_id}} });
DeleteAll("rate_limits", { user_id: {{user_id}} });
DeleteAll("credits", { user_id: {{user_id}} });

// 2. Anonymize user record
UpdateRecord("users", {{user_id}}, {
  username: null,
  first_name: null,
  last_name: null,
  is_active: false
});

return { success: true };
```

### 20. /delete_my_data Command (Task 30)

**Flow**:
1. User sends `/delete_my_data`
2. Bot replies: "⚠️ Это удалит ВСЕ ваши данные... Отправьте ДА для подтверждения."
3. Wait for "ДА" message (timeout: 5 minutes)
4. If "ДА" received → Call DeleteUserData → Send confirmation
5. If timeout or other message → Cancel deletion

---

## Wave 5: Advanced Analytics

### 21-23. Stats Tables (Tasks 34-36)

Already defined in database-schema.md

### 24. CalculateDailyStats (Task 37)

**Job**: Run every day at 23:55

**Algorithm**:
```javascript
const today = startOfDay(now());

const stats = {
  date: today,
  new_users: Count("users", { created_at: { $gte: today, $lt: today+1day } }),
  active_users: CountDistinct("operations", "user_id", { created_at: { $gte: today } }),
  total_users: Count("users"),
  returning_users: Count("users", { last_active: { $gte: today-1day, $lt: today } }),
  operations_count: Count("operations", { created_at: { $gte: today } }),
  revenue_rub: Sum("payments", "amount_rub", { created_at: { $gte: today }, status: "COMPLETED" }),
  costs_rub: Sum("costs", "cost_rub", { created_at: { $gte: today } }),
  profit_rub: revenue_rub - costs_rub
};

CreateOrUpdate("daily_stats", { date: today }, stats);
```

### 25-27. Stats Actions (Tasks 38-40)

**GetUserStats(period)**:
```javascript
// period: "today", "yesterday", "week", "month"
const start = calculateStart(period);
const end = calculateEnd(period);

return {
  new_users: Count("users", { created_at: { $gte: start, $lt: end } }),
  growth_percent: calculateGrowth(period),
  avg_per_day: new_users / daysInPeriod,
  returning: CountReturningUsers(start, end),
  conversion_new_to_active: calculateConversion(start, end)
};
```

**GetFinancialStats(period)**:
```javascript
return {
  payments_count: Count("payments", { created_at: { $gte: start }, status: "COMPLETED" }),
  revenue: Sum("payments", "amount_rub", ...),
  by_tariff: GroupBy("payments", "tariff_id", ...),
  avg_check: revenue / payments_count,
  costs: Sum("costs", "cost_rub", ...),
  profit: revenue - costs,
  margin_percent: (profit / revenue) * 100
};
```

**GetMarketingStats(period)**:
```javascript
return {
  by_source: GroupBy("utm_tags", "source", {
    users: Count(),
    converted: Count({ converted_to_paid: true }),
    revenue: Sum("conversion_value")
  }),
  top_channels: Sort(by_source, "revenue", desc).limit(5)
};
```

### 28. GenerateDailyReport (Task 41)

**Job**: Every day at 6:00

**Format**:
```
📊 Ежедневный отчёт: {{date}}

👥 ПОЛЬЗОВАТЕЛИ
+{{new_users}} новых (было {{prev_total}} → стало {{total_users}})
• Прирост: +{{growth}}% за сутки
• Среднее в день: ~{{avg_per_day}}
• Вернувшихся: {{returning}}
• Новых с генерацией: {{new_with_ops}} ({{conversion}}%)

💰 ФИНАНСЫ
{{payments_count}} платежей на {{revenue}}₽
• Средний чек: {{avg_check}}₽
• Расходы (AI API): {{costs}}₽
• Прибыль: +{{profit}}₽ ({{margin}}% маржа)

🖼 ГЕНЕРАЦИИ
• Текст: {{text_count}}
• Голос: {{voice_count}}
• Анализ: {{analyze_count}}

Текст по моделям:
{{#each models}}
• {{name}}: {{count}}
{{/each}}

📣 TRAFFIC
{{#each sources}}
• {{source}}: {{users}} users
{{/each}}
```

---

## Wave 6: Polish

### Error Handling (Task 44)

**Global Error Handler**:
- Log all errors to errors table
- Send user-friendly message
- Retry if applicable
- Alert admin for critical errors

**Fallback Messages**:
```
AI Timeout: "Извините, AI сервис временно недоступен. Попробуйте через минуту."
Rate Limit: "Превышен лимит запросов. Подождите минуту."
No Credits: "Недостаточно кредитов. Купите кредиты: /buy"
Generic: "Произошла ошибка. Попробуйте позже или обратитесь в поддержку."
```

### Logging (Task 45)

Log everything:
- All AI requests (operations table)
- All payments (payments table)
- All errors (errors table)
- All admin actions (admin_logs table)

### Testing (Task 47)

**E2E Test Scenarios**:
1. Registration → /start → 10 credits
2. Summarize → Deduct 1 → 9 credits
3. Rate limit → 11th request blocked
4. Payment → Stripe → Add credits
5. Coupon → Apply → Free credits
6. Voice → Wesper fails → Deepgram works
7. Daily report → Generated at 6:00
8. Delete data → All records cleared

---

*Implementation Guide v1.0*
*Created: 20 February 2026*
