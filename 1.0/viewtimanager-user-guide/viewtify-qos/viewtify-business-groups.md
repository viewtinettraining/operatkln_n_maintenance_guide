---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtify Business Groups'
id: BTJ-7EZ-LI3-8CP
slug: viewtify-business-groups
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 14:51:52'
---
# **<span align="center">Viewtify Business Groups</span>**

<br />

The **BUSINESS GROUPS** tab allows you to configure Business Groups (BGs). A Business Group is an editable dimension used to include your customers' subnet information, grouping IPs collected by Viewtify based on locations, branches, departments, or any other breakdown criteria relevant to your organization.

<span align="justify">By default, Viewtify doesn't contain any predefined Business Groups, and it is not mandatory for deployment. However, it is highly recommendable to include this information since there are significant optimizations and analytical benefits based on these fields within the Viewtify plugin.</span>

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-bg-tab.png" align="center"></figure>

<br />

---

## **Configuring Business Groups**

You have two primary ways to populate the Business Groups table:

1.  **Manual Entry:** You can add entries individually by clicking the **\+ ADD NEW BUSINESS GROUP** button at the bottom left. This creates a new row where you can manually specify the `Network` (IP address or CIDR subnet) and the corresponding `Business Group` name.
2.  **Bulk Import:** For larger deployments, it is much more efficient to use the **IMPORT HOSTS** button at the bottom right. This allows you to upload a list of IPs and subnets in bulk (via CSV) mapped to their respective groups.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-bg-add.png" align="center"></figure>

<br />

Once you have added or imported your networks, remember to click the **SAVE CHANGES** button to apply the new Business Group definitions.

---

## **Fixing Overlapping Networks**

When defining multiple subnets, especially in complex enterprise networks, it is possible to accidentally create overlapping rules (e.g., assigning the `192.168.1.0/24` subnet to one group, but specifically assigning the smaller `192.168.1.112/28` subnet to another).

Viewtify implements intelligent validations to detect and help you resolve these conflicts automatically. If an overlap occurs, a red warning banner will appear at the top of the screen explaining the conflict.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-bg-overlapping.png" align="center"></figure>

<br />

To resolve the issue, simply click the purple **FIX OVERLAPPING NETWORKS** button located at the top right of the table. The system will automatically reorder the rules (moving the more specific subnet above the broader one) to ensure that traffic is categorized correctly without ambiguity.