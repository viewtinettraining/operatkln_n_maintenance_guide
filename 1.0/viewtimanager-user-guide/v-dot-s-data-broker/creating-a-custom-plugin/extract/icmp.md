---
reusableId: 136
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: ICMP
id: NTA-4FAZ-5QN-QO6
slug: icmp
isVisible: true
lastUpdated: '2025-10-15 15:26:24'
---
# **<span align="center">ICMP Connector</span>**

<br />

The **ICMP Connector** allows the Visual Smart Data Broker (VSDB) to perform health checks on devices using **ping (echo requests)**. It is commonly used to monitor network reachability and packet loss rates across servers, routers, switches, and other IP-enabled devices.

<br />

## **Accessing the ICMP Connector**

1.  From the **Plugin Creator**, select the **Extract** stage.
2.  In the connector list, choose **ICMP Connector**.
3.  The ICMP Connector configuration screen will be displayed.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/4kFBZNWQnWiH3RD9afaf.png" align="center"></figure>

<br />

## **Configuration Parameters**

-   **Frequency Type**<br />
    Defines how often the connector executes:
    
    -   **Periodic**: The pipeline runs for the first time after the configured number of seconds (Refresh Time) once the plugin is installed, and continues to repeat at that interval.
    -   **Scheduled**: Execution is defined using a **cron expression**, allowing precise scheduling by minute, hour, day, week, or month.
-   **Number of Executions**
    
    -   `-1`: The connector runs indefinitely.
    -   Any positive value: The pipeline executes exactly that number of times.
-   **Session**<br />
    A mandatory string parameter used internally by the module to track execution.
-   **Ping Count**<br />
    Defines the number of **echo requests** (pings) sent to each host during every execution cycle.
    
    -   For a host to be declared **down**, _all_ echo requests must fail.
    -   Packet loss percentage is calculated as:
        
        ```
        Lost packets / Ping Count * 100
        ```
        
        Example:
        
        -   If `Ping Count = 5` and 1 ping is lost → packet loss = 20%.
        -   If `Ping Count = 4` and 1 ping is lost → packet loss = 25%.
-   **Ping Timeout**<br />
    The maximum waiting time (in seconds) for each echo reply. If the host does not respond within this time, the ping is considered lost.
-   **Host Batch Size**<br />
    Defines how many hosts are pinged simultaneously in each batch.
    
    -   Example: If there are **100 hosts** in the connector and `Host Batch Size = 50`, the system creates **2 pipelines**, each handling 50 hosts in parallel.

<br />

## **Hosts Section**

At least one host must be defined in the connector.<br />
Hosts can be provisioned in two ways:

-   **Mass provisioning via Inventory** (recommended for large environments, see the _Inventory_ chapter).
-   **Manual entry** using the **Add Host** button, where you specify the IP address and other details.

Hosts can also be imported or exported using the buttons available in the interface.

<br />

## **Summary**

The ICMP Connector enables reachability and latency monitoring of devices through configurable ping operations:

-   Supports **Periodic** and **Scheduled** execution modes.
-   Measures **packet loss percentage** based on the configured Ping Count.
-   Requires full echo request failure to mark a host as **down**.
-   **Host Batch Size** ensures scalable monitoring across large environments by dividing hosts into groups.

Correct configuration ensures accurate availability checks and efficient use of system resources.