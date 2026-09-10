---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Delta
id: O5N-F9C-S8E-1VL
slug: delta
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 08:29:56'
---
# **<span align="center">Delta</span>**

<br />

The **Delta** grid handler is a powerful component that calculates the difference (delta) between the value of a field in the current iteration and its value in the previous iteration during the ETL process.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/delta.png" align="center"></figure>

<br />

---

### **Configuration**

Configuring the **Delta** grid handler involves following these sequential steps:

1.  **Select the Grid-Handler**: Click on the "ADD NEW GRID-HANDLER" button and select **Delta** from the `Grid Handler Type` dropdown menu.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/delta-step1a.png" align="center"></figure>

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/delta-step1b.png" align="center"></figure>

<br />

2.  **Select the Keys**: From the `Keys` dropdown, select the key(s) that you wish to use as groupers for the metric or counter. These keys uniquely identify the entity for which the delta is calculated (e.g., `host` and `interface`).
3.  **Select the Column**: From the `Column` dropdown, choose the numeric field on which the delta operation will be performed.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/delta-step3.png" align="center"></figure>

<br />

---

### **Use Case Example: SNMP Counters**

A common scenario for the Delta grid handler is processing SNMP counters. When retrieving metrics like inbound and outbound octets from network interfaces via SNMP, the values returned are typically **cumulative counters** since the last time the SNMP agent was restarted.

To obtain the real, absolute amount of traffic (octets) transmitted between each ETL polling interval, you must calculate the delta.

#### **Why combine multiple Keys?**

In this scenario, a network device (host) can have multiple interfaces. Therefore, the state must be tracked using a combination of the `host` and `interface` keys together:

-   If only the `interface` key were used, the delta calculation could become corrupted, as multiple distinct devices might share identical interface names (e.g., `eth0`).
-   By combining `host` and `interface` as the **Keys**, the Delta grid handler correctly computes the difference for each unique interface on each unique device.

<br />

<div class="sd-callout" data-callout-type="tip"><strong>Best Practice:</strong> Always evaluate your specific environment and data model. The combination of keys needed to uniquely track state varies depending on the nature of the data sources.</div>

<br />