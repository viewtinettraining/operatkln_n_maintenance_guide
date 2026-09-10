---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Introduction to Viewtify QoS'
id: G45-KCP-OW0-OSH
slug: introduction-to-viewtify-qos
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 11:13:26'
---
# **<span align="center">Introduction to Viewtify QoS</span>**

<br />

**Viewtify QoS** is Viewtinet's advanced bandwidth management and Quality of Service module. It provides administrators with precise control over network traffic, ensuring that critical applications receive the necessary resources while limiting the impact of non-essential data transfers

Through Viewtify QoS, you can create and enforce powerful traffic policies, including:

-   **Rate-Limiting:** Restricting the maximum bandwidth available to specific users, IPs, or applications.
-   **Traffic Shaping:** Smoothing out traffic bursts to maintain a steady and predictable flow of data.
-   **Prioritization:** Giving preference to mission-critical traffic (like VoIP or video conferencing) over lower-priority traffic (like file downloads).
-   **Dropping:** Completely blocking or discarding unwanted or malicious traffic.

<br />

---

## **Dependency on Viewtimon**

> <div class="sd-callout" data-callout-type="alert">The Viewtify QoS module is fundamentally tied to the <strong>Viewtimon</strong> DPI engine.</div>

**It is mandatory to deploy Viewtimon** in order to use Viewtify QoS. This is because Viewtify relies entirely on Viewtimon's deep packet inspection (DPI) capabilities to accurately classify the traffic traversing the network. Viewtimon identifies the applications, protocols, and users, and then Viewtify applies the corresponding bandwidth management policies based on that classification.

<br />

---

## **Inline Deployment and Bypasser**

Unlike traditional monitoring tools that can operate passively on a mirrored port, Viewtify QoS is an active control mechanism. Therefore, it must be deployed **inline** with the network traffic.

To ensure network high availability and prevent the Viewtinet appliance from becoming a single point of failure, Viewtify QoS is deployed in conjunction with a **hardware bypasser**. The bypasser ensures that if the appliance loses power or the Viewtify service stops, network traffic will physically bypass the appliance and continue flowing without interruption.

_(The specific configuration and management of the bypasser will be explained in detail in subsequent sections)._