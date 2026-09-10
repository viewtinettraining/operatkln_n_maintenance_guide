---
reusableId: 95
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'GUI Overview'
id: 80P-CBCB-V4T-FLT
slug: gui-overview
isVisible: true
lastUpdated: '2025-10-15 14:30:46'
---
# **<span align="center">Graphical User Interface (GUI) Overview</span>**

The Viewtimanager graphical interface provides centralized access to system health, configuration, and licensed modules. It is structured into three main zones:

<br />

## **🔝 Top Bar**

Located in the upper-right corner:

-   👤 **User Info**: Displays the currently logged-in user (e.g., `Logged in as admin`).
-   📦 **Module Info**: Shows the name and version of the selected module (e.g., Viewtimanager, Viewtimon, Viewtify QoS), uptime, and access to release notes.
-   🟢 **Control Buttons**: For licensed modules, control buttons (`START`, `STOP`, `RESTART`) are shown for service management.

<br />

## **📋 Sidebar Navigation Menu**

Located on the left, this menu allows access to different modules:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/iwg0OGfTo5xaN1xFf3Qb.png" align="center"></figure>

<br />

## **📋 Left Navigation Menu**

The vertical sidebar lists all accessible modules. By default, the following menu items are always visible:

<table><tbody><tr><th><p>Icon</p></th><th><p>Menu Item</p></th><th><p>Description</p></th></tr><tr><td><p>🏠</p></td><td><p><strong>Home</strong></p></td><td><p>General status and performance overview of the cluster</p></td></tr><tr><td><p>📊</p></td><td><p><strong>Viewtisight</strong></p></td><td><p>Manage Viewtisight: visualization and dashboard service control &amp; setup</p></td></tr><tr><td><p>📦</p></td><td><p><strong>Inventory</strong></p></td><td><p>Register and manage devices and data sources</p></td></tr><tr><td><p>🧩</p></td><td><p><strong>V.S. Data Broker</strong></p></td><td><p>Configure data routing and telemetry/log transport</p></td></tr><tr><td><p>🌐</p></td><td><p><strong>Networking</strong></p></td><td><p>Set IP addresses, DNS, routing, and interfaces</p></td></tr><tr><td><p>👤</p></td><td><p><strong>Admin</strong></p></td><td><p>Manage local users, passwords, and access settings</p></td></tr><tr><td><p>🆔</p></td><td><p><strong>License</strong></p></td><td><p>Apply and monitor platform licenses</p></td></tr></tbody></table>

> ⚠️ The following menu items appear **only when the corresponding feature is licensed**:

<table><tbody><tr><th><p>Icon</p></th><th><p>Menu Item</p></th><th><p>Description</p></th></tr><tr><td><p>📥</p></td><td><p><strong>Viewtilog</strong></p></td><td><p>Monitor performance and configuration of log ingestion modules</p></td></tr><tr><td><p>📈</p></td><td><p><strong>Viewtimon</strong></p></td><td><p>Deep traffic monitoring module. Offers performance stats and rule handling</p></td></tr><tr><td><p>📶</p></td><td><p><strong>Viewtify QoS</strong></p></td><td><p>Policy engine for QoS management. Includes bypass controls and host mapping</p></td></tr><tr><td><p>⚙️</p></td><td><p><strong>Configuration Manager</strong></p></td><td><p>Import/export or replicate configuration templates across nodes</p></td></tr></tbody></table>

<br />

## **🧠 Main Content Panel**

Based on the module selected, the central panel displays:

-   ✅ Health status (e.g., `Running`, `Issues`)
-   📊 Graphs: CPU, memory, I/O, and network usage
-   📁 Tabs such as:
    
    -   `STATUS` – live system metrics
    -   `CONFIGURATION` – modify service parameters
    -   `HOSTS LIST` – view/assign cluster nodes
    -   `ISSUES` – shows alerts or configuration errors
    -   _(Additional tabs like_ `SIGNATURES`, `BUSINESS GROUPS` may appear in modules like Viewtimon/Viewtify)

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/FFJR414FsBeJhIGnjNJN.png"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/OE8BEXxdGhI1rsvHc5PP.png"></figure>

<br />

Contact Viewtinet support for licensing inquiries or to enable additional features.

<br />