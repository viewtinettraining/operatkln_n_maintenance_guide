---
reusableId: 137
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: CSV
id: 7Z6-GTTH-7QR-S4A
slug: csv
isVisible: true
lastUpdated: '2025-10-15 15:25:17'
---
# **<span align="center">CSV Connector</span>**

<br />

The **CSV Connector** is used to ingest records from CSV files. Although the name suggests a strict CSV format, the **field separator is configurable**, allowing flexibility to adapt to different file structures. This connector is widely used for integrations with **VoIP systems**, particularly for ingesting **CDRs (Call Detail Records)**, **CMRs (Call Management Records)**, or any other data source that generates logs in CSV format.

The connector reads files directly from a **local directory on the Viewtilog server**, which means there must be an **external or scheduled process** responsible for depositing CSV files into the specified collection path. Once collected, the files are processed and then moved to a dedicated directory to ensure traceability and avoid reprocessing.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/UFK4rNp2GJqY0IXnwiqC.png" align="center"></figure>

<br />

## **Configuration Parameters**

-   **Frequency Type**<br />
    Same behavior as in SNMP and ICMP connectors:
    
    -   **Periodic**: Executes the pipeline at fixed intervals (defined in _Refresh Time_).
    -   **Scheduled**: Uses a cron expression to control execution at precise times.
-   **Number of Threads**<br />
    Defines how many concurrent threads will process files. This is useful for handling high volumes of data in parallel.
-   **Pipeline Name**<br />
    A unique identifier for the pipeline.
-   **Refresh Time (secs)**<br />
    The interval in seconds between each execution when _Periodic_ is selected.
-   **Number of Executions**
    
    -   `-1`: Continuous execution with no limit.
    -   Positive integer: Limits the number of runs to the specified value.
-   **Collected Path**<br />
    Directory where new CSV files must be placed. Files in this location will be read by the connector.
-   **Processing Path**<br />
    Temporary directory where files are moved while being processed.
-   **Processed Path**<br />
    Directory where files are stored once processing is completed.
-   **Separator**<br />
    Character used to delimit fields (e.g., `,`, `;`, `|`).
-   **Suffix**<br />
    Extension of the files to be processed (e.g., `.csv`).
-   **Max Files**<br />
    Maximum number of files to be processed per cycle.
-   **Keep Commas**<br />
    Option that preserves commas inside fields instead of splitting them as separators.
-   **Has Quotations**<br />
    If enabled, fields enclosed in quotes (`"`) are treated as a single field, even if they contain the separator character.
-   **Chunk Size**<br />
    Defines whether the CSV file will be read in chunks (useful for very large files).

<br />

## **Fields Definition**

In order to parse the file correctly, **fields must be defined**. This can be done in two ways:

1.  **Manual definition**: Use the **Add New Field** button to create fields one by one, assigning them a name and type.
2.  **Import from CSV**: Upload a sample CSV file containing only the **header line** (field names). The system will automatically create the corresponding fields in the connector configuration.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/nzTHsGYKZ2nYSO0pNxfl.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/YS2R089DrTbHW5BXYHiP.png" align="center"></figure>

<br />

**Additional options include:**

-   **Field Name**: Name of the column to be parsed.
-   **Field Type**: Data type for the field (string, integer, float, etc.), which can be applied individually or to all fields at once.
-   **Delete All Fields**: Resets the configuration if needed.

<br />

## **Summary**

The CSV Connector provides a flexible and efficient way to ingest structured data stored in files:

-   Supports both **Periodic** and **Scheduled** execution.
-   Requires a process to deposit CSV files into the collection directory.
-   Can handle field separators and quoted fields for complex data structures.
-   Fields can be configured manually or imported directly from a CSV header.

This connector is ideal for environments where external systems export logs or transaction records in CSV format and need to be integrated into the Viewtinet platform for further analysis.