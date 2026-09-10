---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Schema Intro'
id: FC4-5QC6-JEY-R9H
slug: schema-intro
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 14:24:18'
---
# **<span align="center">Schema Stage</span>**

<br />

The **Schema** stage is the final configuration step of a plugin within the V.S. Data Broker. This stage serves two main critical purposes:

1.  **Database Configuration:** It defines how the table is structured, its retention policies, and the partitioning periods inside the Viewtinet time-series database.
2.  **Data Preparation for Viewtisight:** It specifies the exact formatting, dimensions, metrics, aggregated tables, and real-time alarms that will be available later for visualization and analysis in Viewtisight.

<br />

---

## **Model Settings**

The initial section controls the core database structure and retention logic.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-viewticore-config.png" align="center"></figure>

<br />

### **Table & Raw Data Configuration**

-   **Set:** The name of the destination table in the database (e.g., `snmp_interface_records_info`).
-   **Tenant Field:** Defines which column acts as the **tenant identifier** to logically separate data within the same table. This is commonly set to `host`.
-   **Retention Period for Raw Data:** Specifies how long the **raw (unprocessed) records** will be kept before being automatically purged (e.g., `5 days`).
-   **Partition Period for Raw Data:** Defines the internal partitioning interval used by the database engine to optimize query performance (e.g., `1 day`).

### **Granularities and Aggregated Tables Policy**

This section controls the creation and retention of **aggregated tables** at different time granularities.

> \[!NOTE\] **Not All Data Should Be Aggregated**<br />
> As explained in the conceptual theory, **not all data sources are susceptible to be aggregated**. Aggregation is mandatory for high-volume listener protocols (NetFlow, Syslog) or frequent polling operations (SNMP interfaces) to compress the data, but it is typically disabled for lightweight polling (SNMP health, ICMP).

Each row represents an aggregation level that can be individually **enabled or disabled**:

<table><tbody><tr><th><p>Granularity</p></th><th><p>Retention Period</p></th><th><p>Partition Period</p></th><th><p>Enabled</p></th></tr><tr><td><p>1 minute</p></td><td><p>3 days</p></td><td><p>1 day</p></td><td><p>☐</p></td></tr><tr><td><p>5 minutes</p></td><td><p>1 week</p></td><td><p>1 day</p></td><td><p>☑</p></td></tr><tr><td><p>1 hour</p></td><td><p>1 week</p></td><td><p>1 day</p></td><td><p>☑</p></td></tr><tr><td><p>1 day</p></td><td><p>1 day</p></td><td><p>1 day</p></td><td><p>☑</p></td></tr></tbody></table>

<br />

---

## **Fields**

The **Fields** section is where you review and configure every column that will exist in the database table. These fields are inherited from the grid produced during the Transform stage.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-fields-config.png" align="center"></figure>

<br />

For each column, you can configure:

-   **Field Name:** The internal name of the column in the V.S. Data Broker.
-   **DataBase Name:** The actual column name that will be created in Postgres/ViewtinetDB.
-   **Type:** The SQL data type (e.g., `int64`, `string`, `double`).
-   **Max Length / Precision / Scale:** Optional constraints for string lengths or decimal precision.
-   **Metric/Dimension:** A crucial setting for Viewtisight. A **Dimension** is an attribute used to group or filter data (e.g., `host`, `interface_description`). A **Metric** is a numerical value that can be mathematically operated on.
-   **Agg. Function:** If the field is marked as a Metric, assigning a predefined Aggregation Function (like `sum`, `avg`, `max`) automatically prepares this metric to be used efficiently in Viewtisight dashboards.
-   **Units:** Defines the unit label (e.g., `bps`, `bytes`, `ms`).

<br />

---

## **Aggregated Tables (Dimensions & Metrics)**

If you enabled any granularities in the Model Settings, this section allows you to define exactly **how** those aggregated tables will be built.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-aggregated-tables-fields.png" align="center"></figure>

<br />

Here, you select which specific **Dimensions** and **Metrics** from your main table will be summarized and pushed into the secondary aggregated tables.

By default, the platform groups the records based on the selected dimensions over the defined time interval (e.g., every 5 minutes), applies the `Agg. Function` to the metrics, and stores the compressed results. This reduces volume and dramatically speeds up long-term trend queries.

<br />

---

## **Alarms**

The Schema stage also allows you to define **real-time alarms**.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarms-config.png" align="center"></figure>

<br />

Alarms configured here are evaluated **at insertion time**. This means that as soon as the system writes the record into the database, it instantly evaluates the metric against the configured threshold.

-   **Alarm name:** The identifier for the alarm (e.g., `Interfaz caído`).
-   **Metrics:** The specific column being evaluated (e.g., `interface-oper-status`).
-   **Dimension Keys:** The dimensions that provide context to the alarm, allowing you to know exactly which device or interface triggered it (e.g., `host`, `interface`, `interface-description`).

<br />