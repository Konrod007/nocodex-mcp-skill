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

