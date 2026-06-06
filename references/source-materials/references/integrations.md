# NoCode-X: Integrations & External Systems

> Руководство по интеграции HTML-компонентов, n8n и использованию NoCode-X как бэкенда
> На основе видео: https://www.youtube.com/watch?v=LuaRbmWhmpM и https://www.youtube.com/watch?v=FqrqaNdoVgc

---

## Содержание

1. [HTML Components](#html-components)
2. [n8n Integration](#n8n-integration)
3. [Configuration & Security](#configuration--security)
4. [State Management (Future)](#state-management-future)
5. [NoCode-X as Backend](#nocode-x-as-backend)
6. [Best Practices](#best-practices)

---

## HTML Components

**Video:** https://www.youtube.com/watch?v=LuaRbmWhmpM

### Возможности HTML-компонента

| Feature | Description | Timestamp |
|---------|-------------|-----------|
| **Pure HTML/CSS/JS** | Добавление чистого кода | [02:46] |
| **CDN Libraries** | Подключение внешних библиотек | [05:43] |
| **Dynamic Data** | Плейсхолдеры для параметров | [03:59] |

### Use Cases
- Кастомные UI элементы (календари, графики)
- Чаты и мессенджеры
- 3D визуализации (Three.js)
- Сложные формы с валидацией

### CDN Integration
```html
<!-- Подключение библиотеки через CDN -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/flatpickr/dist/flatpickr.min.css">
```
[05:43, 06:09]

---

## n8n Integration

### Building Chat Interface

**Структура чата на HTML:**
```html
<div class="chat-container">
  <!-- Messages Area -->
  <div id="messages" class="messages-area">
    <!-- Messages will appear here -->
  </div>
  
  <!-- Input Area -->
  <div class="input-area">
    <input type="text" id="message-input" placeholder="Type message...">
    <button id="send-btn">Send</button>
  </div>
</div>
```
[10:36]

### Отправка сообщения в n8n

```javascript
async function sendMessageToN8n(messageText) {
  const webhookUrl = '{{n8n_webhook_url}}'; // From NoCode-X parameter
  
  const response = await fetch(webhookUrl, {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify({
      message: messageText,
      user_id: '{{user_id}}',
      timestamp: new Date().toISOString()
    })
  });
  
  const data = await response.json();
  displayMessage(data.reply, 'bot');
}
```
[18:20]

### Инициализация чата

```javascript
document.addEventListener('DOMContentLoaded', () => {
  const sendBtn = document.getElementById('send-btn');
  const input = document.getElementById('message-input');
  
  // Send on button click
  sendBtn.addEventListener('click', () => {
    const message = input.value;
    if (message.trim()) {
      sendMessageToN8n(message);
      input.value = '';
    }
  });
  
  // Send on Enter key
  input.addEventListener('keypress', (e) => {
    if (e.key === 'Enter') {
      sendBtn.click();
    }
  });
});
```
[27:54]

---

## Configuration & Security

### Configuration Table

```
Table: mindshift_config
Fields:
- n8n_webhook_url (URL) - endpoint для n8n
- welcome_message (Text) - приветственное сообщение
- environment (Enum: development, production)
[36:02]
```

### Secret Fields

В NoCode-X можно пометить поле как **Secret**:
- ✅ Данные шифруются на уровне приложения
- ✅ Ведётся аудит изменений (кто, когда, что менял)
- ✅ Не отображаются в логах
[34:14]

```
Настройка:
1. Создать поле в Data Format
2. В настройках поля: Classification = "Secret"
3. NoCode-X автоматически включает шифрование
```

### Environments
- Development — для тестирования
- Production — для реальных пользователей
[36:16]

---

## State Management (Future)

**Анонсированная функция:**

```
State (Глобальное состояние):
- Доступно из любого экшена и шаблона
- Независимо от вложенности
- Обновление в одном месте → видно везде

Use cases:
- Обновление баланса после запроса в чате [21:20]
- Глобальные настройки приложения
- Состояние авторизации
- Тема оформления (dark/light)
```
[19:47]

---

## NoCode-X as Backend

**Video:** https://www.youtube.com/watch?v=FqrqaNdoVgc

### Project Goals
- Использование NoCode-X как полноценного бэкенда для фронтенда
- Аутентификация + API для внешних приложений

### Functional Blocks
- **Backend:** Data Format + API generation [01:43, 02:00]
- **Frontend:** React с OIDC библиотекой [03:27, 09:00]
- **Security:** Protected API + Access Tokens [17:55, 19:35]

### Technical Implementation

**NoCode-X Auth:** Workspace → Authentication [05:25]

**SPA Settings:** Не использовать Client Secret [07:42]

**Redirect URLs:** Доверенные URL для callback [12:08]

### React Integration

**OIDC Configuration:**
```javascript
const oidcConfig = {
  issuerId: 'your-workspace-id', // Unique workspace ID [10:33]
  clientId: 'your-client-id',
  homeUrl: 'http://localhost:3000/',
  redirectUri: 'http://localhost:3000/callback',
  // NO clientSecret for SPA!
};
```

**Environment Isolation:**
```javascript
// Development
const devConfig = {
  issuerId: 'nocode-x-dev-xxx',
  homeUrl: 'http://localhost:3000/'
};

// Production
const prodConfig = {
  issuerId: 'nocode-x-prod-yyy', // Different ID! [10:57]
  homeUrl: 'https://myapp.com/'
};
```

**Login Status Check:**
```javascript
import { useOidc } from '@axa-fr/react-oidc';

function App() {
  const { isAuthenticated } = useOidc();
  
  return (
    <div>
      {isAuthenticated ? (
        <Dashboard /> // Show content [14:22]
      ) : (
        <LoginButton /> // Show login
      )}
    </div>
  );
}
```

**API Call with Token:**
```javascript
async function fetchData() {
  // 1. Get token from OIDC
  const token = oidc.tokens.accessToken; // Bearer token [20:56]
  
  // 2. Call NoCode-X API
  const response = await fetch(
    'https://api.nocode-x.com/your-endpoint',
    {
      headers: {
        'Authorization': `Bearer ${token}`, // Secure! [19:35]
        'Content-Type': 'application/json'
      }
    }
  );
  
  const data = await response.json();
  return data;
}
```

### Architecture Overview

```
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│   React App     │────▶│   NoCode-X Auth  │     │   NoCode-X API  │
│   (Frontend)    │     │   (OIDC Server)  │     │   (Protected)   │
│                 │     │                  │     │                 │
│ - Login Button  │     │ - Custom UI      │     │ - Data Access   │
│ - API Calls     │     │ - Token Issuance │     │ - Business Logic│
│ - Token Storage │◀────│ - User Mgmt      │◀────│ - Database      │
└─────────────────┘     └──────────────────┘     └─────────────────┘
         │                                               ▲
         │         Authorization: Bearer <token>         │
         └───────────────────────────────────────────────┘
```

---

## Custom Auth Flows (OIDC)

### Custom Templates

NoCode-X позволяет полностью кастомизировать страницы аутентификации:

**Доступные для кастомизации страницы:**
- **Login Page** — страница входа
- **Registration Page** — страница регистрации
- **Reset Password Page** — восстановление пароля
- **Email Verification Page** — подтверждение email

**Как настроить:**
```
Workspace → Authentication → Templates
→ Select template to customize
→ Edit in Template Editor
```

**Преимущества:**
- ✅ Брендинг (логотип, цвета компании)
- ✅ Кастомные поля (дополнительные вопросы при регистрации)
- ✅ Локализация (перевод на нужный язык)
- ✅ React-приложение будет использовать ваш кастомный интерфейс [05:54]

### Identity Providers

Подключение внешних провайдеров аутентификации:

**Доступные провайдеры:**
- **Microsoft Entra ID** (Azure AD) — для корпоративных клиентов
- **Google** — Gmail/Google Workspace
- **LinkedIn** — для B2B приложений
- **GitHub** — для разработчиков
- **Apple** — Sign in with Apple (обязательно для iOS)

**Настройка:**
```
Workspace → Authentication → Identity Providers
→ Add Provider
→ Configure OAuth credentials
→ Map user attributes
```

**Поток:**
```
Пользователь → Кнопка "Sign in with Google"
→ Редирект на Google OAuth
→ Согласие на доступ
→ Редирект обратно в NoCode-X
→ Создание/обновление пользователя
→ JWT токен для доступа к API
```

### OIDC Configuration

**Настройки для Single Page Applications (SPA):**

```javascript
const oidcConfig = {
  // НЕ используйте Client Secret в браузере! [07:42]
  issuerId: 'your-workspace-id',
  clientId: 'your-client-id',
  redirectUri: 'https://yourapp.com/callback',
  responseType: 'token id_token',
  scope: 'openid profile email',
  
  // PKCE для безопасности (обязательно для SPA)
  usePKCE: true
};
```

**Важные эндпоинты:**
```
Authorization Endpoint: /oauth/authorize
Token Endpoint: /oauth/token
UserInfo Endpoint: /oauth/userinfo
Logout Endpoint: /oauth/logout
```

---

## Best Practices

### HTML Component Guidelines

```
✅ DO:
- Use for complex UI not available in standard widgets
- Connect libraries via CDN for advanced features
- Pass configuration via NoCode-X parameters
- Use Secret classification for API keys

❌ DON'T:
- Store API keys in plain text in code
- Hardcode URLs that change between environments
- Make the component too complex (hard to debug)
```

### Security Checklist

- [ ] API keys marked as Secret [34:05]
- [ ] Different configs for Dev/Prod environments
- [ ] Input validation in JavaScript
- [ ] HTTPS only for webhooks
- [ ] Audit log reviewed regularly

### Integration Checklist

- [ ] HTML component created with proper structure
- [ ] CSS styles applied
- [ ] JavaScript logic implemented
- [ ] CDN libraries loaded (if needed)
- [ ] Configuration table created
- [ ] Sensitive data marked as Secret
- [ ] On Load action fetches config
- [ ] Parameters passed to template
- [ ] n8n webhook tested
- [ ] Error handling implemented

### Backend Integration Checklist

**NoCode-X Backend:**
- [ ] Create Data Format for your entities [01:43]
- [ ] Generate test data
- [ ] Create API endpoint [02:00]
- [ ] Configure Authentication settings [05:25]
- [ ] Get issuerId (workspace ID) [10:33]
- [ ] Add Redirect URLs (localhost + production) [12:08]
- [ ] Set API to "Authentication required" [17:55]

**Frontend (React/Vue/Angular):**
- [ ] Install OIDC library (e.g., @axa-fr/react-oidc) [09:00]
- [ ] Configure OIDC with issuerId and clientId [10:33]
- [ ] Implement login/logout buttons
- [ ] Check auth status (isAuthenticated) [14:22]
- [ ] Get access token
- [ ] Add Bearer token to API calls [20:56]
- [ ] Handle token expiration

---

*Part of NoCode-X Skill | Video Tutorials: https://www.youtube.com/watch?v=LuaRbmWhmpM, https://www.youtube.com/watch?v=FqrqaNdoVgc*
