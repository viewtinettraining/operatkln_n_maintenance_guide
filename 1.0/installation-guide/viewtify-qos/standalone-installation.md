---
reusableId: 105
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Standalone Installation'
id: 2DJ-N7C3-94R-9K7
slug: standalone-installation
isVisible: true
lastUpdated: '2025-10-15 10:34:00'
---
# **<span align="center">Installing the Viewtify QoS Module</span>**

<br />

> ⚠️ **Prerequisites & Disclaimers**
> 
> -   The **Viewtify QoS** feature must be licensed and visible under **Viewtify QoS** in the sidebar.
> -   **Viewtimon** must already be installed and running.
> -   **High-Availability (HA) is not supported** for Viewtify QoS in this release. You can only deploy a single-node instance.

---

## **Launch the QoS Installer**

1.  In the Viewtimanager UI, click **Viewtify QoS** in the left nav.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/ZhLfy030UTajqcjupsaf.png" align="center"></figure>
    
2.  Click the **INSTALL QOS** button.
    
    <br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/3pW2VhIXRaNx1p0HIhrc.png">
    

---

<br />

## **Add the Cluster Host**

1.  Under **Cluster for QoS**, click **\+ ADD NEW HOST**.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/PQO6d4eeYqFfpdTRaKQV.png" align="center"></figure>
    
2.  In the new row, enter:
    
    -   **Hostname or IP Address**: management IP (e.g. `10.30.23.4`).
    -   **LAN Hostname or IP Address**: same as above.
    -   **Password** / **Password confirm**: SSH password of the `viewtinet` user on that host.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/fyX8Urcv3SJu3QcnLQrA.png" align="center"></figure>
    
3.  Click **SAVE CHANGES**, then confirm:
    
    > “This module will be active in: 10.30.23.4” → **OK**
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/47LgIjH70AQypet9xYTy.png" align="center"></figure>

## **Finish the Installation**

1.  Wait for the installer log to stream and report **“Installation finished”**.
2.  Click **FINISH INSTALLATION**.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/gXfRvqikCkDex5c4vzJG.png" align="center"></figure>
    

### **Stop Viewtimon Before Interface Binding**

> ### Viewtify QoS requires exclusive binding of NICs, so you must first stop the Viewtimon service.

1.  Navigate to **Viewtimon → STATUS**.
2.  Click **STOP** and confirm **“Do you want to stop this module?” → YES**.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/J7aP4l3GWIz59zG6rf4H.png" align="center"></figure>
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/d6aDAJXV83rAIQrInAXN.png" align="center"></figure>

### **Assign Interfaces for QoS**

1.  Go to **Networking → INTERFACES**.
2.  For each probe NIC you wish to use with QoS, check the **Viewtify QoS** box.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/zNd62gHxWkr4LSP3EheD.png" align="center"></figure>
    
3.  Click **SAVE CHANGES**.
4.  Confirm the red banner: **“Please restart Viewtimon to apply config changes”**.
    
    <br />
    

---

### **Restart Viewtimon**

> ### Restarting Viewtimon will load the new QoS bindings.

1.  Return to **Viewtimon → STATUS**.
2.  Click **RESTART** (or **START**, if still stopped).
3.  Confirm **“Do you want to start this module?” → YES**.
4.  The Viewtimon indicator will turn green and both **Viewtimon** and **Viewtify QoS** status lights will become active.

---

🎉 **Viewtify QoS is now installed and running.**<br />
You can begin creating traffic-shaping and prioritization policies