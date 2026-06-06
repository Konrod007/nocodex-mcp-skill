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

