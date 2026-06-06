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

