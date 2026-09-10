---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grid Filter'
id: GL2-GM1-6UV-GSJ
slug: grid-filter
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 12:00:00'
---
# **<span align="center">Grid Filter</span>**

<br />

The **Grid Filter** handler is a powerful tool designed to selectively keep or discard incoming records (rows) based on specific logical conditions before they are sent to the database.

By setting up dimension filters, you can ensure that only valid, relevant, or compliant data is ingested. Any row that does not meet the specified criteria is completely dropped from the payload during the transformation phase.

---

## **When to use it?**

You should use this handler to:
- **Drop anomalies**: For example, filtering out logs where a percentage metric like CPU or Storage utilization reports a value higher than 100%.
- **Reduce noise**: Discarding irrelevant log levels (e.g., keeping only `ERROR` or `CRITICAL` severity logs and dropping `INFO` or `DEBUG`).
- **Targeted ingestion**: Only ingesting events that belong to a specific tenant or IP subnet.

<br />

## **Configuration Parameters**

The configuration is divided into two parts: the global logical operation and the individual conditions.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-filter-step1.png" align="center"></figure>

<br />

### **1. Global Operation**
- **Operation**: Determines how the system should evaluate multiple conditions if you define more than one. 
  - `AND (match all)`: The row is kept *only* if it satisfies **all** the conditions simultaneously.
  - `OR (match any)`: The row is kept if it satisfies **at least one** of the conditions.

### **2. Conditions (Dimension Filters)**
You can define one or more rules by clicking the **+ ADD NEW DIMENSION FILTER** button. For each rule, you must configure:

- **Column**: The name of the column you want to evaluate (e.g., `storage_utilization`).
- **Filter Type**: Determines how the value will be processed and compared. For example, `int-compare` treats the value as an integer for mathematical comparison.
- **Case Sensitive**: Determines whether string comparisons should distinguish between uppercase and lowercase letters.
- **Match Mode**: Defines string matching behaviors (like exact match, starts with, etc.).
- **Compare Operation**: The mathematical or logical operator used for the evaluation (e.g., `<=`, `>=`, `==`, `!=`).
- **Value**: The threshold, string, or number to compare the column's content against (e.g., `100`).
- **Invert Filter**: If set to `true`, it logically negates the rule (e.g., turning a `<=` into a `>`). By default, it should be `false`.

In the example image provided above, the handler is configured to keep **only** the rows where the `storage_utilization` is less than or equal to `100` (`<= 100`). Any row reporting a value of `101` or higher will be automatically discarded.