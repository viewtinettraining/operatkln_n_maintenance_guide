---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Interfaces
slug: interfaces
isVisible: true
isSearchable: true
id: UW1-KO1-P3S-7TC
---
# **<span align="center">Interfaces</span>**

<br />

The **Interfaces** tab displays all the physical interfaces available on the machine along with their current configuration and status. This view is essential to identify which interfaces are assigned to the different DPI and QoS modules.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-interfaces-1.png" align="center"></figure>

<br />

---

## **Key Information Displayed**

For each physical interface, the system provides the following details:

- **ID, Name, and Interface:** Identifies the hardware port, its system name, and a brief description of the controller (e.g., *Ethernet Controller*).
- **Driver:** Displays the driver currently used by the interface. It is crucial to note that the **`igb_uio`** driver is specifically required for interfaces associated with the **Viewtimon** and **Viewtify QoS** modules to ensure proper high-performance packet processing.
- **Module Assignment (Viewtimon / Viewtify QoS):** Checkboxes indicate which module the interface is currently assigned to. Interfaces can be allocated to either Viewtimon (for monitoring) or Viewtify QoS (for traffic control).
- **Status:** Shows the physical link status of the interface:
  - 🟢 **Green Circle:** The interface is physically **UP** (connected).
  - ⚪ **Gray Circle:** The interface is physically **DOWN** (disconnected).

<br />