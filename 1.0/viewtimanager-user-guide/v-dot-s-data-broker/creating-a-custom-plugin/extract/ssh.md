---
reusableId: 149
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: SSH
id: DNT-JX5E-QQ6-D9Q
slug: ssh
isVisible: true
lastUpdated: '2025-09-03 16:05:08'
---
# **<span align="center">SSH Query Connector</span>**

The **SSH Query Connector** allows Viewtilog to connect to remote devices using SSH and retrieve system metrics or execute custom commands.<br />
This connector is particularly useful when you need to monitor servers or network devices where SNMP or other protocols are not enabled, but SSH access is available.<br />
It is a **scheduled connector**, meaning it runs periodically based on the defined execution frequency.

<br />

## **Key Features**

-   Establishes an SSH session with the target host.
-   Collects standard metrics such as:
    
    -   **CPU usage**
    -   **Memory utilization**
    -   **Disk usage**
    -   **Network interfaces**
    -   **Uptime**
-   Allows execution of **custom commands** defined by the user.
-   Supports **password-based authentication** or other SSH methods.

<br />

## **Configuration Parameters**

From the screenshots provided:

1.  **Connector Type**<br />
    Select **SSH Query Connector** as the connector type.
2.  **Pipeline Name**<br />
    Define a unique name for the pipeline (e.g., `my_ssh_connector`).
3.  **Execution Configuration**
    
    -   **Frequency Type**: Scheduled or periodic.
    -   **Cron Expression**: Defines how often the queries will be executed (e.g., every minute).
    -   **Number of Executions**: `-1` means unlimited executions.
        
        <br />
        
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/Uk3m0c5PZj7X3HsA0hoS.png" align="center"></figure>
    
    <br />
    
4.  **Host Configuration**
    
    -   **Host Name**: IP address or hostname of the device (e.g., `10.30.23.10`).
    -   **Port**: Default SSH port is `22`.
    -   **User**: SSH username (e.g., `viewtinet`).
    -   **Authentication Type**: Password (other methods may be available).
    -   **Password**: Corresponding password for authentication.
    -   Multiple hosts can be added if required
        
        <br />
        
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/ZkIArSUbkgkn2FhneYLT.png" align="center"></figure>
    
    <br />
    
5.  **Queries**<br />
    Choose the type of query to execute. Available options include:
    
    -   `cpu` → Retrieve CPU usage.
    -   `disk` → Disk utilization.
    -   `memory` → Memory usage.
    -   `network` → Network interface metrics.
    -   `service` → Service status.
    -   `uname` → System information.
    -   `uptime` → System uptime.
    -   `cmd` → Execute a custom command.

<br />

## **Example: Querying CPU Metrics**

-   **Pipeline Name**: `my_ssh_cpu_monitor`
-   **Host**: `10.30.23.10`
-   **User**: `viewtinet`
-   **Authentication**: Password
-   **Query Type**: `cpu`

This configuration will connect via SSH and periodically retrieve CPU usage data from the specified host.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/zQwoKveREFPYvSOYQWZk.png" align="center"></figure>

<br />

<br />

---

> ⚠️ **Important Note**<br />
> Ensure the SSH credentials provided have the necessary permissions to execute the selected queries. For production environments, it is recommended to use restricted, read-only accounts instead of root users.

<br />