## Part 7: Authentication & Custom Login Pages

Video: https://www.youtube.com/watch?v=mR3dXcyO-R4

### 1. Enabling Authentication

**Goal:** Require authentication for accessing application or specific pages.

**Page-level Protection:**
```
Template Editor → Settings → Authentication required = true
```
[01:28]

**Global Protection via Template Hierarchy:**
```
Root Template → Authentication required = true
  └─ All Child Templates inherit protection automatically
```
[03:18]

**Best Practice:**
```
❌ Bad: Enable auth on every page manually
✅ Good: Enable once in Root Template

Result: All new pages automatically protected, no security holes
```

### 2. User Management

**User Types:**
- **Developers** — Build the application
- **Users** — Use the application
[04:08]

**Creating Users (Manual):**

| Setting | Description |
|---------|-------------|
| **Verified email** | Mark email as already confirmed |
| **Temporary password** | Force password change on first login |
| **MFA** | Require OTP (Google Authenticator) |
| **WebAuthn** | Biometric auth (Face ID, fingerprint, USB tokens) |
[05:49, 06:29]

### 3. Custom Login Page (Vanilla Login Plugin)

**Installation:**
```
Hub → Search "Vanilla Login" → Install
```
[09:25]

**What you get:**
- Login page template
- Registration page template
- Password reset template
- Email verification template
- All logic pre-built!

**Customization:**
```
Edit templates like regular pages:
- Change colors
- Modify button radius
- Add your logo
- Adjust layout
```
[10:35]

**Activation:**
```
Company Settings → Authentication
→ Set custom templates:
  - Login: My Custom Login Template
  - Register: My Custom Register Template
  - Reset Password: My Custom Reset Template
```
[12:35]

### 4. Logout Implementation

**Simple as:**
```
Button: "Logout"
On Click → Execute Action: Logout

That's it! [15:05]
```

### Best Practices

**Security Hierarchy:**
```
Always configure base security in Root Template:
✅ Prevents accidental unprotected pages
✅ New pages automatically inherit protection
✅ Single point of control
```

**Use Plugins for Speed:**
```
Don't build login forms from scratch:
✅ Install Vanilla Login (5 minutes)
✅ Customize for your brand
✅ Get all auth flows working immediately

Time saved: 3-4 hours of development
```

**MFA Recommendation:**
```
For critical applications:
✅ Enable MFA/WebAuthn at account creation
✅ Recommend Google Authenticator
✅ Support Face ID / fingerprint on mobile

Security level: Enterprise-grade
```

### Security Checklist

- [ ] Root Template has "Authentication required"
- [ ] All pages inherit protection (check Child Templates)
- [ ] Vanilla Login plugin installed and customized
- [ ] Custom templates activated in Company Settings
- [ ] MFA/WebAuthn enabled for admin accounts
- [ ] Logout button implemented
- [ ] Password reset flow tested
- [ ] Email verification working

---

