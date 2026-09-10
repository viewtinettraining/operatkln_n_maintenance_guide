---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Syslog Producer'
id: SYS-PRD-LG1-TR4
slug: syslog-producer
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 16:22:00'
---
# **<span align="center">Syslog Producer</span>**

<br />

The **Syslog Producer** allows you to export the final transformed grid as Syslog messages to a remote server using the standard Syslog protocol (UDP). Each row of the processed grid is formatted and forwarded as an individual Syslog message to the configured destination.

This is particularly useful when you need to integrate Viewtinet's processed data with third-party SIEM platforms, log aggregation systems, or any external tool that supports Syslog ingestion.

<br />

> [!WARNING] **UDP — Connectionless Protocol**<br />
> Syslog operates over **UDP**, which is a connectionless, non-reliable transport protocol. This means that Viewtinet sends the messages without establishing a prior connection and **has no way to confirm whether the remote server is actually receiving the data**. There is no acknowledgment mechanism or error feedback from the destination.<br /><br />
> Therefore, it is the **administrator's responsibility** to guarantee network connectivity between the Viewtinet server and the Syslog destination **before** enabling this producer. It is strongly recommended to verify reachability (e.g., by testing with `netcat` or validating firewall rules for the target IP and port) to ensure the messages are being delivered correctly.

<br />

---

## **Configuration Parameters**

Once you select `Syslog Producer` from the Producer Type dropdown, the following connection and formatting parameters become available:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/syslog-producer-config.png" align="center"></figure>

<br />

-   **IP Address / Hostname:** The destination IP address or hostname of the remote Syslog server where the messages will be sent (e.g., `10.30.23.5`).
-   **Syslog port:** The UDP port on the destination server listening for Syslog messages. The standard default is `514`.
-   **Timestamp position:** Defines the position (index) within the Syslog message where the timestamp will be inserted. A value of `0` places it at the very beginning of the message payload.
-   **Timestamp format:** The format string used to represent the timestamp in each message. It follows the standard Linux `date` command format wildcards. For example, `%s%f` produces a high-precision epoch timestamp including fractional seconds.
-   **Message severity:** The Syslog severity level assigned to each exported message, following the standard Syslog severity codes (RFC 5424). Common values include:
    -   `0` — Emergency
    -   `1` — Alert
    -   `2` — Critical
    -   `3` — Error
    -   `4` — Warning
    -   `5` — Notice
    -   `6` — Informational
    -   `7` — Debug

<br />
