# NoCode-X App Template Audit — 7 Apps — 2026-06-05

Status: inspected seven user-provided applications as app/block/template examples for platform reverse-engineering.

Workspace: `[REDACTED_WORKSPACE]` (`[REDACTED_ID]`)

## Summary Table

| App | ID | APIs | Schemas | Actions | Jobs | Templates | Issues | Main value |
|---|---|---:|---:|---:|---:|---:|---:|---|
| Root | `[REDACTED_ID]` | 0 | 0 | 0 | 0 | 6 | 0 | Text + copy-button HTML component |
| Templates | `[REDACTED_ID]` | 0 | 0 | 0 | 0 | 5 | 0 | Simpler copy-button template |
| Actions | `[REDACTED_ID]` | 0 | 0 | 14 | 0 | 4 | 10 | Action primitives playground: routing, datatable, API response, HTTP, parameters |
| Templates | `[REDACTED_ID]` | 0 | 0 | 35 | 0 | 21 | 30 | Richest app: AI/admin/chat/instructions/logs/dialogs/pagination |
| Instructions | `[REDACTED_ID]` | 0 | 0 | 6 | 0 | 6 | 12 | Focused instructions editor pattern |
| Instructions | `[REDACTED_ID]` | 0 | 0 | 6 | 0 | 6 | 10 | Similar focused instructions editor pattern |
| Dynamic filters | `[REDACTED_ID]` | 0 | 1 | 1 | 0 | 4 | 3 | Clean dynamic filter primitive example |

## Main Findings

### 1. `be5c6a14...` is the best app-template example so far

Application name: `Templates`.

Inventory:

```text
APIs:       0
Schemas:   0
Actions:   35
Jobs:      0
Templates: 21
Issues:    30
```

Important templates:

```text
Pagable list
AI chat message
Chat with user component
Logged Out
Modified on Date by User
User Home
Agent data template
Admin home
Chat Log
Instructions
Agents
Common dialogue
Create Agent Dialog
Delete Agent dialogue
Human chat message
Chat log record
```

Important actions:

```text
Inquire AI
Create Conversation History
Add instruction and user message to thread
Human message received
Display chat log record
Insert a chat record
Load Agents
Add Agent to the list
Create a new Agent
Create Agent and close dialogue
Delete Agent
Delete Agent and close dialogue
Populate agents names
Add agent to dropdown
Add agent to the filter dropdown
Choose Agent
Prepare filters
Show Logs
Load Instructions and activate controls
Load Instructions for selected Agent
Update Instruction
Delete Instruction
Update modified instruction date UI
Activate Admin Dashboard
Activate Buttons for Agents page
Go to Admin Dashboard
Go to Agents page
To Instructions Page
To Chat Log page
Log out
Login again
```

Primitives:

```text
_start: 25
_logline: 14
_action: 6
_getfiltereddatav3: 5
_adddropdownchoice: 4
_enablebutton: 4
_getfirstfiltereddatav3: 4
_addtemplatecomponenttolistv2: 3
_enabletextfield: 3
_setansweroftextfield: 3
_routetopagev2: 3
_getanswerofdropdownfield: 3
_createobjectdata: 2
_deletedatav2: 2
_hidedialog: 2
_refreshpage: 2
_hidepartv2: 2
_showdialog: 2
_addtolistv2: 1
_createemptylist: 1
_createobjectfreev2: 1
_finduserbyid: 1
_formatDate: 1
_replaceplaceholders: 1
_setparameteroftemplatecomponent: 1
_settextoftextpart: 1
_addvaluetoobject: 1
_getdatav2: 1
_updatedata: 1
_getanswerofinputfield: 1
_scrollXto: 1
```

Platform patterns revealed:

```text
admin dashboard navigation
agent list management
modal/dialog create/delete flows
chat UI with human/AI message templates
chat log filtering and display
instructions editor
dropdown population from data
paginated/page-size list control
button/textfield enable/disable UI state
route-to-page navigation
show/hide dialogs
show/hide parts
add template component to list
create/list/update/delete data patterns
```

This app is not clean production-ready, but it is a very useful structural sample.

### 2. `a658eb3c...` is an action playground

Application name: `Actions`.

Inventory:

```text
APIs:       0
Schemas:   0
Actions:   14
Jobs:      0
Templates: 4
Issues:    10
```

Action signatures:

```text
Read a single Office: main(ID:string)
Add office item to the table: main(ITEM:Data)
Delete office: main()
Print Items: main(ITEM:Data)
init the page: main()
Read available offices: main()
TESTING PARAMETERS: main(INPUT:string)
Log textfield change: main()
Interact with AI: main(REQUEST:string)
Goto Offices: main()
call office API: main()
Goto home: main()
DATATABLE_CLICKED: main(ROW_CODE:string,COLUMN_CODE:string,ROW_DATA:any)
Unnamed Action: main()
```

Primitives:

```text
_start
_logline
_createstringvariable
_setapiresponse
_addrowtodatatable
_getfiltereddatav3
_routetopagev2
_httpcall
_getdatav2
_getansweroftextfield
_action
_getobjectfromlist
_settitleoftitlepart
```

Important new/valuable patterns:

```text
Data table row insertion via _addrowtodatatable
Datatable click handler signature: main(ROW_CODE:string,COLUMN_CODE:string,ROW_DATA:any)
API response setting via _setapiresponse
Page navigation via _routetopagev2
Text field read via _getansweroftextfield
Title text update via _settitleoftitlepart
Action parameter typing examples: string, Data, any row data
```

Even though templates are only default/error pages, the action layer is useful.

### 3. Instructions apps show a focused editor pattern

Applications:

```text
[REDACTED_ID] — Instructions
[REDACTED_ID] — Instructions
```

Both have:

```text
APIs:       0
Schemas:   0
Actions:   6
Jobs:      0
Templates: 6
Issues:    10–12
```

Templates:

```text
Modified on Date by User
Instructions
Error pages
LottieFiles component
```

The `Instructions` template includes:

```text
TOP_MENU_1
BUTTON_AGENTS_1
BUTTON_INSTRUCTIONS_1
BUTTON_SEE_CHAT_LOGS_1
BUTTON_CHAT_1
BUTTON_LOGOUT_1
AGENTS_DROPDOWN_CODE_1
INSTRUCTIONS_TEXT_FIELD_1
MODIFIED_TEMPLATE_CODE_1
BUTTON_UPDATE_INSTRUCTIONS
```

Reusable subtemplate:

```text
Modified on Date by User:
Agent ID: {{AGENT}}, Modified on {{TDATE}} by {{TUSER}}
```

Primitives include:

```text
_action
_getanswerofdropdownfield
_getfirstfiltereddatav3
_adddropdownchoice
_enabletextfield
_setansweroftextfield
_setanswerofdropdown
_finduserbyid
_formatDate
_replaceplaceholders
_setparameteroftemplatecomponent
_settextoftextpart
_addvaluetoobject
_getansweroftextfield
_getdatav2
_updatedata
_disabletextfield
_enablebutton / _disablebutton
```

Pattern:

```text
Load agents into dropdown
→ user selects agent
→ fetch instruction record
→ enable text field / button
→ populate text field
→ update data record
→ update Modified-on subtemplate with agent/date/user
```

This is valuable as a form/editor workflow pattern.

### 4. Dynamic filters app reveals `_addfiltertolist`

Application: `Dynamic filters` (`[REDACTED_ID]`).

Inventory:

```text
APIs:       0
Schemas:   1
Actions:   1
Jobs:      0
Templates: 4
Issues:    3
```

Schema:

```text
Users
fields:
- name
- firstName
```

Action:

```text
Filter users: main()
```

Primitives:

```text
_addfiltertolist
_getfiltereddatav3
_logline
_start
```

Pattern:

```text
create filter object/list dynamically
→ pass filters into getfiltereddatav3
→ fetch users matching dynamic conditions
```

This is a clean, specific example of dynamic query construction. However, validator says the Users data format is non-existing even though MCP lists it — same validator/schema mismatch class observed before.

### 5. Text/copy-button templates

Applications:

```text
Root — [REDACTED_ID]
Templates — [REDACTED_ID]
```

They mostly contain non-action HTML templates:

```text
Text and copy button
Unnamed template
```

Observed codes:

```text
VERTICAL_LIST_CODE_1
HORIZONTAL_LIST_CODE_1
TEXT_PART_CODE_1
HTML_CODE_1
TRISTANS_CODE / TRISTANS_CODE_1
TEMPLATE_CODE_1
```

Pattern:

```text
Text block + custom HTML/SVG/JS copy button
```

Useful as small UI component examples, not as full app patterns.

## Recurring Problems

### Validator/data-format mismatch

Seen again in:

```text
Dynamic filters → Users schema exists in MCP, but validator says non-existing data format.
```

Previously also seen in:

```text
Jobs-Steve → application_log
Root → Ideas
```

This is now a repeated platform defect candidate.

### Broken/missing action references

Instructions/admin apps show many issues like:

```text
Execute action references non-existing action <uuid>
Action references template <uuid> that does not exist
```

This suggests these app templates may have been copied/imported without preserving internal object IDs, or cleanup/import left dangling references.

### Deprecated primitives still common

Frequent deprecated methods:

```text
_getfiltereddatav3
_createobjectdata
_createobjectfreev2
_addtemplatecomponenttolistv2
```

### UI element references missing

Issues include:

```text
Required argument "UI element" was empty
Required argument "List ui element" was empty
```

## New / Important Platform Primitives From This Batch

```text
_addrowtodatatable
_setapiresponse
_routetopagev2
_getansweroftextfield
_settitleoftitlepart
_adddropdownchoice
_enablebutton
_disablebutton
_enabletextfield
_disabletextfield
_setansweroftextfield
_setanswerofdropdown
_setparameteroftemplatecomponent
_showdialog
_hidedialog
_refreshpage
_hidepartv2
_scrollXto
_addfiltertolist
_addtolistv2
_createemptylist
_deletedatav2
_finduserbyid
```

These app examples are more useful than marketplace plugins for UI/control-flow primitives.

## Recommended Deep Dives

1. Deep-dive `be5c6a14...` (`Templates`) first:
   - map pages/templates;
   - map navigation actions;
   - map chat flow;
   - map agent CRUD;
   - map dialog patterns;
   - map chat log filtering.

2. Deep-dive `a658eb3c...` (`Actions`) second:
   - datatable click signature;
   - add row to datatable;
   - set API response;
   - page routing;
   - action parameter typing.

3. Deep-dive `2a8c59a...` (`Dynamic filters`) third:
   - `_addfiltertolist` recipe;
   - dynamic filters + getfiltereddatav3;
   - document validator mismatch.

4. Use the two `Instructions` apps as focused form/editor examples, but they are partial duplicates of the richer `be5c6a14...` app.

## Verdict

```text
This batch is significantly more useful than the previous 3-app batch because it includes one rich multi-page admin/chat/instructions app and several focused primitive examples.
```

Ratings:

```text
Насколько полезно для понимания платформы: 9/10
Насколько полезно как готовые app templates: 5/10
Насколько полезно для reusable patterns: 9/10
Production readiness: 2/10
```
