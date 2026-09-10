---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'The Viewtimon Interface'
id: Y1G-L34-YR2-JHP
slug: viewtimon-interface
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 10:48:29'
---
# **<span align="center">The Viewtimon Interface</span>**

<br />

The **Viewtimon** module provides a dedicated interface for managing the DPI probe, monitoring its health, and checking its performance.

> <div class="sd-callout" data-callout-type="info">The Viewtimon interface is not always active by default. Access to this module depends on the Viewtimon feature being properly licensed in your deployment.</div>

To access this interface, navigate to the main Viewtimanager left-hand menu and click on **Viewtimon**.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-menu.png" align="center"></figure>

<br />

---

## **Module Overview and Controls**

Upon entering the Viewtimon section, you are greeted with the **STATUS** tab, which acts as the main dashboard for the module.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-performance.png" align="center"></figure>

<br />

### **System Information & Controls**

At the very top of the page, the system provides critical operational information and control buttons for the Viewtimon engine:

-   **Version:** Displays the currently installed version of Viewtimon (e.g., `6.3.5.6369 (Revision)`), along with a link to the latest **release notes**.
-   **Uptime:** Shows how long the Viewtimon service has been continuously running without interruption.
-   **Control Buttons (Top Right):** These buttons allow you to manage the engine's service state:
    
    -   **STOP:** Halts the Viewtimon DPI engine.
    -   **RESTART:** Safely restarts the service (useful after applying certain configuration changes).
    -   **START:** Starts the engine if it is currently stopped.

### **Navigation Tabs**

Below the top controls, several tabs allow you to navigate through the different configuration areas of Viewtimon:

-   **STATUS:** The current view, showing the performance dashboard.
-   **CONFIGURATION:** For setting up network interfaces and advanced engine parameters.
-   **SIGNATURES:** To manage custom or updated DPI application signatures.
-   **BUSINESS GROUPS:** To define organizational grouping for IPs and subnets.
-   **HOSTS LIST:** Displays discovered hosts on the network.
-   **ISSUES:** A log of any internal warnings or errors detected by the module.

---

## **Viewtimon Performance Dashboard**

The **STATUS** tab features the **Viewtimon Performance** dashboard, which visualizes the real-time and historical health of the probe itself (not the user traffic). It includes the following key indicators:

-   **CPU Usage:** Monitors the processing load of the DPI engine.
-   **Memory Usage:** Tracks the RAM consumption of the module.
-   **IO Wait:** Displays the time the CPU spends waiting for input/output operations (e.g., writing to disk), which is crucial for identifying bottlenecks.

<br />

### **Time Selector Configuration**

To analyze the performance historically, you can use the robust **Time Selector** located at the top of the dashboard.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-time-selector.png" align="center"></figure>

<br />

This selector allows you to customize the view:

-   **Dashboard Dropdown:** Allows switching to different performance dashboards if available.
-   **Start Date & End Date:** Define an exact custom time range.
-   **Time Shortcut:** A quick dropdown to select common periods (e.g., `Last day`, `Last 7 days`, `Last hour`).
-   **Granularity:** Adjust the resolution of the data points on the graphs (e.g., `5 minutes`, `1 hour`), allowing for fine-grained analysis or smoother long-term trends.
-   **Control Icons:** The buttons on the right allow you to refresh the data manually, lock the time range, enable auto-refresh, or access further dashboard options.

---

## **Additional Health Dashboards**

Using the **Dashboard Dropdown** in the Time Selector, you can access two additional specialized dashboards to further analyze the health and performance of the probe:

<br />

<figure align="center" style="width:45%"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-dashboard-click.png" width="45%" align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-dashboard-dropdown.png" width="45%" align="center"></figure>

<br />

### **1\. Stages Monitoring**

This dashboard displays key information about the internal functioning of the Viewtimon probe and its data processing pipeline.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-stages-monitoring.png" align="center"></figure>

<br />

It includes the following metrics:

-   **Total Throughput:** The total amount of data being processed internally.
-   **Total Dropped Packets:** Identifies if any packets are being dropped by the engine.
-   **Total Deduplicated Packets:** Shows packets that were identified as duplicates and handled accordingly.
-   **Total Throughput by stage & Total Dropped Packets by stage:** Breaks down the throughput and drops across the specific internal processing stages of the engine (e.g., analyze, balancer, qos).

### **2\. Interface Statistics**

This dashboard provides a clear view of the physical or virtual network interfaces that Viewtimon is monitoring.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-interface-statistics.png" align="center"></figure>

<br />

It highlights:

-   **Throughput:** The traffic volume measured directly at the interface level.
-   **Input Packets:** The total number of packets received by the interface.
-   **Packets with Errors:** The number of malformed or corrupted packets detected.
-   **Packets missed:** Packets that the interface failed to capture, which can indicate hardware bottlenecks or excessive traffic bursts.

<br />