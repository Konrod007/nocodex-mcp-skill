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

