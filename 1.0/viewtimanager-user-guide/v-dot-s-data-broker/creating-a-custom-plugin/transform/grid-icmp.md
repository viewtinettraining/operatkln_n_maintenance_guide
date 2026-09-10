---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grid ICMP'
id: JNC-MDX-IUI-QRJ
slug: grid-icmp
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 09:22:00'
---
# **<span align="center">Grid ICMP</span>**

<br />

The **Grid ICMP** handler allows you to perform active network ping checks against an IP address or hostname directly during the ETL transformation stage.

By extracting the destination IP/hostname from a specified column in the grid, the handler executes an ICMP echo request (ping) to calculate essential network statistics such as:

-   **Status**: Whether the destination is `alive` or `down`.
-   **Packet Loss**: Percentage of packets lost.
-   **Round Trip Time (RTT)**: Average, Maximum, and Minimum latency response times.

These statistics are dynamically injected into the grid as new columns and can then be seamlessly loaded into the time-series database for monitoring and alerting.

---

## **Configuration Parameters**

To properly set up the **Grid ICMP** handler, define the following configuration values:

-   **Host Column**: The existing column in the grid that contains the destination IP address or hostname to ping.
-   **New Column Prefix**: A custom text prefix that will be prepended to all the newly generated statistics columns. For example, if you set the prefix to `my_prefix`, the handler will create the following columns: `my_prefix_status`, `my_prefix_packet_loss`, `my_prefix_rtt_avg`, `my_prefix_rtt_max`, and `my_prefix_rtt_min`.
-   **Ping Count**: The number of ICMP echo request packets to send for the test (e.g., `4`).
-   **Ping Timeout**: The maximum amount of time (in seconds) to wait for a response before considering the request timed out (e.g., `2`).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-icmp-step1.png" align="center"></figure>

<br />

---

## **Expected Behaviour**

Using the configuration from the image above as an example:

-   The handler reads the IP address from the `host` column.
-   It sends `4` ping requests with a timeout of `2` seconds.
-   The results are appended to the grid using the prefix `my_prefix`.

### **Grid Example**

<table><tbody><tr><th><p><strong>Before Transformation:</strong></p></th><th><p>host</p></th></tr><tr><td><p><br></p></td><td><p><code>192.168.1.1</code></p></td></tr><tr><td><p><br></p></td><td><p><code>10.0.0.99</code></p></td></tr></tbody></table>

<br />

<table><tbody><tr><th><p><strong>After Transformation:</strong></p></th><th><p>host</p></th><th><p>my_prefix_status</p></th><th><p>my_prefix_packet_loss</p></th><th><p>my_prefix_rtt_min</p></th><th><p>my_prefix_rtt_avg</p></th><th><p>my_prefix_rtt_max</p></th></tr><tr><td><p><br></p></td><td><p><code>192.168.1.1</code></p></td><td><p><code>alive</code></p></td><td><p><code>0</code></p></td><td><p><code>1.2</code></p></td><td><p><code>1.5</code></p></td><td><p><code>2.1</code></p></td></tr><tr><td><p><br></p></td><td><p><code>10.0.0.99</code></p></td><td><p><code>down</code></p></td><td><p><code>100</code></p></td><td><p><code>0</code></p></td><td><p><code>0</code></p></td><td><p><code>0</code></p></td></tr></tbody></table>

<br />

This powerful feature eliminates the need for separate active probing plugins, as you can continuously measure availability and latency metrics on-the-fly alongside your standard data ingestion.