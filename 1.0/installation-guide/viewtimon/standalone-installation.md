---
reusableId: 102
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Standalone Installation'
id: 3QS-ZQO7-DIX-JDN
slug: standalone-installation
isVisible: true
lastUpdated: '2025-07-17 11:25:11'
---
# **<span align="center">Installing the Viewtimon Module</span>**

> ⚠️ **Prerequisites & Disclaimers**
> 
> -   The **Viewtimon** feature must be licensed and visible under **Viewtimon** in the sidebar.
> -   **High-Availability (HA) is not supported** for Viewtimon in this release. You can only deploy a single-node instance.

---

### **Launching the Installer**

1.  Log in to **Viewtimanager** as an admin or a user with install privileges.
2.  In the left navigation, click **Viewtimon**.
3.  Click the **INSTALL VIEWTIMON** button.}
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/OT95DV0aQBm6aF7KZOch.png" align="center"></figure>
    

### **Defining the Cluster Host**

> Since HA is not supported, you will only configure a single node.

1.  Under **Cluster for Viewtimon**, click **\+ ADD NEW HOST**.
    
    <br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/K8cnKPmbJnkcb19G4bH0.png">
    
    <br />
    
2.  In the **Cluster Host List** row, enter:
    
    -   **Hostname or IP Address**: the management IP of your Viewtimon server (e.g. `10.30.23.4`).
    -   **LAN Hostname or IP Address**: same as above.
    -   **Password** and **Password confirm**: the SSH password for the `viewtinet` user on that host.
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/oKm9TleIgcASvcXdKDR1.png">
    
    <br />
    
3.  Click **SAVE CHANGES**, then confirm the dialog:
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/V7zJCYgoIwlSHtp95y6c.png" align="center"></figure>
    

<br />

### **Running the Installer**

1.  Once the host is accepted, the installation log will stream in the panel.
2.  Wait until you see **“Installation finished”** and no fatal errors.
3.  Click **FINISH INSTALLATION** to complete.
    
    <br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/DGdvQs9RTorsIrbsAAgz.png">
    

---

### **Assigning Traffic Interfaces**

1.  Navigate to **Networking → INTERFACES**.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/pQoATLuNFRwYgIf1NUR6.png" align="center"></figure>
    
2.  Locate the NICs you wish to dedicate to Viewtimon.
3.  Check the **Viewtimon** box for each interface (do **not** enable HA).
4.  Click **SAVE CHANGES**, then confirm the red banner:
    
    > “Please restart Viewtimon to apply config changes”
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/AgESE5h1xa4wtmDeZUFE.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/1k2LWlMSnyGo4h4k5VY4.png" align="center"></figure>

### **Starting the Service**

1.  Return to **Viewtimon → STATUS**.
2.  Click **START**.
    
    <br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/VsvsBv7XhHJQGfGnwsZU.png">
    
    <br />
    
3.  Confirm the prompt **“Do you want to start this module?”** by clicking **YES**.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/HGyEMTPrv0ljWju9ScMk.png" align="center"></figure>
    
4.  The Viewtimon status indicator will turn green and performance graphs will appear.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/7MSwma8VHOuuETm2ysB6.png" align="center"></figure>

🎉 **Viewtimon is now installed and running.** You can monitor real-time traffic