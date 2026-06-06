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
