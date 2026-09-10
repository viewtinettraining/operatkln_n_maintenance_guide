---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Introduction
slug: intro
isVisible: true
isSearchable: true
id: H4I-A1D-ZM6-Q3O
---
# **<span align="center">Networking</span>**

<br />

This section covers the networking configurations for the **Viewtimon** and **Viewtify QoS** modules. It is important to note that this configuration has **nothing to do** with the management network configuration of the appliance or the service network used for log collection, metrics, SNMP, Netflow, and APIs by the Viewtilog module.

<br />

---

## **Management & Service Planes in DPI Solutions**

In the context of DPI (Deep Packet Inspection) solutions, **management** and **service planes** refer to the distinct functional layers that handle different aspects of network operations:

- **Management Plane:** This plane is responsible for the configuration, monitoring, and administration of the DPI solution. It includes functionalities such as policy enforcement, user authentication, system logging, and performance monitoring.
- **Service Plane (Wire Data):** This plane focuses on processing and analyzing network traffic. It handles tasks such as packet inspection, traffic classification, QoS enforcement, and security policies application.

These planes work together to ensure efficient network traffic analysis, policy enforcement, and overall system reliability.

<br />

---

## **Interface and IP Address Combinations for Viewtimon**

Viewtimon works with a copy of the traffic, which can be provided through port-mirroring, using a TAP, or with port span. In this case, each interface captures network traffic without interfering with its flow.

- **No interface pairing is required**, meaning that if there are **M interfaces, all can be used simultaneously (Service Plane)**.
- **IP addresses are assigned only to management interfaces (Management Plane)**.

<br />

### **Viewtimon Deployment**

Viewtinet needs to receive a copy of IP traffic for Wire Data observability. As illustrated below, this can be done with a TAP, port span, or packet broker.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-intro-3.png" align="center"></figure>

<br />

---

## **Interface and IP Address Combinations for Viewtify QoS**

- Viewtify QoS operates in **bridge mode** at Layer 2 of the OSI model.
- A **Bridge mode** deployment typically requires **pairs of interfaces** to act as a transparent bridge.
- If there are **N physical interfaces**, they can be grouped into pairs to form **N/2 Bridge links**.
- Since traffic passes through without modifying IPs, interfaces in Bridge mode **usually do not have assigned IP addresses (Service Plane)**, except for a dedicated management interface **(Management Plane)**.

<br />

### **Viewtify Deployment**

For Traffic Control, Viewtinet needs to be deployed inline with a passive bypass.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-intro-5.png" align="center"></figure>

<br />

---

## **The Viewtinet Bypass Device**

The bypass is a mandatory device when deploying Viewtify QoS inline. The **Bypasser** is a watchdog process for the Classifier (The Probe).

- The Bypasser process sends periodic heartbeats to the Viewtinet Bypass device to indicate that the Classifier is up and running normally.
- Sending heartbeats puts/keeps the Bypass device in an **Active State**, so network traffic is directed through the Appliance Server (The Probe).
- If the Bypasser process stops sending heartbeats (indicating failure), the Bypass device switches internally to **Bypass State**, so network traffic is bypassed directly between the LAN and Internet, not sending traffic through the Appliance server.

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-1.png" align="center">
  <figcaption><b>Picture 1: The Bypasser's role in the big picture.</b></figcaption>
</figure>

<br />

### **Heartbeats and Operations**

- Heartbeats are sent every 100 ms by the Bypasser process to the Bypass device to indicate that everything is OK.
- If the Bypasser process detects an error, no heartbeats are sent.
- The Bypasser process is used as a Watchdog for The Probe. Optionally, extensions may be used as Watchdogs for other services, such as Viewtify OPT.
- The Bypasser process also handles Heartbeats, USB detection, and acts as a configuration server, controlled by the ViewtiManager.
- The Watchdogged process (The Probe) is a "smart watchdogged process", which indicates if it is "operational" or not through Push Notifications. In this case, "operational" means that The Probe is running and may process incoming network traffic.
- The Bypasser process subscribes to the Push Notifications to detect any "operational changes" in The Probe.
- The ViewtiManager can control the Bypasser process through its web-based GUI.
- All communication between the Bypasser process and the Bypass device goes through a USB cable. The Bypass device also uses USB as its power supply. Without power, the Bypass device switches to Bypass State automatically.

### **Failure Detection**

If the Viewtinet Bypass device does not receive a heartbeat within a (configurable) timeout period, this is considered a failure, and the device switches to Bypass State. Failures are defined as:

- Classifier failure (reporting NOT_READY, process died, not responding to Bypasser, etc.)
- Bypasser failure (process died, etc.)
- Server failure (power off, kernel panic, etc.)
- USB cable disconnected (this powers off the Viewtinet Bypass device)

### **Active State & Bypass State**

- Without any failures, the Viewtinet Bypass device should send all traffic to the Classifier, and is said to be in an **Active State**.
- When a failure occurs, the Viewtinet Bypass device redirects all traffic, and is said to be in a **Bypass State**.
- The Viewtinet Bypass device may be configured to work either in the Active State or in the Bypass State without any power (that is, when the USB cable is disconnected).

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-2.png" align="center">
  <figcaption><b>Picture 2: The Bypass device in the Active State and in the Bypass State, respectively.</b></figcaption>
</figure>

<br />

### **MultiSegment**

The Bypass device may use up to 8 segments (depending on how many hardware modules are installed). Each segment may use an individual network traffic route.

- With the MultiSegment option **disabled**, the same settings are applied to all segments. That means that bypassing an Appliance Server on one segment (`FORCE_BYPASS`), is also applied to all other segments.
- With the MultiSegment option **enabled**, each segment may be set to `NORMAL_OPERATION` or `FORCE_BYPASS` individually. That means that traffic on one segment may bypass an Appliance Server (`FORCE_BYPASS`), while traffic on another segment is processed by the Appliance Server (`NORMAL_OPERATION`).

<br />
