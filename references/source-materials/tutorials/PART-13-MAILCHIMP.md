 ## Part 13: Email with Mailchimp (Mandrill)
 
 Video: https://www.youtube.com/watch?v=MtX9828RZkE
 
 ### 1. Mailchimp/Mandrill Setup
 
 **Mailchimp uses Mandrill for API-based email:**
 
 **Sender Domain:**
 - Add and verify your domain
 - Confirm ownership via email link
 - Configure DNS records (DKIM and DMARC) [01:55]
 - Status must be "Authenticated" [02:23]
 
 **API Key:**
 - Create in Mandrill settings
 - Demo accounts have domain restrictions [02:45]
 
 ### 2. NoCode-X Configuration
 
 **Install Plugin:**
 ```
 Hub → Search "Mailchimp API Plugin" → Install
 ```
 [01:27]
 
 **Configuration Data Format:**
 ```
 Data Format: mailchimp_config
 Fields:
 - api_key (Secret) - Mandrill API key
   (Automatically encrypted) [03:37]
 ```
 
 ### 3. Send Email Action
 
 **Function: Mailchimp: Send new message**
 ```
 Parameters (Request):
 - text: Email body (text version) [05:38]
 - subject: Email subject
 - from_email: Sender address (must be verified domain) [06:04]
 - to: Array of objects with email and type [06:27]
 ```
 [04:46]
 
 **Example Request:**
 ```json
 {
   "text": "Hello! This is your notification.",
   "subject": "Welcome",
   "from_email": "noreply@yourdomain.com",
   "to": [
     {
       "email": "user@example.com",
       "type": "to"
     }
   ]
 }
 ```
 
 ### 4. Testing & Debugging
 
 **Built-in Tester:**
 ```
 Create "Test cases" in NoCode-X:
 - Save parameter sets
 - Run tests with one click
 - No UI building required
 ```
 [08:06]
 
 **Application Logs:**
 ```
 Check logs for detailed error codes:
 - recipient-domain-mismatch: Wrong domain on demo account
 - invalid-sender: Unverified sender domain
 - quota-exceeded: API limits reached
 ```
 [09:07]
 
 ### 5. Additional Plugin Features
 
 **Beyond simple sending:**
 
 | Feature | Description |
 |---------|-------------|
 | **Get template and info** | Retrieve template details |
 | **Get user info** | Manage user data |
 | **Add new template** | Create templates via API |
 [04:53]
 
 ### Best Practices
 
 **DNS Configuration:**
 ```
 Critical for deliverability:
 ✓ DKIM records configured
 ✓ DMARC policy set
 ✓ Domain authenticated
 ✓ SPF record added
 
 Why: Prevents spam folder delivery
 ```
 [01:55, 02:23]
 
 **Demo Account Limitations:**
 ```
 Free/demo accounts restricted to:
 ✓ Verified sender domains only
 ✓ Limited number of recipients
 ✓ No high-volume sending
 
 For production: Upgrade to paid plan [09:42]
 ```
 
 **Security:**
 ```
 Always use Secret fields for:
 ✓ API keys
 ✓ Authentication tokens
 ✓ Passwords
 
 Never hardcode credentials!
 ```
 
 ### Mailchimp vs Mailjet Comparison
 
 | Feature | Mailchimp/Mandrill | Mailjet |
 |---------|-------------------|---------|
 | **Templates** | Advanced (drag-drop) | Built-in |
 | **API** | Mandrill (separate) | Direct |
 | **Free tier** | Limited (demo) | Generous |
 | **DNS setup** | Required (DKIM/DMARC) | Simpler |
 | **Best for** | Marketing campaigns | Transactional |
 
 ### Complete Mailchimp Setup Checklist
 
 **Mailchimp/Mandrill:**
 - [ ] Create account
 - [ ] Add sender domain
 - [ ] Verify domain ownership
 - [ ] Configure DKIM/DMARC records
 - [ ] Domain status: "Authenticated"
 - [ ] Create Mandrill API key
 
 **NoCode-X:**
 - [ ] Install Mailchimp API Plugin
 - [ ] Create mailchimp_config data format
 - [ ] Store API key as Secret
 - [ ] Configure sender email
 
 **Email Logic:**
 - [ ] Create send email action
 - [ ] Set up test cases
 - [ ] Test with verified domain
 - [ ] Check Application Logs
 - [ ] Handle error scenarios
 
 **Production:**
 - [ ] Upgrade from demo (if needed)
 - [ ] Monitor deliverability
 - [ ] Check spam scores
 - [ ] Set up bounce handling
 
 ---
 
