---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtimon Configuration'
id: D4S-M0QZ-2PC-2AM
slug: viewtimon-configuration
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 18:56:18'
---
# **<span align="center">Viewtimon Configuration</span>**

<br />

The **CONFIGURATION** tab within the Viewtimon interface is where you define the core processing parameters, activate specific traffic inspectors, and enable advanced troubleshooting features.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-configuration.png" align="center"></figure>

<br />

---

## **1\. Viewtimon Configuration (Instances)**

This section governs the fundamental resources allocated to the DPI engine.

-   **Number of Instances:** This field defines how many DPI engine instances will run in parallel. The recommended sizing is **1 instance for every 500 Mbps of traffic** that the probe is expected to process. Properly sizing this ensures the system can handle the traffic volume without dropping packets.
-   **Reporting period (secs):** Defines how frequently the engine aggregates and flushes the obtained metrics into the database (e.g., `1 min`).

## **2\. Inspectors**

Inspectors are specialized internal modules responsible for dissecting specific application protocols.

By enabling these checkboxes (TLS, DNS, VOIP, HTTP, DHCP, FTP), you activate the corresponding inspector.

> <div class="sd-callout" data-callout-type="info"><strong>KPI Collection</strong> These inspectors are directly responsible for obtaining the rich protocol-specific metrics. The KPIs that each inspector is able to extract are fully detailed in the <a href="kpireference.md" target="_blank">KPI Reference</a> page. If an inspector is disabled, its corresponding KPIs will not be collected.</div>

## **3\. Viewtimon Sniffer**

The **Viewtimon Sniffer** is an advanced feature that transforms the probe into a full packet capture tool (similar to Wireshark), allowing for deep forensic analysis of network traffic.

By checking the **Enable** box, the engine begins saving raw `pcap` files based on the traffic it sees.

You can further control this feature using:

-   **Packet Truncation:** Allows you to limit the maximum length of captured packets (e.g., `32766` bytes). Truncating packets is useful if you only need to inspect headers rather than full payloads, saving significant disk space.
-   **Capture Filters:** You can add specific filters (`Type`, `Value`, `Length`) so the sniffer only captures traffic matching certain criteria (e.g., specific IP addresses or ports), rather than capturing all network traffic.

<br />