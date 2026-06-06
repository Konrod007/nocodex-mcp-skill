# NoCode-X: Advanced Features & Patterns

> Advanced topics: Vector databases, Telegram bots, payment systems, SaaS patterns

---

## Vector Database Integration (RAG, Semantic Search)

### Can NoCode-X Store Vectors Natively?

**No.** NoCode-X uses a traditional relational database, which is NOT optimized for high-dimensional vector operations.

**BUT** you can integrate external vector databases via HTTP API calls.

### Recommended Architecture

```
NoCode-X (logic) + Pinecone (vectors) + OpenAI (embeddings)
```

### Supported Vector Databases

| Database | Type | Integration | Best For |
|----------|------|-------------|----------|
| **Pinecone** | Managed SaaS | HTTP REST API | Production, scale |
| **Weaviate** | Self-hosted/Cloud | HTTP REST API | Flexibility, GraphQL |
| **Qdrant** | Self-hosted/Cloud | HTTP REST API | Open source, speed |
| **Supabase pgvector** | PostgreSQL extension | Via API | Simple setup |

### Use Cases

1. **Semantic Search** — Find documents by meaning, not keywords
2. **RAG (Retrieval-Augmented Generation)** — Feed relevant docs to LLM
3. **Recommendations** — "Similar to X" functionality
4. **Duplicate Detection** — Find similar images/text
5. **Knowledge Base** — AI-powered Q&A over documents

### Pinecone Integration Example

**Generate Embeddings:**
```bash
POST https://api.openai.com/v1/embeddings
Authorization: Bearer <OPENAI_API_KEY>

{
  "input": "Your text here",
  "model": "text-embedding-3-small"
}
```

**Store in Pinecone:**
```bash
POST https://<INDEX_HOST>/vectors/upsert
Api-Key: <PINECONE_API_KEY>

{
  "vectors": [{
    "id": "doc_123",
    "values": [0.0023, -0.0089, 0.1234, ...],
    "metadata": {
      "user_id": "user_456",
      "title": "Document Title"
    }
  }],
  "namespace": "user_456"
}
```

---

## Telegram Bot Integration

NoCode-X does NOT have a native Telegram node, but you can integrate using HTTP API calls.

### Architecture

```
User → Telegram Bot → NoCode-X API → Deepgram → Telegram Bot → User
```

### Setup

1. Create bot via @BotFather
2. Set up webhook in NoCode-X
3. Process voice messages

### Telegram API Endpoints

```bash
# Get file path
GET https://api.telegram.org/bot<TOKEN>/getFile?file_id=<FILE_ID>

# Download file
GET https://api.telegram.org/file/bot<TOKEN>/<file_path>

# Send message
POST https://api.telegram.org/bot<TOKEN>/sendMessage
{
  "chat_id": "<CHAT_ID>",
  "text": "<MESSAGE>"
}
```

### Deepgram Integration

```bash
POST https://api.deepgram.com/v1/listen?model=nova-3&smart_format=true
Authorization: Token <DEEPGRAM_API_KEY>
Content-Type: audio/ogg

# Response
{
  "results": {
    "channels": [{
      "alternatives": [{
        "transcript": "Hello, this is the transcribed text"
      }]
    }]
  }
}
```

### Voice Message Workflow

```
1. Receive webhook from Telegram
2. Get file_id from message
3. Download audio from Telegram
4. Send to Deepgram for transcription
5. Send result back to user
6. DELETE audio file (CRITICAL!)
```

---

## Payment Integration

### Available Integrations

| Integration | Type | Documentation |
|-------------|------|---------------|
| **Stripe** | Payment Gateway | Built-in |
| **Mailchimp** | Email Marketing | Via API |
| **MailJet** | Email Marketing | Via API |
| **YooKassa** | Payment (Russia/CIS) | Via HTTP API |

### Stripe (Native)

```
User → NoCode-X Page → Stripe Checkout → Webhook → Update user access
```

**Rocket Mode Prompt:**
```
Create a subscription system with:
- Stripe integration for payments
- Three tiers: Free, Pro ($9.99/month), Enterprise ($49/month)
- Subscription status tracking in database
- Webhook handler for payment.succeeded event
```

### YooKassa (via API)

**Create Payment:**
```bash
POST https://api.yookassa.ru/v3/payments
Authorization: Basic <BASIC_AUTH>

{
  "amount": {"value": "100.00", "currency": "RUB"},
  "payment_method_data": {"type": "bank_card"},
  "confirmation": {
    "type": "redirect",
    "return_url": "https://yoursite.com/success"
  },
  "metadata": {
    "user_id": "123",
    "order_id": "456"
  }
}
```

### Payment Database Schema (NoSQL)

```
users:
  - id: UUID
  - email: string
  - subscription_tier: enum (free, pro, enterprise)
  - subscription_status: enum (active, canceled, past_due)
  - credits_balance: integer

payments:
  - id: UUID
  - user_id: UUID (Reference)
  - amount: decimal
  - currency: string (RUB, USD, EUR)
  - status: enum (pending, succeeded, failed)
  - external_payment_id: string
```

---

## Credits & Tokens System

### Architecture

```
User Balance
  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
  │ Total       │  │ Used        │  │ Available   │
  │ Credits     │  │ Credits     │  │ = Total -   │
  └─────────────┘  └─────────────┘  └─────────────┘
```

### Credit Packages

| Package | Price | Credits | Price/Credit |
|---------|-------|---------|--------------|
| Starter | 99 ₽ | 100 | ~1 ₽ |
| Comfort | 599 ₽ | 1000 | ~0.6 ₽ |
| Maximum | 1999 ₽ | 5000 | ~0.4 ₽ |

### Credit Consumption Rules

| Feature | Cost (credits) | Calculation |
|---------|----------------|-------------|
| Voice Transcription | 1 | Per minute |
| AI Text Generation | 2-10 | Per 1000 tokens |
| Image Generation | 5-20 | Per image |
| API Call | 1 | Per request |

### Implementation Logic

```
1. Check balance ≥ cost BEFORE execution
2. Deduct credits (create pending transaction)
3. Execute action
4. Confirm transaction (or rollback on failure)
5. Notify user of balance update
```

---

## Complete SaaS Example

### Rocket Mode Prompt

```
Build a SaaS subscription system with:

1. USER MANAGEMENT:
   - Registration with email verification
   - Three subscription tiers with credit allowances
   - Credit balance system with purchase options

2. PAYMENT INTEGRATION:
   - Stripe integration for subscriptions
   - Credit package purchases (one-time)
   - Webhook handlers for payment events

3. CREDIT SYSTEM:
   - Daily credit allowance based on tier
   - Additional purchased credits
   - Credit consumption tracking per feature
   - Real-time balance display

4. FEATURES & LIMITS:
   - Free tier: limited usage
   - Pro tier: increased limits, priority support
   - Enterprise: unlimited, API access

5. NOTIFICATIONS:
   - Email when subscription renews
   - Warning at 20% daily limit
   - Alert when credits exhausted

6. ADMIN DASHBOARD:
   - View all users and their stats
   - Credit package management
   - Refund handling
```

---

## Troubleshooting

### Common Issues

**"Action not triggering"**
- Check if action is linked to a trigger
- Verify the action is not "dead"
- Check trigger conditions

**"API returns 401/403"**
- Verify API key in environment variables
- Check header format
- Ensure API key has permissions

**"Database query is slow"**
- Add indexes to frequently queried fields
- Use pagination for large datasets
- Avoid N+1 queries

**"Credits not deducting"**
- Check if credit check is BEFORE action execution
- Verify database transaction is committed
- Check if rollback occurs on error

---

## Security Best Practices

### Environment Variables
```
❌ NEVER: api_key = "sk_live_1234567890"
✅ ALWAYS: api_key = env.STRIPE_API_KEY
```

### Webhook Security
- Validate webhook signatures
- Use HTTPS-only webhook URLs
- Implement idempotency keys
- Log all webhook events

### File Upload Security
- Validate file types (whitelist)
- Scan uploads for malware
- Store files outside web root
- Generate random filenames

### Data Protection
- Encrypt sensitive data at rest
- Use HTTPS for all API communications
- Implement proper access controls
- Set data retention policies

---

## Server-side Code (Backend)

> ⚠️ **Beta/Planned Feature** — Проверьте актуальность в документации NoCode-X

### Возможности

NoCode-X планирует запуск исполнения кода на стороне сервера для сложной бизнес-логики, которую трудно реализовать визуальными нодами.

### Поддерживаемые языки

| Язык | Применение | Статус |
|------|------------|--------|
| **Python** | Data processing, ML, complex algorithms | Planned |
| **JavaScript** | API integrations, data transformations | Planned |

### Use Cases

**1. Сложные вычисления:**
```python
# Пример: Расчет сложной статистики
def calculate_user_metrics(data):
    """Calculate advanced user engagement metrics"""
    metrics = {
        'retention_rate': calculate_retention(data),
        'ltv': calculate_ltv(data),
        'churn_probability': predict_churn(data)
    }
    return metrics
```

**2. Интеграции с legacy-системами:**
```python
# Пример: Интеграция с ERP
import requests

def sync_with_erp(user_data):
    """Sync user data with corporate ERP"""
    response = requests.post(
        'https://erp.company.com/api/users',
        json=user_data,
        headers={'Authorization': f'Bearer {erp_token}'}
    )
    return response.json()
```

**3. Обработка файлов:**
```javascript
// Пример: Генерация PDF отчетов
const puppeteer = require('puppeteer');

async function generateReport(data) {
    const browser = await puppeteer.launch();
    const page = await browser.newPage();
    
    await page.setContent(createHTMLTemplate(data));
    const pdf = await page.pdf({ format: 'A4' });
    
    await browser.close();
    return pdf;
}
```

### Как использовать

**Вызов из Action:**
```
Action: Process Complex Logic
├─ Step 1: Prepare input data
├─ Step 2: Call Server Function
│   ├─ Function: calculate_metrics
│   ├─ Language: python
│   └─ Input: prepared_data
└─ Step 3: Process result
```

**Ограничения:**
- ⏱️ Timeout: 30 seconds per execution
- 📦 Memory: 512 MB per function
- 🔄 Concurrent: 10 parallel executions per app

### Безопасность

- Код выполняется в изолированном sandbox
- Нет доступа к файловой системе хоста
- Ограниченный network access (whitelist URLs)
- Автоматическое логирование всех вызовов

---

## Deployment Checklist

### Pre-Launch
- [ ] All API keys switched to production
- [ ] Webhook URLs point to production domain
- [ ] Database indexes created
- [ ] Error logging configured
- [ ] Backup strategy tested
- [ ] Rate limits enabled
- [ ] File size limits configured
- [ ] SSL certificate installed
- [ ] Terms of Service published
- [ ] Privacy Policy published

### Post-Launch
- [ ] Monitor error logs daily
- [ ] Check API rate limits
- [ ] Verify backup jobs running
- [ ] Review user feedback
- [ ] Monitor credit consumption

---

*Part of NoCode-X Skill*
