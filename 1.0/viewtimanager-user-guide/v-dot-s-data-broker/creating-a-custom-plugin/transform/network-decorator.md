---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Network Decorator'
id: NET-DEC0-GH1-TR4
slug: network-decorator
isVisible: true
isSearchable: true
lastUpdated: '2026-05-20 20:30:00'
---
# **<span align="center">Network Decorator</span>**

<br />

The **Network Decorator** grid handler is a powerful transformation component that shares the same underlying concept as the CSV Decorator, but is specifically designed for **IP address and Subnet matching**. 

It takes a Grid column containing an IP address and compares it against a reference CSV file containing subnets or specific IP addresses in CIDR notation (e.g., `/24`, `/16`, or `/32` for a single host). If the Grid IP address falls within a defined subnet in the CSV file, the handler adds the corresponding descriptive information to new Grid columns.

<br />

---

## **Use Cases**

This handler is generally used to enrich IP addresses with contextual information, such as:
-   **Subnet Belonging:** Identifying which network segment an IP address belongs to (e.g., `Madrid Network`, `Miami Network`).
-   **Department or Area:** Mapping IP addresses to specific departments (e.g., `HR Subnet`, `IT Servers`).
-   **Location / Site:** Associating traffic or logs with physical locations or branches based on the IP address.
-   **Device Identification:** Using a `/32` mask to identify specific hosts or critical devices within the network.

<br />

---

## **Configuration & Practical Example**

To configure the Network Decorator, you must define the lookup CSV file and map the source IP column to the destination descriptive columns.

<br />

### **Step 1: The Reference CSV File**

The lookup CSV file must contain at least two columns: one for the network/IP in CIDR notation, and one (or more) for the descriptive information to be added. 

In this example, the CSV file `network_decorator_example.csv` contains a `net` column with the subnets and a `descriptive_field` column with the location names:

-   `192.168.32.0/24` -> `Madrid Network`
-   `172.16.0.0/16` -> `Miami Network`
-   `10.30.23.1/32` -> `Device Example` (using `/32` to indicate a specific host)

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/network-decorator-csv.png" align="center"></figure>

<br />

### **Step 2: Grid Handler Configuration**

In the Transform stage, add a new **Net Decorator** handler and configure it as follows:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/network-decorator-config.png" align="center"></figure>

<br />

-   **CSV File Path:** Select the reference CSV file containing the subnets.
-   **Source Columns:** Define the lookup relationship.
    -   `CSV Name` = `net` (the column containing the CIDR subnets).
    -   `Grid Name` = `net_src_ip` (the column in the Grid containing the actual IP addresses to evaluate).
-   **Destination Columns:** Define where the new information will be stored.
    -   `CSV Name` = `descriptive_field` (the descriptive value from the CSV).
    -   `Grid Name` = `descriptive_value` (the new column that will be created in the Grid).
-   **Default value if not found:** Set a default label such as `No_info_provided` for IP addresses that do not match any subnet in the CSV file.

<br />

**Result:**

If the Grid contains the IP `192.168.32.45` in the `net_src_ip` column, the handler will evaluate it against the CSV file, determine that it belongs to the `192.168.32.0/24` subnet, and create a new column `descriptive_value` with the text `Madrid Network`.

<br />

---

<div class="sd-callout" data-callout-type="info"><strong>Net IPv6 Decorator:</strong> Please note that there is a separate Grid Handler called <strong>Net IPv6 Decorator</strong>. It applies the exact same methodology and configuration process described in this document, with the only difference being that the subnets in the CSV file must be defined using IPv6 notation.</div>

<br />
