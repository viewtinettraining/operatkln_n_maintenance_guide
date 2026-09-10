---
reusableId: 150
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Syslog
id: 9KD-EY7D-1I9-Y1X
slug: syslog
isVisible: true
lastUpdated: '2025-09-03 16:25:58'
---
# **<span align="center">Syslog Connector</span>**

The **Syslog Connector** is used to process syslog messages that have been previously captured by the **Ethernet Streamer** connector. Similar to the Netflow connector, it operates as a **scheduled pipeline**, meaning it runs periodically based on the configured execution frequency.

Unlike Netflow, the Syslog protocol does not require selecting a version, which simplifies its configuration.

<br />

## **Key Characteristics**

-   Works together with the **Ethernet Streamer** pipeline, which dumps raw syslog traffic into a specific directory.
-   Periodically processes the dumped files and extracts syslog messages.
-   Each syslog record is then parsed into structured fields for further analysis.
-   Highly scalable, as multiple threads can be configured for concurrent processing.

## **Configuration Parameters**

From the provided screenshot:

1.  **Connector Type**<br />
    Select **Syslog Connector** as the connector type.
2.  **Pipeline Name**<br />
    Define a unique name for the pipeline (e.g., `my_syslog_connector`).
3.  **Number of Threads**<br />
    Configure the number of concurrent threads.
    
    -   More threads = faster processing.
    -   However, higher values increase CPU and memory consumption.
4.  **Execution Configuration**
    
    -   **Frequency Type**: Scheduled or periodic.
    -   **Cron Expression**: Defines how often the pipeline will run (e.g., every minute).
    -   **Number of Executions**: `-1` indicates unlimited executions.
5.  **Paths**
    
    -   **Collected Path**: Directory where Ethernet Streamer dumps raw syslog traffic.
    -   **Processing Path**: Temporary directory used while processing files.
    -   **Processed Path**: Final directory where processed files are stored.
6.  **File Handling**
    
    -   **Suffix**: Defines the format of files to be processed (e.g., `.csv`).
    -   **Max Files**: Maximum number of files to read per execution cycle.
    -   **Chunk Size**: Splits large files into smaller chunks for more efficient processing.
        
        <br />
        

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/M6zx6jJzAjbqb3WU5xu0.png" align="center"></figure>

## **Example Scenario**

If the **Ethernet Streamer** is configured to capture syslog traffic from multiple devices on port 514 and dump the data into `/opt/vn/dhyana/var/data/syslog/collected`, then the Syslog Connector will:

1.  Periodically read files from this directory.
2.  Process and decode the syslog messages.
3.  Store the structured output in the processed directory for use in later stages of the ETL pipeline.

---

> ⚠️ **Important Note**<br />
> The Syslog Connector **depends on a properly configured Ethernet Streamer pipeline**. Without it, there will be no traffic to process.

<br />