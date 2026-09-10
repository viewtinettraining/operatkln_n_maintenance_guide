---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Date Converter'
id: VKX-UXK-YCI-T8O
slug: date-converter
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 09:03:41'
---
---

# **<span align="center">Date Converter</span>**

<br />

The **Date Converter** grid handler is a critical component used to parse, transform, and format timestamps during the ETL process.

---

## **Context: Time-Series Database**

The Viewtinet database is a time-series database where the **mandatory timestamp field** is `created_at`. This field must always be provided in a **16-digit epoch format** (microseconds).

By default, the system handles the `created_at` field automatically depending on the data source:

-   **Polling Protocols (e.g., ICMP, SNMP):** The `viewtilog` process automatically populates the `created_at` field based on the exact moment the response is received from the queried device.
-   **Listening Protocols (e.g., Syslog, NetFlow):** The `viewtilog` process automatically assigns the `created_at` value based on the exact moment the event is received by the server.

### **Why use the Date Converter?**

While the automatic timestamp is useful, it represents the time the event was _received_ by Viewtinet, not necessarily the time the event _actually occurred_ on the source device.

If your incoming data payload already contains a specific timestamp (e.g., a transaction time, an initiation time, or a log generation time), you can use the **Date Converter** to parse that timestamp from the payload and overwrite the `created_at` field so that the event is accurately positioned in the time-series database.

<br />

---

## **Configuration Steps**

Configuring the **Date Converter** grid handler involves following these sequential steps:

1.  **Select the Grid-Handler**: Click on the "ADD NEW GRID-HANDLER" button and select **Date Converter** from the `Grid Handler Type` dropdown menu.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-step1a.png" align="center"></figure>

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-step1b.png" align="center"></figure>

<br />

2.  **Select the Date Column**: From the `Date Column` field, select the column from which you want to convert the timestamp.
3.  **Set the New Column**: In the `New Column` field, enter the name of the column in the database that will store the converted date. If you want to overwrite the timestamp inserted by Viewtinet, you must write `created_at`.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-step3.png" align="center"></figure>

<br />

4.  **Define Date Column Format**: In the `Date Column Format` field, insert the exact format of the timestamp as it comes from the ETL.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-step4.png" align="center"></figure>

<br />

5.  **Define New Date Column Format**: In the `New Date Column Format` field, insert the desired format for the converted date. If you selected `created_at` in step 3, you must insert the symbol `%s` (which is the 10-digit epoch time) and concatenate `000000`, leaving it as `%s000000`. In any other case, use the format you wish to display.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-step5.png" align="center"></figure>

<br />

---

## **Configuration & Formatting Reference**

The Date Converter allows you to extract a timestamp from a source column, parse it using standard formats, and output it to a new column with a different format.

For both the **Date Column Format** (parsing the input) and the **New Date Column Format** (writing the output), you can use the standard formatting filters from the **Linux** `date` command (e.g., `%Y`, `%m`, `%d`, `%H`, `%M`, `%S`).

<div class="sd-callout" data-callout-type="info"><strong>16-Digit Epoch Requirement:</strong> The <code>%s</code> wildcard represents a standard 10-digit epoch timestamp (seconds). Since the Viewtinet database requires a 16-digit epoch for the <code>created_at</code> field, it is extremely common to append six zeros to the output format like this: <code>%s000000</code>.</div>

<br />

---

## **Practical Examples**

### **Example 1: Parsing a Standard Date into** `created_at`

In this scenario, a column named `sale_date` contains a date in a standard format (e.g., `YYYY-MM-DD`). We want to parse it and convert it into the mandatory 16-digit epoch format to overwrite the event's timestamp.

-   **Date Column:** `sale_date`
-   **New Column:** `created_at`
-   **Date Column Format:** `%Y-%m-%d` (or `%D` depending on input)
-   **New Date Column Format:** `%s000000`

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-example1-v2.png" align="center"></figure>

<br />

### **Example 2: Human-Readable System Uptime**

The Date Converter also supports special parsing formats like `timeticks-centiseconds`, which is commonly used to parse the `system-uptime` value provided by SNMP devices. This allows converting device uptime ticks into a standard readable timestamp or another required format.

-   **Date Column:** `system-uptime`
-   **New Column:** `system_uptime_human`
-   **Date Column Format:** `timeticks-centiseconds`
-   **New Date Column Format:** `*` (Asterisk represents a default human-readable format mapping)

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-example2-v2.png" align="center"></figure>

<br />

### **Example 3: Parsing a Complex Timestamp string**

In this example, the data payload provides a very specific timestamp in the `Start Initiation Time` column (e.g., `20231025143000.123` format). We parse this precise timestamp including fractional seconds (`%f`) and convert it into the 16-digit epoch.

-   **Date Column:** `Start Initiation Time`
-   **New Column:** `timestamp`
-   **Date Column Format:** `%Y%m%d%H%M%S.%f`
-   **New Date Column Format:** `%s000000`

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-example3-v2.png" align="center"></figure>

<br />