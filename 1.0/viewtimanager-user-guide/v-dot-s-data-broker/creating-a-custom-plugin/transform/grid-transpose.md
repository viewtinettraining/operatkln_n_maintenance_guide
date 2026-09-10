---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grid Transpose'
id: 9XM-YVZ-OY1-MTB
slug: grid-transpose
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 11:10:35'
---
# **<span align="center">Grid Transpose</span>**

<br />

The **Grid Transpose** handler fundamentally reshapes the structure of your data grid. It converts a wide row containing multiple individual columns into a long "key-value" format (often referred to as an Entity-Attribute-Value model), creating multiple rows out of a single original row.

## **When to use it?**

This handler is extremely useful when integrating with time-series databases or monitoring systems that expect data in a strict `metric_name` and `metric_value` schema rather than wide tables. By transposing the grid, you normalize highly dimensional data into a standard, scalable key-value structure.

---

## **Configuration Parameters**

To configure the handler, you need to define which column(s) will act as the anchor point for the transposition:

-   **Grid Handler Type**: Select `Grid Transpose`.
-   **Keys**: Select the column that should be maintained as the constant primary key across all newly generated transposed rows. Generally, the `timestamp` column is selected here to ensure that all the newly generated metric rows maintain the exact temporal key of the original event.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-transpose-step1.png" align="center"></figure>

<br />

---

## **Expected Behaviour**

The following example demonstrates how a wide grid row is transposed into a long structure.

**Original Grid (Wide format):**

<table><tbody><tr><th><p>timestamp</p></th><th><p>host</p></th><th><p>name</p></th><th><p>network</p></th><th><p>rtt_min</p></th><th><p>rtt_avg</p></th><th><p>rtt_max</p></th><th><p>rtt_mdev</p></th><th><p>packet_loss</p></th><th><p>reply</p></th><th><p>status</p></th><th><p>hostname</p></th><th><p>operating_system</p></th><th><p>role</p></th><th><p>snmp</p></th><th><p>type</p></th><th><p>vendor</p></th><th><p>version</p></th></tr><tr><td><p><code>1779447362814887</code></p></td><td><p><code>10.30.23.151</code></p></td><td><p><br></p></td><td><p><br></p></td><td><p><code>430</code></p></td><td><p><code>584</code></p></td><td><p><code>1110</code></p></td><td><p><code>263</code></p></td><td><p><code>0</code></p></td><td><p><code>1</code></p></td><td><p><code>alive</code></p></td><td><p><code>rds151.viewtinet.local</code></p></td><td><p><code>Windows</code></p></td><td><p><code>Remote Desktop for Student</code></p></td><td><p><code>NO</code></p></td><td><p><code>Virtual Machine</code></p></td><td><p><code>Microsoft</code></p></td><td><p><code>10</code></p></td></tr></tbody></table>

<br />

When applying the **Grid Transpose** handler with the `Keys` set to `timestamp`, the grid generates a completely new structure with default column names `field`, `value`, and `field_value`:

**Transposed Grid (Long format):**

<table><tbody><tr><th><p>timestamp</p></th><th><p>field</p></th><th><p>value</p></th><th><p>field_value</p></th></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>host</code></p></td><td><p><code>10.30.23.151</code></p></td><td><p><code>host=10.30.23.151</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>name</code></p></td><td><p><br></p></td><td><p><code>name=</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>network</code></p></td><td><p><br></p></td><td><p><code>network=</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>rtt_min</code></p></td><td><p><code>380</code></p></td><td><p><code>rtt_min=380</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>rtt_avg</code></p></td><td><p><code>1440</code></p></td><td><p><code>rtt_avg=1440</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>rtt_max</code></p></td><td><p><code>5090</code></p></td><td><p><code>rtt_max=5090</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>rtt_mdev</code></p></td><td><p><code>1826</code></p></td><td><p><code>rtt_mdev=1826</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>packet_loss</code></p></td><td><p><code>0</code></p></td><td><p><code>packet_loss=0</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>reply</code></p></td><td><p><code>1</code></p></td><td><p><code>reply=1</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>status</code></p></td><td><p><code>alive</code></p></td><td><p><code>status=alive</code></p></td></tr></tbody></table>

> _Note: For the sake of brevity, only the first 10 fields are shown, but the handler iterates through all original columns._

<br />

### **Explanation:**

-   The configured key (`timestamp`) is preserved as the anchor in every new row.
-   The original column name becomes the `field`.
-   The original data inside that column becomes the `value`.
-   The handler automatically creates a `field_value` column concatenating both using an `=` sign.

<br />