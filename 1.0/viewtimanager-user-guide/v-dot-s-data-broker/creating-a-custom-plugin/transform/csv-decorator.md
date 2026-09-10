---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'CSV Decorator'
id: CSV-DEC0-GH1-TR4
slug: csv-decorator
isVisible: true
isSearchable: true
lastUpdated: '2026-05-20 18:40:04'
---
# **<span align="center">CSV Decorator</span>**

<br />

The **CSV Decorator** grid handler is a powerful transformation component that allows you to **map data** or **add extra information** to the Grid by using an external CSV file as a lookup source. This enables injecting dynamic content into a statically-configured ETL pipeline.

It works by performing a **LEFT OUTER JOIN** between the Grid data and the CSV file: for every row in the Grid, the handler looks up matching records in the CSV file based on a reference column obtained during the ETL process, and populates new columns with the corresponding values.

<br />

---

## **Configuration**

After selecting the **CSV Decorator** as Grid Handler Type, the following configuration panel is displayed:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-empty-config.png" align="center"></figure>

<br />

The available configuration fields are:

<table><tbody><tr><th><p>Field</p></th><th><p>Description</p></th></tr><tr><td><p><strong>CSV File Path</strong></p></td><td><p>Absolute path to the CSV file used as lookup source. Click the pencil icon ✏️ to create or edit the CSV file directly.</p></td></tr><tr><td><p><strong>Default value if not found</strong></p></td><td><p>Default value assigned to new Grid columns when there is no matching row in the CSV file.</p></td></tr><tr><td><p><strong>Delimiter</strong></p></td><td><p>Delimiter character used in the CSV file. Defaults to <code>,</code> (comma).</p></td></tr><tr><td><p><strong>Operation</strong></p></td><td><p>Logical operation used when matching multiple source columns (<code>AND</code> requires all columns to match).</p></td></tr><tr><td><p><strong>Source Columns</strong></p></td><td><p>Column(s) used as <strong>lookup keys</strong> to match CSV records with Grid records. Specify the <strong>CSV Name</strong> (column in the CSV file) and the <strong>Grid Name</strong> (column in the Grid).</p></td></tr><tr><td><p><strong>Destination Columns</strong></p></td><td><p>Column(s) to be <strong>created or updated</strong> in the Grid with matched CSV values. Specify the <strong>CSV Name</strong> and the desired <strong>Grid Name</strong>.</p></td></tr></tbody></table>

<br />

To configure the CSV Decorator, there are two main approaches depending on your goal: **Data Mapping** and **Data Enrichment**.

<br />

### **Configuration for Data Mapping**

To use the CSV Decorator to map values (e.g., replacing a numeric code with a label), follow these general steps:

<br />

**Step 1:** Click the **"+ ADD NEW GRID HANDLER"** button to add a new handler to the Transform stage, and select **CSV Decorator** from the Grid Handler Type dropdown.

<br />

**Step 2:** Once the CSV Decorator panel appears, click the **pencil icon** ✏️ next to the **CSV File Path** field to create a new CSV file (or use **"UPLOAD FILE"** to import an existing one).

<br />

**Step 3:** Define the CSV content that will serve as the mapping table. You can use the **TABLE** tab to add columns and rows visually, or switch to the **TEXT** tab to type the CSV content directly as shown below:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-csv-text.png" align="center"></figure>

<br />

**Step 4:** Configure the **Source Columns** and **Destination Columns** to define the lookup relationship, then set the **Default value if not found** and the **Delimiter** as needed.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-mapping-config.png" align="center"></figure>

<br />

**Step 5:** Click **"SAVE"** ✅ to apply the configuration.

<br />

**Use Cases for Data Mapping:**

-   **Interface Status Mapping:** Map SNMP numeric interface status codes (e.g., `1`, `2`, `3`) to their human-readable descriptions (`up`, `down`, `testing`).
-   **Layer 4 Protocol Mapping:** Map OSI Layer 4 protocol numbers (e.g., `6`, `17`, `1`) to their corresponding protocol names (`TCP`, `UDP`, `ICMP`).
-   **Any Numeric Code to Description:** Any scenario where a numeric or coded value obtained during the extraction process needs to be translated to a meaningful label for reporting or analysis purposes.

<br />

---

### **Configuration for Data Enrichment**

To use the CSV Decorator to add new columns with extra information, follow these general steps. This approach is commonly used to enrich data with contextual information from external sources. In most cases, the **IP address** is used as the lookup key, since it is a field frequently obtained during the ETL extraction process and serves as a reliable identifier to correlate with external reference data.

<br />

**Step 1:** Click the **"+ ADD NEW GRID HANDLER"** button to add a new handler to the Transform stage, and select **CSV Decorator** from the Grid Handler Type dropdown.

<br />

**Step 2:** Click the **pencil icon** ✏️ next to the **CSV File Path** field to create or upload the CSV file containing the enrichment data.

<br />

**Step 3:** Define the CSV content. The CSV should contain the lookup key (e.g., IP address) and the additional columns to be injected:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-enrichment-csv.png" align="center"></figure>

<br />

**Step 4:** Configure the **Source Columns** (e.g., matching the IP address) and multiple **Destination Columns** to inject the extra data. It is recommended to configure a **Default value if not found**:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-enrichment-config.png" align="center"></figure>

<br />

**Step 5:** Click **"SAVE"** ✅ to apply the configuration.

<br />

**Use Cases for Data Enrichment:**

-   **Geographic Data:** Add country, city, or region information based on the IP address.
-   **Site/Location:** Associate each host with its physical location, building, or data center.
-   **Department/Area:** Map hosts to the department, business unit, or organizational area they belong to.
-   **Roles:** Assign functional roles (e.g., `Hypervisor`, `Firewall`, `Active Directory`) to each host based on external reference data.
-   **Hardware/Software Inventory:** Add vendor, operating system, version, and device type information to enrich monitoring data.

<br />

---

## **Practical Examples**

The following sections present two practical examples that illustrate the two main use cases of the CSV Decorator: **Data Mapping** and **Data Enrichment**.

<br />

### **Example 1: Data Mapping**

In this example, the CSV Decorator is used to **map** the values of a Grid column to different values using an external CSV file. This is useful when you need to replace coded values with readable labels (e.g., replacing a numeric SNMP interface status code `1` with its meaning `up`).

<br />

The CSV file `ifAdminStatus.csv` contains two columns: `value` (the numeric code to look up) and `description` (the human-readable label to return):

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-mapping-ifstatus-csv.png" align="center"></figure>

<br />

The **Source Columns** and **Destination Columns** are configured as follows:

-   **Source Columns:** `CSV Name` = `value` and `Grid Name` = `interface-admin-status`. The handler matches the values in the CSV column `value` against the Grid column `interface-admin-status`.
-   **Destination Columns:** `CSV Name` = `description` and `Grid Name` = `interface_admin_status_desc`. The handler creates a new column `interface_admin_status_desc` in the Grid, populated with the matched `description` values from the CSV.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-mapping-ifstatus-config.png" align="center"></figure>

<br />

**Result:**

<table><tbody><tr><th><p>interface-admin-status</p></th><th><p>interface_admin_status_desc</p></th></tr><tr><td><p>1</p></td><td><p>up</p></td></tr><tr><td><p>2</p></td><td><p>down</p></td></tr><tr><td><p>3</p></td><td><p>testing</p></td></tr></tbody></table>

<br />

---

### **Example 2: Data Enrichment**

In this example, the CSV Decorator is used to **add new information** to the Grid by creating additional columns based on a reference field. Unlike data mapping (which replaces values), data enrichment **preserves the original column** and adds new columns with extra information.

This approach is commonly used to enrich data with information such as **geographic location**, **physical site or building**, **department/area/business unit**, **roles**, **operating system**, **vendor**, or any other contextual data from external sources. In most cases, the **IP address** is used as the lookup key, since it is a field frequently obtained during the ETL extraction process and serves as a reliable identifier to correlate with external reference data.

<br />

The CSV file `inventory_vn_training.csv` contains a complete inventory of network hosts with columns for `ip`, `hostname`, `operating_system`, `role`, `snmp`, `type`, `vendor`, and `version`. The IP address (`ip`) serves as the lookup key to match records against the Grid:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-enrichment-inventory-csv.png" align="center"></figure>

<br />

The **Source Columns** and **Destination Columns** are configured as follows:

-   **Source Columns:** `CSV Name` = `ip` and `Grid Name` = `host`. The handler matches the CSV column `ip` (containing IP addresses) against the Grid column `host` obtained during extraction.
-   **Destination Columns:** Seven new columns are added: `hostname`, `operating_system`, `role`, `snmp`, `type`, `vendor`, and `version`. Each injects the corresponding enrichment data from the CSV into the Grid.
-   **Default value if not found:** Set to `No_info` so that Grid rows without a matching IP in the CSV file receive a clear default label instead of being left empty.
-   **Delimiter:** Set to `:` as the CSV file uses colon as separator.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-enrichment-inventory-config.png" align="center"></figure>

<br />

**Result:**

The Grid now contains seven new columns with the enriched inventory data, while the original `host` column remains unchanged:

<table><tbody><tr><th><p>host</p></th><th><p>hostname</p></th><th><p>operating_system</p></th><th><p>role</p></th><th><p>type</p></th><th><p>vendor</p></th><th><p>version</p></th></tr><tr><td><p>192.168.1.10</p></td><td><p>training.view</p></td><td><p>PVE</p></td><td><p>Hypervisor</p></td><td><p>SuperMicro</p></td><td><p>Proxmox</p></td><td><p>8.1.4</p></td></tr><tr><td><p>10.30.23.1</p></td><td><p>cancerbero.v</p></td><td><p>FreeBSD</p></td><td><p>Training Firewall</p></td><td><p>Virtual Machine</p></td><td><p>Netgate-Pfsense</p></td><td><p>14.0</p></td></tr><tr><td><p>10.30.23.2</p></td><td><p>guacamole.v</p></td><td><p>Ubuntu</p></td><td><p>Remote Desktop</p></td><td><p>LX Container</p></td><td><p>Viewtinet</p></td><td><p>24.04</p></td></tr><tr><td><p>10.30.23.99</p></td><td><p><em>(unknown)</em></p></td><td><p>No_info</p></td><td><p>No_info</p></td><td><p>No_info</p></td><td><p>No_info</p></td><td><p>No_info</p></td></tr></tbody></table>

<br />

<div class="sd-callout" data-callout-type="info"><strong>Key Difference:</strong> In <strong>Data Mapping</strong> (Example 1), the Destination Column uses the <strong>same Grid Name</strong> as an existing column, so the original values are <strong>replaced</strong>. In <strong>Data Enrichment</strong> (Example 2), the Destination Column uses a <strong>new Grid Name</strong>, so new columns are <strong>added</strong> while preserving the original data.</div>

<br />

---

## **Multi-Column Lookup**

The CSV Decorator supports matching on **multiple columns simultaneously**. When multiple Source Columns are configured and the **Operation** is set to `AND`, **all values must match** for a CSV record to be considered a valid lookup hit.

For example, you could match on both `transport` and `port` to find the corresponding `service` in a CSV file.

The following CSV file (`iana-port-config.csv`) contains the multi-column mapping:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-ianaport-csv.png" align="center"></figure>

<br />

The Source Columns are configured to match both `transport` against `netflow.protocol` and `port` against `netflow.dst_port`. The Destination Column extracts the corresponding `service` into `dst_service`:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-ianaport-config-v2.png" align="center"></figure>

<div class="sd-callout" data-callout-type="tip"><strong>Best Practice:</strong> Use the CSV Decorator to dynamically enrich pipeline data with information from external sources, such as mapping IP addresses to geographic locations, translating SNMP status codes to human-readable labels, or adding vendor-specific metadata from a reference table. This avoids hardcoding values directly in the pipeline configuration and allows updating the lookup data by simply modifying the CSV file without redeploying the pipeline.</div>

<br />