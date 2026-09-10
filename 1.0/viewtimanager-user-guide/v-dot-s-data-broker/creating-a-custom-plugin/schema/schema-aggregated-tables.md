---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Creating Aggregated Tables'
id: SCH-AGG-TBL-003
slug: schema-aggregated-tables
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 17:36:00'
---
# **<span align="center">Creating Aggregated Tables</span>**

<br />

In high-volume environments, querying raw data spanning long periods (weeks or months) can be resource-intensive. To optimize performance and visualization speed, the **Schema Stage** allows for the creation of **Aggregated Tables**.

<br />

---

## **What are Aggregated Tables?**

Aggregated tables store **pre-processed, summarized data** derived from detailed raw records. Instead of keeping millions of individual data points, the platform calculates summaries (using functions like `sum()`, `avg()`, `count()`) at regular intervals and stores the results.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-concept.png" align="center"></figure>

<br />

By querying these optimized tables instead of the raw data, dashboards load significantly faster and the volume of stored data is drastically reduced.

<br />

---

## **Granularities in Aggregated Tables**

Aggregated tables are created based on different time **granularities**. The platform can automatically generate secondary tables that summarize the data at various intervals:

-   Every 60 seconds (1-minute detail)
-   Every 5 minutes (medium granularity)
-   Every 1 hour
-   Every 24 hours (daily trend)

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-example.png" align="center"></figure>

<br />

Using the `snmp_interface_records_info` table as an example, the system appends the granularity in seconds to the table name (e.g., `_agg_if_300` for 5 minutes, `_agg_if_3600` for 1 hour). Viewtisight will automatically query the most appropriate table depending on the time range selected in the dashboard.

<br />

---

## **Enabling Aggregated Tables**

You can selectively enable or disable the creation of aggregated tables for each specific granularity using the **Enabled** checkboxes in the Model Settings.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-enabled.png" align="center"></figure>

<br />

> [!WARNING] **Consider Polling Frequency**
> It is crucial to consider the frequency of data collection before enabling an aggregated table.
> - **Minimum Granularity:** If the Extract stage collects data via SNMP every **5 minutes**, this represents your minimum possible granularity. It makes no sense to enable the 1-minute aggregation table because no new data arrives at that speed.
> - **Useless Aggregation:** For data like SNMP Interfaces, even if data is collected every minute, there is usually only one record per interface per minute. Aggregating one record into a 1-minute table provides no compression or performance benefit, so the 1-minute aggregation should be disabled.

<br />

---

## **Retention Policies per Granularity**

Finally, one of the biggest advantages of aggregated tables is that they allow you to maintain long-term historical data without consuming massive amounts of disk space. 

Using the **Retention Period** dropdowns, you can define exactly how long the data should be kept on the hard drive for each specific granularity.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-retention.png" align="center"></figure>

<br />

A common configuration strategy is:
-   **1 Minute:** Kept for only a few days (if enabled).
-   **5 Minutes:** Kept for several months.
-   **1 Hour / 1 Day:** Kept for years, allowing for long-term historical trend analysis and capacity planning with a minimal storage footprint.

<br />

---

## **Step-by-Step Configuration**

To manually define the structure of an aggregated table, follow these steps:

**Step 1:** Scroll down to the **Aggregated Tables** section and click the **ADD AGGREGATED TABLE** button.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-add-button.png" align="center"></figure>

<br />

**Step 2:** A new configuration block will appear. You can change the default **Aggregated table name** if needed.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-name.png" align="center"></figure>

<br />

**Step 3:** The system provides one default empty field. Clicking on the dropdown will display all the Dimensions and Metrics available from the main table. 

> [!IMPORTANT] **Configuration Order**
> You must configure **Dimensions first**, followed by the **Metrics**. 

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-field.png" align="center"></figure>

<br />
<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-list.png" align="center"></figure>

<br />

**Step 4:** To add additional dimensions or metrics to your aggregated table, simply click the **ADD NEW FIELD** button at the bottom of the table block. 

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-new-field.png" align="center"></figure>

<br />

**Step 5:** Continue adding all the desired **Dimensions** first.

> [!TIP] **Tenant Field First**
> It is highly recommended to place the field that identifies the **tenant** (e.g., `tenant`, `customer_id`) as the very first dimension in the list. This optimizes query performance in multi-tenant environments.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-dimensions.png" align="center"></figure>

<br />

**Step 6:** Once all dimensions are defined, you can start adding your **Metrics**. For every metric you add, you must select the required **Aggregation Function** (e.g., `sum`, `avg`, `max`, `count`) that will be used to compress the data points into a single summarized value.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-metric-select.png" align="center"></figure>

<br />
<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-metrics.png" align="center"></figure>

<br />
<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-function.png" align="center"></figure>

<br />
