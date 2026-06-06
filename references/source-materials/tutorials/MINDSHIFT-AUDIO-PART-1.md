## Tutorial: Building "Mindshift Audio" App (Part 1)

Video: https://www.youtube.com/watch?v=SBkcR7TvIkw

Complete step-by-step guide to building a mobile-first audio hypnotherapy application with AI-generated personalized content.

### 1. Project Concept [00:00]

**Idea:** Create a personalized audio self-help application for hypnotherapy sessions.

**Key Features:**
```
├─ AI-powered content generation based on user input
├─ Backend selects random background music (prevents habituation)
├─ Mobile-first responsive design
├─ Credit system for usage
├─ Custom audio player via HTML component
└─ Belief assessment system
```

**Architecture:**
```
Frontend (Mobile App UI)
        ↓
AI Processing (User input → Structured request)
        ↓
Backend (Generate audio + Random music selection)
        ↓
User receives unique personalized recording
```

### 2. Project Setup [03:43]

**Starting Fresh:**
```
Create New Application:
├─ Clean slate (no pre-built actions/templates)
├─ Mobile-first approach
└─ English language for international audience
```

**First Template: Login Page:**
```
Step 1: Create Template
├─ Name: "Login Page"
└─ Type: Authentication page

Step 2: Disable Authentication (Critical!)
Template Settings → Authentication Required: ❌ OFF
Why: Users can't access login page if auth is required
```

**Editor Navigation Tips:**
```
├─ Shift key: Toggle between selection and pan tools
├─ Ctrl + Scroll: Zoom in/out
├─ Space + Drag: Pan canvas
└─ 100% width/height: Full page containers
```

### 3. Design System Setup [07:38]

**Accessing Design System:**
```
Navigation: Design System tab

Benefits:
├─ Centralized color management
├─ Global typography control
├─ Automatic updates across all pages
└─ Brand consistency

Colors Defined:
├─ Primary: Main brand color
├─ Secondary: Accent color
├─ Background: Page background
├─ Surface: Cards, panels
└─ Text: Content colors
```

**Design Token Strategy:**
```
✅ DO: Use semantic names (Primary, not "Blue")
✅ DO: Set up Dark/Light mode variants
✅ DO: Test accessibility (contrast ratios)
✅ DO: Document color usage patterns
```

### 4. Login Page Layout [08:48]

**Container Structure:**
```
Root Container (Vertical List)
├─ Width: 100%
├─ Height: 100%
├─ Position: X=0, Y=0 (absolute)
└─ Alignment: Center (all items)

Child Elements:
├─ Logo (Image) - 70x70px, centered
├─ Title (Text) - "Welcome Back"
├─ Email Field (Input)
├─ Password Field (Input)
├─ Forgot Password (Link)
└─ Login Button (Primary action)
```

**Vertical vs Horizontal Lists:**
```
Vertical List:
├─ Elements stack top-to-bottom
├─ Use for: Forms, cards, content sections
└─ Spacing: Gap between items

Horizontal List:
├─ Elements side-by-side
├─ Use for: Navigation, button groups, headers
└─ Alignment: Left, center, right, space-between
```

**Input Fields:**
```
Label vs Placeholder:
├─ Label: Moves up when typing (floating)
├─ Placeholder: Disappears on input
└─ Recommendation: Use Labels for clarity

Configuration:
├─ Type: Email (for email validation)
├─ Type: Password (masked input)
├─ Required: Yes
└─ Style: Match design system
```

**Button Styling:**
```
Login Button:
├─ Text: "Login"
├─ Icon: Login icon (Google Font Icons)
├─ Border Radius: 12px (rounded corners)
├─ Background: Primary color
├─ Hover: Darker shade
└─ Full width on mobile
```

**Link Styling:**
```
Forgot Password Link:
├─ Font Size: 10px
├─ Color: Text secondary
├─ Alignment: Right

Hover State (On Hover):
├─ Text Decoration: Underline
├─ Cursor: Pointer (hand icon)
└─ Color: Primary (optional)
```

### 5. Login Logic Implementation [35:14]

**Workspace Configuration:**
```
Step 1: Go to Workspace Settings
Step 2: Select "Authentication" tab
Step 3: Choose your app for login handling
Step 4: Save configuration

Result: NoCode-X knows which app handles authentication
```

**Creating Login Action:**
```
Trigger: On Click (Login button)
Action Name: "Login"
Description: "Authenticates user with email and password"

Logic Flow:
1. Get value of field (Email)
   └─ Save to Variable Scope: "email"

2. Get value of field (Password)
   └─ Save to Variable Scope: "password"

3. Login function
   ├─ Email: {{email}}
   └─ Password: {{password}}

4. On Success → Route to Home Page
5. On Error → Show error message
```

**Variable Scope:**
```
Concept: Temporary storage during action execution

Structure (like a spreadsheet):
┌─────────────┬──────────────────┐
│ Name        │ Value            │
├─────────────┼──────────────────┤
│ email       │ user@example.com │
│ password    │ ********         │
│ user_id     │ 12345            │
└─────────────┴──────────────────┘

Usage:
├─ Store: Function results
├─ Pass: Between action steps
└─ Access: Via {{variable_name}}
```

**Naming Conventions:**
```
✅ GOOD Action Names:
├─ "Login User"
├─ "Validate Email Format"
├─ "Send Welcome Email"
└─ "Calculate Total Price"

❌ BAD Action Names:
├─ "Action 1"
├─ "Do stuff"
├─ "Process"
└─ "Handle click"

Why it matters:
├─ Clarity for future you
├─ Team collaboration
├─ AI assistant understanding
└─ Debugging and logs
```

### 6. Registration Page [01:03:23]

**Duplicating Template:**
```
Efficient approach:
1. Right-click "Login Page"
2. Select "Duplicate"
3. Rename to "Register"
4. Modify as needed

Benefits:
├─ Consistent styling
├─ Faster development
├─ Shared design patterns
└─ Easier maintenance
```

**Registration Fields:**
```
Additional Inputs:
├─ First Name (Text)
├─ Last Name (Text)
├─ Email (Email)
├─ Password (Password)
└─ Confirm Password (Password)
```

**Terms & Conditions:**
```
Layout: Horizontal List
├─ Slide Toggle (Checkbox)
│   └─ State: On/Off
├─ Text: "I agree to Terms of Service"
│   └─ Link to terms page

Logic:
├─ Toggle state stored in variable
├─ Registration blocked if not checked
└─ Show error: "Please accept terms"
```

**Email Verification Strategy:**
```
Option 1: Immediate verification
├─ User clicks link immediately
└─ Simpler flow

Option 2: Verification on first login (Recommended)
├─ Link sent after registration
├─ Valid for 10 minutes
├─ More secure (time-limited)
└─ Better UX (can explore first)

Configuration:
Settings → Authentication → Email Verification
```

### 7. Page Navigation [01:19:02]

**Internal Routing:**
```
Don't: Hard-code URLs
├─ Breaks when domain changes
├─ Difficult to maintain
└─ Not portable between environments

Do: Use Route to Page function
├─ Reference template by name
├─ Works across environments
├─ Maintains navigation history
└─ Automatic URL generation
```

**Implementing Navigation:**
```
From Login to Register:

1. Add On Click trigger to "Sign up" link
2. Create Action: "Go to Register"
3. Add function: Route to Page
4. Select Template: "Register"
5. Save and test

Implementation:
├─ Trigger: Click on "Sign up" link
├─ Action: Navigate to Register
├─ Method: Route to Page (Register)
└─ Result: URL updates, page loads
```

**Testing Navigation:**
```
Incognito Mode Testing:
├─ Tests clean session
├─ No cached data
├─ Simulates new user experience
└─ Catches auth issues early

Checklist:
├─ Login page loads without auth
├─ Click "Sign up" → Register page
├─ Register page loads correctly
├─ All elements styled properly
├─ Mobile responsive
└─ No console errors
```

### 8. Mobile-First Considerations

**Design Principles:**
```
Mobile-First Approach:
├─ Design for mobile screens first
├─ Progressive enhancement for desktop
├─ Touch-friendly targets (min 44px)
├─ Readable text (min 16px)
└─ Simplified navigation

Testing:
├─ Use browser dev tools (mobile view)
├─ Test on actual devices
├─ Check touch interactions
└─ Verify load times on mobile networks
```

**Responsive Patterns:**
```
Container Strategy:
├─ Max-width on desktop (centered)
├─ Full-width on mobile
├─ Padding adjustments
└─ Stack elements vertically on small screens

Typography:
├─ Scalable font sizes
├─ Readable line heights
├─ Adequate contrast
└─ Appropriate line lengths (45-75 chars)
```

### Best Practices from Tutorial

**Development Workflow:**
```
1. Plan structure (paper/wireframe)
2. Set up design system first
3. Build core templates
4. Implement logic incrementally
5. Test continuously
6. Iterate based on feedback
```

**Code Organization:**
```
✅ DO:
├─ Name everything clearly
├─ Group related elements
├─ Use consistent spacing
├─ Document complex logic
├─ Test edge cases
└─ Clean up unused elements

❌ DON'T:
├─ Leave default names
├─ Skip documentation
├─ Mix different patterns
├─ Ignore mobile view
├─ Forget error handling
└─ Rush to production
```

### Quick Mindshift Audio Checklist

**Part 1 Complete:**
- [ ] Project created (clean slate)
- [ ] Login page template created
- [ ] Authentication disabled on login page
- [ ] Design system configured
- [ ] Login form layout (logo, fields, button)
- [ ] Login action implemented
- [ ] Variable scope usage
- [ ] Registration page (duplicated + modified)
- [ ] Terms & conditions toggle
- [ ] Navigation between pages working
- [ ] Mobile responsive tested

**Part 2 Preview (Next Steps):**
- [x] Root template with navigation
- [x] Template hierarchy
- [x] Homepage with user greeting
- [x] Credit display
- [x] Consistency bar
- [x] Safety warnings
- [x] Part 3: Audio generation flow
- [x] Part 4: N8N chat integration
- [ ] Additional features (payments, advanced AI)

---

