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

