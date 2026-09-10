---
reusableId: 145
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Netflow
id: N8H-HPYX-VSJ-1GV
slug: netflow
isVisible: true
lastUpdated: '2025-09-02 12:36:00'
---
# **<span align="center">Netflow</span>**

The **Netflow Connector** is designed to process flow data (Netflow, JFlow, NetStream) captured by the **Ethernet Streamer** pipeline. Before using this connector, it is **mandatory** to configure a valid **Ethernet Streamer** pipeline with the correct port and host filters. The Ethernet Streamer captures the binary traffic and stores it in the **Collected Path** directory, where the Netflow Connector will later process and decode it.

<br />

⚠️ **Note:** Viewtinet already provides a **Plugin Template** for Netflow integrations, so in most cases you will not need to configure this pipeline manually.

<br />

## **Key Parameters**

-   **Frequency Type**<br />
    Works the same way as other scheduled connectors (ICMP, SNMP, CSV). It can be set to:
    
    -   **Periodic**: Runs every _x_ seconds defined in _Refresh Time_.
    -   **Scheduled**: Runs based on a Cron Expression.
-   **Threads**<br />
    Defines the number of concurrent threads for pipeline execution. Increasing the number of threads allows processing multiple files simultaneously but will also increase CPU and memory usage. Adjust carefully depending on system resources.
-   **Collected Path**<br />
    Directory where Ethernet Streamer dumps the captured Netflow traffic files.
-   **Processing Path**<br />
    Temporary location where files are processed.
-   **Processed Path**<br />
    Directory where files are stored after being successfully processed.
-   **Suffix**<br />
    File extension of the dumped files, usually `.csv`.
-   **Max Files**<br />
    Maximum number of files to read per thread execution. For example, if set to `5` and there are 3 threads, the connector can process up to 15 files in parallel.
-   **Number of Executions**<br />
    If set to `-1`, the pipeline will run continuously. Any other value specifies the number of executions before stopping.
    
    <br />
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/EgT0xLm3xxAsC58zkY5T.png" align="center"></figure>

<br />

-   **Version**<br />
    Defines the Netflow version to use for decoding records. Supported versions include **5**. **9 and IPFIX**.<br />
    The selected version determines which fields will be decoded and stored.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/dRHicKbWSX5sCewcL6gx.png"></figure>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/X9ZU8iol52d7WRzNEy2H.png"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/mI049ZPsaejF8gWwjxdZ.png" align="center"></figure>

<br />

Each field is tied to the Netflow version selected (v5, v9 or IPFIX). Ensure consistency between the configured version and the expected field set.

<br />

✅ With this connector, Viewtinet transforms raw Netflow exports into structured data ready for monitoring, dashboards, and analytics.

<br />