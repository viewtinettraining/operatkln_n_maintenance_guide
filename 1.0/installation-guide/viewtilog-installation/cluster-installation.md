---
reusableId: 88
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Cluster Installation'
id: ND7-Z3HP-QAV-NIZ
slug: cluster-installation
isVisible: true
lastUpdated: '2025-10-15 10:22:27'
---
# **<span align="center">Cluster-Mode Installation for Viewtilog</span>**

<br />

<span align="justify">When deployed in High-Availability (H.A.) mode, Viewtilog operates as a cluster of two or more nodes that continuously collect and replicate monitoring and log data. This encompasses network performance metrics via SNMP,NetFlow records,syslog messages,call detail records (CDRs), and any other enabled sources. A floating VIP managed by Keepalived and load-balanced by HAProxy ensures uninterrupted ingestion: if one node fails, traffic automatically shifts to the backup, while under normal conditions the load is evenly distributed. Advanced clustering and load-balancing configurations are documented in the Viewtilog User Guide.</span>

<br />

## **Prerequisites**<br />

### **Mandatory Requirements**

-   **Primary node with Viewtilog installed and licensed**: The first cluster node must have Viewtilog fully installed, licensed (including the H.A. feature), and operational via the bundle installation process.
-   **Cluster size**: At least **2 nodes**—one designated as **master**, the other as its **mirror**.
-   **Floating VIP**: A dedicated IPv4 address for failover.
-   Ensure system clocks on all cluster nodes are synchronized; integration with an NTP service is mandatory

### **Recommended for Optimal Performance**

-   **Homogeneous hardware**: Identical CPU, RAM, and storage across all cluster nodes.
-   **Separate inter-node network**: An additional NIC on each server for heartbeat and synchronization, using its own Virtual IP.

### **Optional Requirements**

-   **Dedicated service subnet**: Use a separate network (e.g., 10.100.x.x/24) for all log and metric collection traffic.
-   **Additional network interfaces**: Configure additional NICs on each node using IP addresses outside the management network to isolate log and metrics collection traffic.
-   **Separate VLAN**: Place service and synchronization traffic on a dedicated VLAN to enhance both security and performance.

<br />

### **Network Overview**

In this High-Availability Viewtilog cluster, SNMP, ICMP and API-based metrics are actively polled by the Viewtilog nodes, whereas syslog and NetFlow traffic is pushed from the data sources to the floating VIP (10.30.23.21). The VIP directs incoming log and flow data to the active node’s management interface: normally \*\*Node 1\*\* (eth0: 10.30.23.5), with automatic failover to \*\*Node 2\*\* (eth0: 10.30.23.6) if the primary goes down. A dedicated inter-node link (eth1) at 10.100.100.100 ↔ 10.100.100.101 carries heartbeat, state synchronization, and replication traffic to keep the cluster coordinated.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/GqV7J5L0AXdNhO4L2t1T.png"></figure>

<br />

<div class="sd-callout" data-callout-type="warning">Interface names (e.g., <code>eth1</code>) may vary depending on your OS and naming conventions; adjust accordingly.<br></div>

<br />

## **Adding a Second Viewtilog Node via Viewtimanager**

<br />

Follow these steps to deploy the second node for **Viewtisight**, **Viewtimanager** and **Viewtiauth** modules from the master:

-   **Log in to Viewtimanager (VIP)**
    
    -   Open your browser and navigate to<br />
        `http://VIP-IP:4200/`
    -   Authenticate with your administrator credentials and choose Viewtimanager.

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/d1evQxpHA2lOK9OUbj8g.png"><br />
<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/3vTRuPMSbOvFkCQZI9v4.png" align="center"></figure>

-   **Navigate to the Viewtilog Hosts Tab**
    
    -   In the left‐hand menu, click **Viewtilog**.<br />
        

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/kg9NJU6ccpYUp0wo5qsK.png" align="center"></figure>

-   Select the **Hosts** tab at the top of the page.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/ATD3VSzFNjQj9Pu9vPbs.png" align="center"></figure>

## **Add the Second Node to Viewtilog**

-   Click **Add New Host**:

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/cytJw3BFf6ltd2sozuMW.png"></figure>

-   <span align="justify">If Node 1’s configuration uses the same IP address for both the “Hostname or IP Address” and the “LAN Hostname or IP Address,” you must update the inter-node communication network IP to match the dedicated network defined for this purpose.</span>
-   **Hostname or IP Address**: Specify the fully qualified domain name (FQDN) or the management interface IP of Node 2 (for example, \`10.30.23.6\`).
-   **LAN Hostname or IP Address** : Specify the fully qualified domain name (FQDN) or the inter-node communication interface IP of Node 2 (for example, \`10.100.100.2\`).
-   **Password & Password confirm**: Supply the same SSH credentials used for Node 2

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/lQ3ePdpGdoRij5qQuZSw.png"></figure>

-   Click **ADD NEW VIRTUAL ADDRESS:**
-   **Virtual IP Address:** Specify the fully qualified domain name (FQDN) or the Virtual IP (VIP) address (e.g., 10.30.23.21).
-   Click **Save**.
-   Confirm changes

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/WmbAR5g2dFrKqp5U2ULP.png"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/opuAOZSDeSq7YxumkKNx.png" align="center"></figure>

-   Wait until the ‘Installation Finished’ message appears.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/2wb3s63FPruz26GV6hQO.png"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/z06h397milw76pSOBr9x.png"></figure>

<br />