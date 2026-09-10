---
reusableId: 147
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Sflow
id: Z4I-P8Q4-K1D-88D
slug: sflow
isVisible: true
lastUpdated: '2025-09-02 15:11:06'
---
# **<span align="center">sFlow Connector</span>**

<br />

The **sFlow Connector** is designed to process flow data exported in the **sFlow protocol** from network devices such as switches and routers. Similar to the NetFlow Connector, it works in conjunction with the **Ethernet Streamer** pipeline. Before using this connector, it is **mandatory** to configure an **Ethernet Streamer** pipeline with the correct port (commonly UDP/6343) and host filters. The Ethernet Streamer captures the binary sFlow traffic and stores it in the **Collected Path** directory, where the sFlow Connector later processes and decodes it.

<br />

⚠️ **Note:** Viewtinet provides a **Plugin Template** for sFlow integrations. In most scenarios, you will not need to configure this connector manually, as the template already includes a functional setup.

<br />

## **Key Parameters**

-   **Frequency Type**<br />
    Same as other scheduled connectors (ICMP, SNMP, CSV, NetFlow). It can be configured as:
    
    -   **Periodic**: Executes every _x_ seconds (defined in _Refresh Time_).
    -   **Scheduled**: Executes according to a Cron Expression.
-   **Threads**<br />
    Defines the number of concurrent threads for pipeline execution. Increasing this number allows more files to be processed simultaneously, but also increases CPU and memory usage.
-   **Collected Path**<br />
    Directory where the Ethernet Streamer dumps the captured sFlow traffic files.
-   **Processing Path**<br />
    Temporary directory where files are handled while being decoded.
-   **Processed Path**<br />
    Directory where files are stored after successful processing.
-   **Suffix**<br />
    File extension of dumped files, usually `.csv` or a binary format depending on the configuration.
-   **Max Files**<br />
    Maximum number of files processed per thread during each execution cycle.
-   **Number of Executions**
    
    -   `-1`: The connector will run indefinitely.
    -   Positive integer: Limits the execution to the specified number of runs.
-   **Version**<br />
    Defines how fields are decoded according to the sFlow standard version. Typically supports **sFlow v5**, which is the most widely used.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/XgZ5Nqi9RM1DUarAFCdd.png"></figure>

<br />