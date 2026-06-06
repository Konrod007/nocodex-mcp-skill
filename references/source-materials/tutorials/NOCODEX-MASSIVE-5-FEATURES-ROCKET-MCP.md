# NoCode-X Just Got Massive: 5 Game-Changing Features

Source: user-provided transcript of the developer video `NoCode-X Just Got Massive! 5 New Game-Changing Features (Rocket Mode, MCP Tools & More)`.

Video URL: `https://www.youtube.com/watch?v=h83Q5K6WwY4`

Treat this as transcript-derived platform knowledge. Verify exact UI labels, function names, and current behavior in the live NoCode-X app before making production claims.

## Why This Video Matters

This short update is important because it introduces or demonstrates several practical platform surfaces:

- Standard Page / application dashboard when entering Visual Development mode;
- advanced built-in database query capabilities;
- page-level Action parameter values;
- Rocket Mode logic-generation improvements;
- expanded MCP tooling for AI agents inspecting and modifying NoCode-X applications.

Several concepts overlap with later notes already in the playbook, but this video gives concise source evidence and concrete examples.

## 1. Standard Page / Application Dashboard

When entering Visual Development mode, NoCode-X shows a new Standard Page / dashboard.

The dashboard includes:

- a short application description;
- recent versions of the application;
- which versions are deployed to which environments;
- three of the most urgent issues to solve;
- latest application log lines;
- visible indication when errors are happening;
- links to NoCode-X resources;
- buttons to edit the application, view versions, view issues, and view logs;
- log filtering by query.

Developer positioning:

- this dashboard is intended to become a go-to page for monitoring the application and surrounding operational state;
- more content/features are planned for the dashboard.

Practical use:

- Start application audits from this dashboard when rendered UI access exists.
- Use it as the first operational overview before drilling into Issues, Logs, Versions, Actions, Templates, Jobs, or APIs.
- In MCP-only analysis, do not claim the exact dashboard state unless the rendered UI has been inspected.

## 2. Advanced Built-In Database Queries

The video demonstrates the new/improved `get filtered` / `fetch a list of data records (new version)` action capability.

Demo data formats:

```text
Product
- name

Sale
- product_id
- customer_id
- amount
- total_price

Customer
- name
- type
```

The Sale rows are linked to Product and Customer records by IDs.

### Selecting Attributes

By default, the query fetches all record data. The new query settings allow selecting only needed attributes.

Practical use:

- Select only the attributes required for the UI/report/action output.
- Reduces payload size and helps performance.

### Aggregations

The transcript demonstrates aggregations on selected attributes:

- sum of `total_price`;
- average of `total_price`.

Example outcome described:

```text
SUM(total_price) -> one record with total sum
AVG(total_price) -> one record with average
```

Practical use:

- Prefer database-level aggregation for dashboards/reports instead of fetching all records and summing in Actions.

### Group By

The transcript demonstrates grouping sales by `product_id` and summing `total_price` per product.

Conceptual query:

```text
SELECT product_id, SUM(total_price)
FROM Sale
GROUP BY product_id
```

Practical use:

- Use grouping for totals per product, customer, status, source, type, period, role, etc.

### Distinct

The query UI supports `distinct` to avoid duplicate results.

Practical use:

- Use when the report/list requires unique values.
- Verify how `distinct` interacts with selected attributes, joins, and aggregations in the live app.

### Filters On Aggregations

The transcript distinguishes filtering the aggregation from filtering each individual row.

Example:

```text
Group by product_id
SUM(total_price)
Filter aggregate: SUM(total_price) > 500
```

This returns products whose total sales exceed 500, not individual sale rows whose price exceeds 500.

Practical use:

- Use for dashboard thresholds, e.g. customers with total spend > X, products with revenue > X, teams with open tickets > X.
- Be explicit whether the filter applies before aggregation or after aggregation.

### Joins

The video demonstrates joining Sale to Customer:

```text
Source format: Sale
Join target: Customer
Local field: Sale.customer_id
Target field: Customer.id
```

The query only returns matching records. If a Sale has an empty/non-matching `customer_id`, the example says result count drops.

Practical use:

- Use joins when one data format stores another format's ID and the UI/report needs fields or filters from both.
- Check whether the join behaves like an inner join in the current platform before relying on missing-row behavior.

### Filters On Joined Data

The transcript filters Sale rows by a field on joined Customer rows:

```text
Customer.type == "one-off"
```

The result includes sales linked to customers of that type.

Practical use:

- Useful for CRM, billing, reporting, segmentation, and permission-like filtering.

### Join On Join And OR Filters

The video states support for:

- join on a join;
- OR filters;
- combining joins with aggregations.

Practical use:

- Build complex reports incrementally: start with one table, add one join, then add filters, then aggregation/grouping.
- Test on small known datasets before using complex queries in production UI.

## 3. Page-Level Action Parameter Values

The video demonstrates passing explicit parameter values to Actions called from pages.

Pattern:

1. Create an Action with a parameter, e.g. `my_log_line` of type text.
2. Add an action step that writes the parameter to the application log.
3. Link the Action to a button/page event.
4. Expand the action binding in the page editor.
5. Fill input fields for the Action parameters.
6. Run the page and click the button; the log receives the explicit value.

Important details:

- each Action parameter becomes configurable in the page action binding;
- placeholders can be used in the field;
- LiquidJS can be used in the field;
- if the field is left empty, automatic inheritance from page parameters still works;
- this is described as backward compatible.

Practical use:

- Reuse one Action from multiple UI elements by passing different constants/placeholder values.
- Avoid cloning Actions just to change a small text, ID, status, or mode parameter.
- For debugging missing or wrong Action input values, inspect both the Action signature and the page action-binding parameter fields.

## 4. Rocket Mode Logic Improvements

The video says Rocket Mode improvements focused on higher-quality generated logic.

Developer-stated goals:

- generated logic should be more correct;
- logic should be more aligned with user intent;
- logic should work end-to-end with the built-in database;
- zero-shot prompts should increasingly produce working logic.

A future video is promised to showcase Rocket Mode generating built-in-database-backed logic out of the box.

Practical use:

- Continue treating Rocket Mode output as a draft that must be inspected and tested.
- Inspect generated data formats, actions, page bindings, logs, issues, and stored records before trusting the generated app.
- When prompting Rocket Mode, include data model, actions, pages, roles, test data, expected logs/tests, and acceptance criteria.

## 5. Expanded MCP Tools

The video demonstrates an external ChatGPT window configured with the NoCode-X MCP server.

Demonstrated MCP/agent capabilities:

- list available NoCode-X workspaces;
- switch workspace;
- switch application;
- list all Actions in an app;
- inspect an Action;
- see a TypeScript-like visualization of Action steps;
- request issues for an Action;
- list templates;
- inspect a named template;
- inspect template parameters/elements;
- list data schemas;
- inspect a data schema and see fields/example data;
- access jobs and APIs;
- inspect settings/elements enough for AI to help debug;
- request changes to create pages, databases, logic, or an entire application.

Example Action visualization described:

```text
start method
log_line
add_accordion_item
```

Example Template inspection described:

```text
named template
- no parameters
- two elements: button and HTML code
```

Example Data Schema inspection described:

```text
Sale
- product_id
- customer_id
- amount
- total_price
```

Practical use:

- For read-only debugging, inspect the current workspace/app and then list/get actions, templates, data schemas, jobs, APIs, issues, and logs.
- For mutating builder requests, gather facts first and make precise requests naming target objects.
- Distinguish MCP facts from rendered UI facts; use browser/preview for exact visual behavior when needed.
- Treat MCP write/build requests as mutating application changes.

## Skill Guidance Updates From This Source

This transcript supports or reinforces these skill guidance areas:

- Start app audits from Standard Page/dashboard when UI is available.
- Use advanced database queries for selected attributes, aggregation, grouping, aggregate filters, joins, nested joins, OR filters, and distinct results.
- Prefer database-level aggregation/filtering over fetching all rows and processing in Actions.
- Use page-level Action parameter values to reuse Actions safely across buttons/pages.
- Debug Action input problems by checking page-level bindings as well as Action definitions.
- Treat Rocket Mode logic as improving but still requiring verification.
- Use MCP-first inspection for app structure and debugging, then browser/preview for rendered UI facts.

## Verification Checklist For Live Apps

When using this source for a target NoCode-X app, verify:

- whether the Standard Page/dashboard is visible in the target account/environment;
- exact dashboard contents and issue/log status;
- whether the function picker labels match `get filtered` / `fetch a list of data records (new version)`;
- which aggregation functions are currently available;
- exact behavior of aggregate filters vs row filters;
- exact join behavior when local/target fields are empty or unmatched;
- whether OR filters and join-on-join are available in the current query UI;
- whether page-level Action parameter values support placeholders/LiquidJS in the current UI;
- whether automatic parameter inheritance still works when parameter value fields are empty;
- what MCP tools are actually registered in the current Hermes/NoCode-X configuration;
- whether MCP mutating/build requests are enabled and appropriate for the target app.
