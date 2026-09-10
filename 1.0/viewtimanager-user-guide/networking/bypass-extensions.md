---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Bypass Extensions'
slug: bypass-extensions
isVisible: true
isSearchable: true
id: 9PX-AV4-WBK-OXM
---
# **<span align="center">Bypass Extensions</span>**

<br />

The **BYPASS EXTENSIONS** tab provides a list of the available Bypasser plugins installed on the system. It is important to note that **this page is strictly informational**, meaning it displays the status and basic configuration of the extensions, but their operational state (enabled/disabled) is managed from the Bypass Config tab or other sections.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-extensions-1.png" align="center"></figure>

<br />

---

## **How Bypass Extensions Work**

A Bypasser plugin functions as an **additional Watchdog** for the appliance. 

While the "main" Bypasser Watchdog observes any changes to the classifier process ("The Probe"), a plugin can observe essentially anything that yields a "boolean" result (i.e., reporting either **OK** or **ERROR**).

### **Logical AND Operation**
When one or more plugins are enabled, they form a **"logical AND"** condition together with the main Bypasser Watchdog. This means that:
- **ALL** results must return `OK/READY` for the Bypasser to consider the system to be in a normal operational state.
- If **at least one** plugin is failing, the Bypass device is immediately set to `FORCE_BYPASS`.

### **Example: Viewtify OPT Plugin**
For instance, the **Viewtify OPT** plugin acts as a Watchdog specifically for the Viewtify OPT service. 
If this plugin is enabled, both *The Probe* and the *Viewtify OPT service* must report success. If either of them fails, the Bypasser stops sending heartbeats, and the Bypass device is forced into the `FORCE_BYPASS` state.

---

## **Extension States**

There is always a fixed number of deployed (available) plugins that are installed together with the Bypasser itself. However, an extension can either be enabled or disabled:

- **Disabled Extension:** Does not affect the internal state or the decision-making of the Bypasser.
- **Enabled Extension:** Actively monitors its assigned service and can force the system into bypass if it detects a failure (as described in the example above).

<br />