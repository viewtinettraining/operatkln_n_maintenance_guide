---
reusableId: 87
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Cluster Installation'
id: NQU-2BQB-PAX-CE8
slug: cluster-installation
isVisible: true
lastUpdated: '2025-10-15 10:16:28'
---
# **<span align="center">Cluster-Mode Installation for Viewtisight</span>**

<br />

<span align="justify">By default, the graphical user interface modules Viewtisight, Viewtimanager, and Viewtiaut alongside the Viewticore module are installed together in a “Standalone” deployment. Consequently, there is no separate installation chapter for these components. When you need a clustered, high-availability setup with two or more nodes, however, you must add and configure each additional server. This chapter details the steps to deploy a second Viewtisight node.</span>

<br />

## **Prerequisites**<br />

### **Mandatory Requirements**

-   **Primary node installed and licensed**: The first cluster node must be fully installed and operational via the bundle installation process.
-   **Cluster size**: At least **2 nodes**—one designated as **master**, the other as its **mirror**.
-   **Floating VIP**: A dedicated IPv4 address for failover.
-   Ensure system clocks on all cluster nodes are synchronized; integration with an NTP service is mandatory

<br />

### **Recommended for Optimal Performance**

-   **Homogeneous hardware**: Identical CPU, RAM, and storage across all cluster nodes.
-   **Separate inter-node network**: An additional NIC on each server for heartbeat and synchronization, using its own Virtual IP.
    
    <br />
    

### **Network Overview**

Below is a high-level view of a two-node, high-availability Viewtisight cluster:

-   **Client access**: All traffic (HTTP/HTTPS) goes to the floating VIP **10.30.23.21**, managed by Keepalived.
-   **Master node**: **Node 1** (eth0: 10.30.23.5) receives traffic by default.
-   **Failover node**: **Node 2** (eth0: 10.30.23.6) takes over if Node 1 fails.
-   **Heartbeat & sync**: A dedicated link between **10.100.100.100** (Node 1 eth1) and **10.100.100.101** (Node 2 eth1) carries cluster state and health checks.
-   **Additional configuration** To enable inter-node communication, you must configure the extra NICs via Netplan—edit the YAML files in \`/etc/netplan/\` to assign the static 10.100.100.x addresses.
    
    <br />
    
    <div class="sd-callout" data-callout-type="warning">Interface names (e.g., <code>eth1</code>) may vary depending on your OS and naming conventions; adjust accordingly.</div>
    

<span align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/st3TBf1ZPapYO8coCI5t.png"></span>

### **<br />
Ports Configuration**

<span align="justify">If your Viewtinet cluster nodes are spread across geographically separate data centers, reside in different subnets, or sit behind firewalls or VPN gateways, you must explicitly open all required service and HA-Proxy ports on every security device (firewall rules, router ACLs, cloud security groups, etc.). This includes MongoDB replica ports (23450, 23459), backend/frontend HTTP/HTTPS ports (4500–4605), Viewticore and Dhyana ports (8091, 9988, 9095), and HA-Proxy listener ports (4000–5001, 8080, 443). If any of these ports remain blocked, inter-node synchronization, health checks, and user access to the management UIs will fail, and the HA cluster will not function.<br></span>

Below is the list of service ports published by each component and the HA-Proxy front-end ports for a two-node HA setup:

<br />

<table><tbody><tr><th><p><span align="center">Component</span></p></th><th><p><span align="center">Service Port</span></p></th><th><p><span align="center">HA-Proxy Port</span></p></th></tr><tr><td><p><span align="center">Viewtiauth-mongo</span></p></td><td><p><span align="center">23450</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtiauth-mongo-arbiter</span></p></td><td><p><span align="center">8540</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtiauth-backend-HTTP</span></p></td><td><p><span align="center">4500</span></p></td><td><p><span align="center">4000</span></p></td></tr><tr><td><p><span align="center">Viewtiauth-frontend-HTTP</span></p></td><td><p><span align="center">4600</span></p></td><td><p><span align="center">4200</span></p></td></tr><tr><td><p><span align="center">Viewtiauth-backend-HTTPS</span></p></td><td><p><span align="center">4501</span></p></td><td><p><span align="center">4001</span></p></td></tr><tr><td><p><span align="center">Viewtiauth-frontend-HTTPS</span></p></td><td><p><span align="center">4601</span></p></td><td><p><span align="center">4201</span></p></td></tr><tr><td><p><span align="center">Viewtisight-mongo</span></p></td><td><p><span align="center">23459</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtisight-mongo-arbiter</span></p></td><td><p><span align="center">8451</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtisight-backend-HTTP</span></p></td><td><p><span align="center">4502</span></p></td><td><p><span align="center">4101</span></p></td></tr><tr><td><p><span align="center">Viewtisight-frontend-HTTP</span></p></td><td><p><span align="center">4602</span></p></td><td><p><span align="center">8080</span></p></td></tr><tr><td><p><span align="center">Viewtisight-backend-HTTPS</span></p></td><td><p><span align="center">4503</span></p></td><td><p><span align="center">4102</span></p></td></tr><tr><td><p><span align="center">Viewtisight-frontend-HTTPS</span></p></td><td><p><span align="center">4603</span></p></td><td><p><span align="center">443</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-mongo</span></p></td><td><p><span align="center">23451</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-mongo-arbiter</span></p></td><td><p><span align="center">8452</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-backend-HTTP</span></p></td><td><p><span align="center">4504</span></p></td><td><p><span align="center">1337</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-frontend-HTTP</span></p></td><td><p><span align="center">4604</span></p></td><td><p><span align="center">5000</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-backend-HTTPS</span></p></td><td><p><span align="center">4505</span></p></td><td><p><span align="center">1339</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-frontend-HTTPS</span></p></td><td><p><span align="center">4605</span></p></td><td><p><span align="center">5001</span></p></td></tr><tr><td><p><span align="center">Viewticore-gateway</span></p></td><td><p><span align="center">8091</span></p></td><td><p><span align="center">8090</span></p></td></tr><tr><td><p><span align="center">Viewticore-alarms</span></p></td><td><p><span align="center">9988</span></p></td><td><p><span align="center">9987</span></p></td></tr><tr><td><p><span align="center">Dhyana</span></p></td><td><p><span align="center">9095</span></p></td><td><p><span align="center">N/A</span></p></td></tr></tbody></table>

<br />

---

<br />

## **Adding a Second Node via Viewtimanager**

<br />

Follow these steps to deploy the second node for **Viewtisight**, **Viewtimanager** and **Viewtiauth** modules from the master:

-   **Log in to Viewtimanager (Master)**
    
    -   Open your browser and navigate to<br />
        `http://MASTER-NODE-IP:4200/`
    -   Authenticate with your administrator credentials and choose Viewtimanager.<br />
        
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/d1evQxpHA2lOK9OUbj8g.png"></figure>
    
    <br />
    
    <figure align="center" style="width:51%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/3vTRuPMSbOvFkCQZI9v4.png" width="51%" align="center"></figure>
    
    <br />
    
-   **Navigate to the Viewtisight Hosts Tab**
    
    -   In the left‐hand menu, click **Viewtisight**.<br />
        
    
    <figure align="center" style="width:46%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/Pv2ipyiPw87a79CYZoZd.png" width="46%" align="center"></figure>
    
    -   Select the **Hosts** tab at the top of the page.
        
        <br />
        
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/ObLdrCbd5ZrP449RxiPn.png" align="center"></figure>
    

### **Add the Second Node to Viewtisight**

-   Click **Add New Host**:

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/ExoBlLBZcstkvswwMLdh.png" align="center"></figure>

-   If Node 1’s configuration uses the same IP address for both the “Hostname or IP Address” and the “LAN Hostname or IP Address,” you must update the inter-node communication network IP to match the dedicated network defined for this purpose.
-   **Hostname or IP Address**: Specify the fully qualified domain name (FQDN) or the management interface IP of Node 2 (for example, \`10.30.23.6\`).
-   **LAN Hostname or IP Address** : Specify the fully qualified domain name (FQDN) or the inter-node communication interface IP of Node 2 (for example, \`10.100.100.2\`).
-   **Password & Password confirm**: Supply the same SSH credentials used for Node 2

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/xkQUZT64sXfBCFC9uEbl.png" align="center"></figure>

<br />

-   Click **ADD NEW VIRTUAL ADDRESS:**
-   **Virtual IP Address:** Specify the fully qualified domain name (FQDN) or the Virtual IP (VIP) address (e.g., 10.30.23.21).
-   Click **Save**.
-   Confirm changes

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/G7cbEmXoE5flk5NrPG4O.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/Oo1WRrTZCzMUDah9c1ys.png" align="center"></figure>

-   Wait until the new host’s status indicator turns **Online** or **Healthy**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/yxcTikUbOCehS7nD7JmY.png" align="center"></figure>

<br />

-   <span align="justify">Because each server requires its own license under the Viewtinet model, you must obtain the </span> `server-info.txt` file as described in the “Getting Server Info” section of the “Bundle Installation” chapter.
-   <span align="justify">Once you have received the license file from your Viewtinet representative, perform the “Admin User Activation” and “Upload License” steps on the second cluster node as described in the corresponding sections of the “Bundle Installation” chapter.</span>
    
    <br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/hyRlkoqouQjbs3txAQHT.png"></figure>
    
    <br />
    

<br />