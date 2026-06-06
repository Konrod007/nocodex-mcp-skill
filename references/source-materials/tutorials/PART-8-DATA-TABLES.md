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

