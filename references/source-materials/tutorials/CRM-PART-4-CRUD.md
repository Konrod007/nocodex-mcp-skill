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

