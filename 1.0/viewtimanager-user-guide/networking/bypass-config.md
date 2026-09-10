---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Bypass Configuration'
slug: bypass-config
isVisible: true
isSearchable: true
id: DVT-MAD-BHQ-LDF
---
# **<span align="center">Bypass Configuration</span>**

<br />

The **BYPASS CONFIG** tab allows you to configure the behavior of the network segments (pairs of physical ports). From this screen, you can manage how traffic is handled by the appliance, either processing it normally or bypassing it completely.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-config-1.png" align="center"></figure>

<br />

---

## **Global vs. Per-Segment Bypass**

The bypass functionality can be controlled either globally for the entire appliance or individually per segment.

- **Global Bypass:** You can set the entire appliance into bypass mode by using the global switch.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-config-3.png" align="center"></figure>
  <br />

- **Multi-segment Feature:** When the multi-segment feature is enabled, you can configure bypass settings for each segment individually. This allows you to set specific segments to *Normal Operation* while forcing others into *Bypass*.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-config-4.png" align="center"></figure>
  <br />

---

## **Per-Segment Configuration Options**

Expanding a segment provides several advanced configuration options tailored to specific networking needs:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-config-2.png" align="center"></figure>

<br />

- **Use VLANs:** 
  - By activating this checkbox, the QoS engine will classify the source of internal connections based on the VLAN tag of the packet. 
  - In QinQ environments, the outermost VLAN will be read. 
  - *Default Behavior:* If disabled, the QoS engine classifies the connection source using the IP address.

- **Extensions:** These dropdowns allow you to configure extensions for special use cases.

- **Use Fail Port:** 
  - When enabled, if one of the two ports in the segment fails, the system will automatically shut down the peer port of that segment. This forces the entire segment into bypass mode, ensuring traffic continuity.

- **One failure is enough:** 
  - Activating this option ensures that the segment enters bypass mode immediately upon a single failure. This prevents network "flapping" issues where intermittent link drops could cause the appliance to constantly switch in and out of bypass mode.

<br />