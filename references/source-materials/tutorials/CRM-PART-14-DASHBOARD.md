 ## Part 14: CRM Dashboard (AI-Generated)
 
 Video: http://www.youtube.com/watch?v=NCROc3uob68
 
 ### 1. Project Goals
 
 **Main Goal:** Build a functional CRM dashboard prototype in one session.
 
 **Key Tasks:**
 - Generate page design with AI
 - Set up data structure for users with test records
 - Implement data loading into Data Table
 - Interactive detail view: Update user info in side panel on row click [00:44]
 
 ### 2. Functional Blocks
 
 **AI Generation:**
 - Use text prompt to create dashboard layout with table and details window [02:00]
 
 **Data Structure:**
 ```
 Data Format: User
 Fields:
 - first_name (Text)
 - last_name (Text)
 - gender (Enum)
 - lead_source (Text)
 - profile_photo (Image URL)
 - country (Text)
 ```
 [05:14]
 
 **Test Data:**
 - Generate 5 random users for testing [09:47]
 
 **Data Binding:**
 - Display data in text fields and image component [28:12]
 
 ### 3. Technical Implementation
 
 **Container Hierarchy:**
 ```
 Main Container: Horizontal List
 ├─ Left Panel (50%): Data Table
 └─ Right Panel (50%): User Details
 ```
 [15:01]
 
 **Layout Settings:**
 - Use "Space between" to align elements to edges [13:42]
 
 **Loading Data (On Load):**
 ```
 Action: Load Users
 
 Step 1: Fetch a list of data records
 └─ Get all users from database [17:50]
 
 Step 2: Add list of objects to data table
 └─ Populate table with fetched data [19:26]
 
 ⚠️ Important: Delete default rows and columns first! [22:01]
 ```
 
 **Row Click Handler (On Click):**
 ```
 Event: On Click on table row
 Parameters automatically created:
 - Row Code (ID of clicked row)
 - Row Data (object with row data) [28:32]
 
 Action: Update Detail View
 
 Step 1: Configure Row Data parameter
 ├─ Switch from Free Input to Parameter Input
 ├─ Define fields: first_name, last_name, country, etc.
 └─ This tells NoCode-X the data structure [32:35]
 
 Step 2: Update UI elements
 ├─ Set value of input field (for form elements)
 ├─ Set text on text element (for layout elements)
 └─ Use Row Data fields as source [38:20]
 ```
 
 **Combining Strings:**
 ```
 Function: Replace placeholders
 Text field: "{{first_name}} {{last_name}}"
 
 Result: "John Smith" (combined from two fields)
 ```
 [41:39]
 
 ### 4. Important Development Tips
 
 **Media Library:**
 ```
 Upload images via Media section
 Each photo gets a URL
 Store URL in user's profile_photo field
 ```
 [46:55]
 
 **Debugging with Logs:**
 ```
 Function: Write to application log
 Use to check what data is passed on click
 Best way to debug data flow
 ```
 [31:39]
 
 **Element Types:**
 ```
 Know the difference:
 - Form elements (input fields) → Use "Set value of input field"
 - Layout elements (text blocks) → Use "Set text on text element"
 ```
 [38:10]
 
 ### Best Practices
 
 **⚠️ Don't Click Auto-Layout:**
 ```
 Never click "Arrange blocks hierarchically" in action editor
 Unless you want your carefully placed blocks to be rearranged!
 ```
 [39:18]
 
 **Centering the Canvas:**
 ```
 If screen goes black when navigating to template:
 → Click "eye" icon → "Center"
 → Returns canvas to center of view
 ```
 [24:51]
 
 **Row Data Configuration:**
 ```
 ❌ Bad: Leave Row Data as "Free Input"
 ✅ Good: Switch to "Parameter Input" and define structure
 
 Why: NoCode-X needs to know field names to show them in dropdowns
 ```
 [32:35]
 
 ### Common Patterns
 
 **Pattern: Master-Detail View**
 ```
 Left side: Data Table (list of records)
 Right side: Details panel (selected record info)
 
 Interaction:
 1. Click row in table
 2. Row Data captured automatically
 3. Details panel updated with selected user data
 ```
 
 **Pattern: Editable Profile**
 ```
 Right panel contains:
 - Profile photo (image)
 - Name fields (inputs)
 - Country (dropdown)
 - Save button
 
 On Save: Update database record
 ```
 
 ### Quick CRM Dashboard Checklist
 
 **Design:**
 - [ ] Generate layout with AI prompt
 - [ ] Set up Horizontal List container
 - [ ] Configure left/right panels
 - [ ] Add Data Table to left panel
 - [ ] Add detail components to right panel
 
 **Data:**
 - [ ] Create User Data Format
 - [ ] Generate test data (5+ users)
 - [ ] Upload profile photos to Media
 - [ ] Add photo URLs to user records
 
 **Logic:**
 - [ ] On Load: Fetch and populate table
 - [ ] Delete default table rows/columns
 - [ ] On Row Click: Capture Row Data
 - [ ] Configure Row Data structure
 - [ ] Update detail fields from Row Data
 - [ ] Test with Write to log
 
 **Polish:**
 - [ ] Use Replace placeholders for combined fields
 - [ ] Add loading states
 - [ ] Test all interactions
 - [ ] Check mobile responsiveness
 
---

