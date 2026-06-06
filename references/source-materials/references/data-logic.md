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
