---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Split
id: P8G-AJA-YBT-F5B
slug: split
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 13:53:43'
---
# **<span align="center">Split</span>**

<br />

The **Split** grid handler allows you to subdivide a single grid column into one or more fragments by using a specific delimiter (separator) character. It then takes a specific fragment (based on its numerical index) and saves it into a completely new column within your database grid.

---

## **Configuration Parameters**

To configure the **Split** grid handler, you must define the following parameters:

-   **Split Column**: The original column that contains the text string you want to subdivide (e.g., `syslog_record`).
-   **Separator**: The exact character or string used as the delimiter to split the text (e.g., `%`, `,`, `|`, or `-`).
-   **Field Idx**: The numerical index of the fragment you want to extract. **Note that the index starts at** `1`.
-   **New Column Name**: The name of the new column where the extracted fragment will be stored.

You can add the `Split` grid handler multiple times if you need to extract several different indices from the same original column into different new columns.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/split-step1.png" align="center"></figure>

<br />

---

## **Expected Behaviour**

To better understand how the **Split** grid handler behaves, let's use a fictitious log message based on the configuration shown in the image above.

Suppose our `syslog_record` column contains the following event structure where fields are separated by a `%` character: `[EVENT_TYPE]%[EVENT_NAME]%[IP_ADDRESS]`.

Given the following grid:

<table><tbody><tr><th><p>syslog_record</p></th></tr><tr><td><p><code>SystemAlert%DiskFailure%10.0.0.5</code></p></td></tr><tr><td><p><code>Authentication%UserLogin%192.168.1.20</code></p></td></tr><tr><td><p><code>invalid_log_format</code></p></td></tr></tbody></table>

<br />

If we apply the two Split configurations shown in the image:

1.  Extracting **Index 1** into a new column named `event_type` using `%` as the separator.
2.  Extracting **Index 2** into a new column named `event` using `%` as the separator.

The resulting grid will be:

<table><tbody><tr><th><p>syslog_record</p></th><th><p>event_type</p></th><th><p>event</p></th></tr><tr><td><p><code>SystemAlert%DiskFailure%10.0.0.5</code></p></td><td><p><code>SystemAlert</code></p></td><td><p><code>DiskFailure</code></p></td></tr><tr><td><p><code>Authentication%UserLogin%192.168.1.20</code></p></td><td><p><code>Authentication</code></p></td><td><p><code>UserLogin</code></p></td></tr><tr><td><p><code>invalid_log_format</code></p></td><td><p><code>invalid_log_format</code></p></td><td><p><br></p></td></tr></tbody></table>

<br />

### **Explanation:**

-   For the first row (`SystemAlert%DiskFailure%10.0.0.5`), the string is split by `%` into three parts: `SystemAlert` (Index 1), `DiskFailure` (Index 2), and `10.0.0.5` (Index 3). The handler accurately extracts Index 1 into `event_type` and Index 2 into `event`.
-   For the row containing `invalid_log_format` (which lacks the separator), the string cannot be split. Therefore, the entire original string acts as Index 1 (placed in `event_type`), and since there is no Index 2, the `event` column remains empty.
-   The original `syslog_record` column is fully preserved.

<br />