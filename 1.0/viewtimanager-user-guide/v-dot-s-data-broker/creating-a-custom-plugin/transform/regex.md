---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Regex
id: 2CV-MCK-FEE-ZSX
slug: regex
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 11:17:32'
---
# **<span align="center">Regex</span>**

<br />

The **Regex** grid handler allows you to extract and map values from a string column using regular expressions, creating new columns in the process.

This is highly useful for parsing complex or unstructured string data, such as custom log formats, Syslog messages, or unformatted text payloads, into individual searchable database fields.

---

## **Configuration Parameters**

The handler (internally known as `grid-regex`) has the following configuration parameters:

-   **Regex Column**: The name of the column to apply the regular expressions to.
-   **Output Fields**: Semicolon-separated list of new columns to create from regex matches.
-   **Regex Group**: Defines a regular expression identifier and how to map its capture groups to output columns. You can define multiple _regex-group_ blocks to try several regexes in order.
-   **Regular Expression**: The regex pattern to apply.
-   **Regex Field**: Maps a capture group (by index, starting from 1) to an output column.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/regex-step1.png" align="center"></figure>

<br />

When you click the pencil icon () next to a Regex Group, you can edit the specific mapping of capture groups to their respective output column names:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/regex-step2.png" align="center"></figure>

<br />

---

## **Expected Behaviour**

Given the previous example configuration (`MySQL` regex group on the `syslog_record` column) and the following grid:

<br />

<table><tbody><tr><th><p>syslog_record</p></th></tr><tr><td><p><code>&lt;30&gt;Dec 29 16:58:56 LOPOIDCBD01 mysqld_exporter[1201]: ts=2025-12-29T21...</code></p></td></tr></tbody></table>

<br />

The resulting grid will be:

<table><tbody><tr><th><p>syslog_record</p></th><th><p>priority</p></th><th><p>datetime</p></th><th><p>hostname</p></th><th><p>process</p></th><th><p>pid</p></th><th><p>message</p></th></tr><tr><td><p><code>&lt;30&gt;Dec 29 16:58:56 LOPOIDCBD01 mysqld_exporter[1201]: ts=2025-12-29T21...</code></p></td><td><p><code>&lt;30&gt;</code></p></td><td><p><code>Dec 29 16:58:56</code></p></td><td><p><code>LOPOIDCBD01</code></p></td><td><p><code>mysqld_exporter</code></p></td><td><p><code>1201</code></p></td><td><p><code>ts=2025-12-29T21...</code></p></td></tr></tbody></table>

<br />

### **Explanation:**

-   The handler applies the regex `^(\&lt;\d+\&gt;)\s(\w{3}\s+\d+\s+[\d:]+)\s+([^\s]+)\s+([^[\s:]+)(?:[(\d+)])?:\s+(.)$` to each value in the `syslog_record` column.
-   For each match, it extracts the capture groups by their index (starting from 1) and assigns them to the columns defined in the `Regex Fields` section (`priority`, `datetime`, `hostname`, `process`, `pid`, `message`).
-   If the regex does not match (e.g., `invalid_data`), the new columns are left empty for that row.
-   **The original column is preserved;** new columns are appended to the grid without modifying or removing the source data.

<br />