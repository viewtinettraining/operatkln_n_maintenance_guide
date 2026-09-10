---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'IP Address Converter'
id: VRJ-3SH-NUH-NLG
slug: ip-address-converter
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 16:58:00'
---
# **<span align="center">IP Address Converter</span>**

<br />

The **IP Address Converter** grid handler is used to perform conversions between standard IP address string formats and their mathematical representations (Integers or Hexadecimals), and vice versa. 

This is particularly useful when raw data sources provide IP addresses as decimal integers or hexadecimals, which need to be translated into readable dotted-decimal IP addresses for analysis, or when you need to compress IPs into integer representations.

<br />

---

## **Configuration**

Configuring the IP Address Converter is straightforward. It requires three main parameters to process the data:

-   **Field:** The source column in your grid that contains the value you want to convert.
-   **Output column name:** The destination column where the handler will write the resulting converted value. If this column doesn't exist, it will be created.
-   **Mode:** The type of conversion operation you want to perform.

<br />

### **Available Modes**

The handler supports four different conversion modes depending on your needs:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/ip-address-converter-modes.png" align="center"></figure>

<br />

-   **IP Address to Int:** Converts a standard dotted-decimal IP address (e.g., `192.168.1.1`) into its 32-bit Integer representation.
-   **Int to IP Address:** Converts a 32-bit Integer representation back into a standard dotted-decimal IP address.
-   **IP Address to Hexadecimal:** Converts a standard dotted-decimal IP address into its Hexadecimal representation.
-   **Hexadecimal to IP Address:** Converts a Hexadecimal string representation back into a standard dotted-decimal IP address.

<br />