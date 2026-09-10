---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtify Hosts List'
id: WD5-4HC-BOB-1YK
slug: viewtify-hosts-list
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 10:13:22'
---
# **<span align="center">Viewtify Hosts List</span>**

<br />

The **HOSTS LIST** tab provides an overview of the physical or virtual appliance where the Viewtify engine is currently deployed and running.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-hosts-list.png" align="center"></figure>

<br />

---

## **Informational Overview**

For the vast majority of users, this tab is **purely informational**. It displays the underlying Hostname or IP Address (e.g., `10.30.23.5`) and LAN interface IP associated with the Viewtify module. This helps administrators quickly identify which physical or virtual node is currently processing the network traffic.

Additionally, this section displays High Availability (HA) status if applicable (e.g., "No HA will be applied as there are only one host defined" for standalone deployments).

> <div class="sd-callout" data-callout-type="warning"><strong>System Architecture Changes</strong> The settings within this tab (such as adding new hosts or uninstalling nodes) directly manipulate the cluster architecture of the Viewtify engine.</div>
> 
> **Do not make any changes in this section** unless you have deep architectural knowledge of the deployment or have been explicitly instructed by Viewtinet Support. Modifying these fields without caution can cause severe operational issues and result in the DPI engine completely halting traffic processing.

<br />
