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

