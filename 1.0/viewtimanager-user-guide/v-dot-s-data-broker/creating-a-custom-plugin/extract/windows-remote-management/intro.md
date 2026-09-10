---
reusableId: 152
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Intro
id: SOU-4DMA-MVG-KSA
slug: intro
isVisible: true
lastUpdated: '2025-09-04 12:44:22'
---
# **<span align="center">Windows Remote Management (WinRM)</span>**

<br />

The **Windows Remote Management (WinRM) Connector** enables Viewtilog to securely connect to Windows servers and retrieve a wide range of performance metrics, logs, and system information.<br />
By leveraging Microsoft’s native **WinRM protocol**, this connector provides agentless monitoring, eliminating the need to install additional software on the target Windows hosts.

<br />

## **Key Capabilities**

-   **Performance Metrics**: Collect counters such as CPU utilization, memory usage, disk I/O, and network statistics.
-   **System Information**: Gather details including uptime, running processes, installed hotfixes, and system configuration.
-   **Event Logs**: Query Windows event logs (e.g., Security, Application, System) for specific events such as logon attempts, service state changes, or errors.
-   **Agentless Access**: Uses WinRM over HTTP/HTTPS to communicate, ensuring minimal overhead on the monitored system.

<br />

## **Typical Use Cases**

-   Monitoring resource consumption of critical Windows servers.
-   Collecting logon and security events from domain controllers.
-   Tracking disk usage and performance on application servers.
-   Auditing configuration and system health without deploying additional agents.

<br />

📌 The WinRM Connector is ideal for organizations with Windows-based infrastructures, as it integrates seamlessly with the Visual Smart Data Broker (VSDB) ETL pipeline to provide visibility of server health and security events in real time.