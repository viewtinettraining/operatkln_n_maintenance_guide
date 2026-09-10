---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'QoS Profiles'
id: WO0-VUU-YUB-DSJ
slug: profiles
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 15:34:26'
---
# **<span align="center">QoS Profiles</span>**

<br />

If Classification Rules define _what_ traffic you are managing, **QoS Profiles** define _how_ that traffic should be handled. By assigning a profile to a rule, you instruct the engine on how to shape, limit, or prioritize the flow.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-1.png" align="center"></figure>

<br />

---

## **Types of Profiles**

Viewtify QoS offers six fundamental types of profiles to address different network needs:

1.  **Max Rate:** Sets a maximum throughput limit to non-critical or heavy applications (e.g., capping streaming or P2P downloads) to prevent them from saturating the link.
2.  **Max Rate (%):** Used generally in child policies to define a maximum throughput limit as a percentage of the parent policy's bandwidth.
3.  **Min Rate:** Allocates a guaranteed minimum quantity of bandwidth to critical applications, ensuring they function smoothly even during network congestion.
4.  **Min Rate (%):** Used generally in child policies to define a guaranteed minimum bandwidth as a percentage of the parent policy's bandwidth.
5.  **Priority Queue:** Sets different transmission priorities according to the sensitivity of the flows.
6.  **Drop:** Instantly drops the packets of undesired or malicious flows, effectively blocking the traffic.
7.  **Normal QoS:** Leaves the inherited QoS settings intact without applying new restrictions at this level.
8.  **Real Time:** Specifically created and optimized for conference, voice, and VoIP applications to ensure minimal latency.
9.  **No QoS:** No QoS is set for the flow. In case of link saturation, these packets are the most likely to be dropped by the network hardware.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-2.png" align="center"></figure>

<br />

---

## **Priority Levels**

When using Priority Queue profiles, there are **3 core priority levels** available: High, Medium, and Low.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-3.png" align="center"></figure>

<br />

-   **Hierarchical Application:** Priorities are applied in a hierarchical way. Each level inherits the priority of its higher levels within the policy tree.
-   **Logical Combinations:** Through the combination of priorities across different branches of your policy tree, you can create up to **16 logical priority levels** for extremely granular traffic management.

<br />

---

## **Symmetric and Asymmetric Rates**

When configuring bandwidth limits, you have the flexibility to define how upload and download traffic are handled.

-   **Combined Rates:** Max and Min rates can be applied within the same profile for both inbound and outbound traffic, reducing the total number of rules needed in your policy.
-   **Symmetry:** You can configure the profile with **Symmetric** rates (e.g., 200 Kbps down / 200 Kbps up) or **Asymmetric** rates (e.g., 14 Mbps down / 12 Mbps up) using the equal/not-equal toggle button between the fields.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-4.png" align="center"></figure>

<br />

---

## **Creating a QoS Profile**

To create and configure a QoS profile based on your network needs, follow these steps:

1.  Click on the **+ ADD NEW** button to create a new row.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-create-1.png" align="center"></figure>

<br />

2.  Enter a unique **Name** for your profile. If you try to save without filling the mandatory fields, the system will highlight the row in red.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-create-2.png" align="center"></figure>

<br />

3.  Select the **Type** from the dropdown menu (e.g., `Max Rate`).
4.  In the **Download/Priority** and **Upload** boxes, enter the bandwidth you want to control (e.g., `300 Kbps`). By default, the profile will be **Symmetric**, meaning the Download and Upload rates are equal.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-create-3.png" align="center"></figure>

<br />

5.  If you need to configure an **Asymmetric** profile (where Download and Upload limits are different), click on the equal symbol (`=`) between the boxes.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-create-4.png" align="center"></figure>

<br />

6.  The symbol will change to a not-equal sign (`≠`), allowing you to configure the upload speed independently according to your needs.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-create-5.png" align="center"></figure>

<br />

---

## **Searching and Deleting Profiles**

Similar to classification rules, safety validations prevent you from breaking active configurations.

-   QoS Profiles can be deleted **only if they are not used** in any policy.
-   The **Search** option (magnifying glass) helps you find exactly which policy is currently using the profile, so you can reassign it before attempting deletion.

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-search.png" align="center">
</figure>

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-search-result.png" align="center">
</figure>

<br />

To delete a profile, locate the desired profile and click on the **trash can icon**. However, if a profile is currently being used in a Use Case or Policy, the system will protect it and it will not be possible to delete it.

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-delete.png" align="center">
</figure>

<br />