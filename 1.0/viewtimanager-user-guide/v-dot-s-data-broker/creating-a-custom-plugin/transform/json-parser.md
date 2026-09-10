---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'JSON Parser'
id: JYR-UF1-IMM-QW3
slug: json-parser
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 10:11:39'
---
# **<span align="center">JSON Parser</span>**

<br />

The **JSON Parser** handler is specifically designed to extract nested elements from JSON strings located within a grid column. It parses the JSON structure, retrieves the desired values, and saves them into completely new columns with the appropriate data type.

> \[!NOTE\] The handler will **not** delete or modify the original source columns (the "from columns"); it will only create or modify the destination columns (the "to columns").

---

## **Configuration Parameters**

To extract elements from a JSON string, you must define the mapping rules in the configuration:

-   **JSON field separator**: The character used to separate nested levels when specifying the path to the element (e.g., `,` or `:`).
-   **Columns Section**: Click **\+ ADD NEW COLUMN** to define an extraction rule.
    
    -   **From-column name**: The source column in the grid that contains the JSON string (e.g., `payload` or `owner`).
    -   **JSON field**: The exact path or key inside the JSON structure to extract. For nested objects, you can use the defined separator to drill down (e.g., `type:id` if using `:` as the separator, or `payload.object.issue` using standard dot notation).
    -   **To-column name**: The name of the new column where the extracted value will be stored.
    -   **To-column type**: The data type to cast the extracted value into (e.g., `string`, `int`).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/json-parser-step1.png" align="center"></figure>

<br />

---

## **Expected Behaviour**

The following example describes the handler's behaviour in a practical scenario using `:` as the JSON field separator.

Given the following initial grid:

<table><tbody><tr><th><p>owner (string)</p></th><th><p>permissions (string)</p></th></tr><tr><td><p><code>{"user": "admin","tenant": "Viewtinet"}</code></p></td><td><p><code>{"type": {"id": "42","label": "devel"}}</code></p></td></tr><tr><td><p><code>{"user": "dev","tenant": "Client"}</code></p></td><td><p><code>{"type": {"id": "21","label": "labs"}}</code></p></td></tr></tbody></table>

<br />

If we configure the handler to extract three different fields:

1.  Extracting the `user` element from the `owner` column into a new string column called `owner_user`.
2.  Extracting the `type` element from the `permissions` column into a new string column called `permissions_type`.
3.  Extracting the nested `id` element inside `type` from the `permissions` column (using the path `type:id`) into a new integer column called `permissions_id`.

The resulting grid would be as follows:

<table><tbody><tr><th><p>owner (string)</p></th><th><p>permissions (string)</p></th><th><p>owner_user (string)</p></th><th><p>permissions_type (string)</p></th><th><p>permissions_id (int)</p></th></tr><tr><td><p><code>{"user": "admin","tenant": "Viewtinet"}</code></p></td><td><p><code>{"type": {"id": "42","label": "devel"}}</code></p></td><td><p><code>admin</code></p></td><td><p><code>{"id": "42","label": "devel"}</code></p></td><td><p><code>42</code></p></td></tr><tr><td><p><code>{"user": "dev","tenant": "Client"}</code></p></td><td><p><code>{"type": {"id": "21","label": "labs"}}</code></p></td><td><p><code>dev</code></p></td><td><p><code>{"id": "21","label": "labs"}</code></p></td><td><p><code>21</code></p></td></tr></tbody></table>

<br />

### **Explanation:**

-   The first new column, `owner_user`, contains the `user` element from the `owner` column, as specified by the JSON field `"user"`.
-   The second new column, `permissions_type`, contains the whole `type` nested object, converted to a string, as specified by the JSON field `"type"`.
-   The third new column, `permissions_id`, contains the `id` double-nested element, as specified by the JSON field `"type:id"`. Note the `:` separated element list used to traverse the JSON hierarchy.

<br />