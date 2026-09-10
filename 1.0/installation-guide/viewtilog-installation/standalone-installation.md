---
reusableId: 77
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Standalone Installation'
id: OAK-P0VS-SIQ-GDI
slug: standalone-installation
isVisible: true
lastUpdated: '2025-10-15 10:18:48'
---
# **<span align="center">Standalone Installation of Viewtilog</span>**

> **Note:** This chapter covers a **standalone** installation of Viewtilog.<br />
> High-availability (cluster/H.A.) installations are described in Chapter 2.

---

## **Prerequisites**

-   A running instance of Viewtinet Manager with administrative GUI access
-   SSH credentials for the target host (same machine) where Viewtilog will be installed
-   Network connectivity between your browser and the Viewtinet Manager

---

## **Step 1: Open the Viewtilog Module**

1.  Log in to Viewtinet Manager as **admin**.
2.  In the left-hand navigation menu, click **Viewtilog**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/CbrW5OtEwUlMXqpQYW4B.png" align="center"></figure>

---

## **Step 2: Launch the Connector Installer**

1.  On the Viewtilog page, click the **Install Connectors** button.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/MPBJyXqcAbJCKATEUJce.png"></figure>
    

---

## **Step 3: Add the Host**

1.  In the **Cluster for Connectors** panel, click **\+ Add New Host**.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/JFvIKa6lD5DOhSV6zIfC.png"></figure>
    
    <br />
    
2.  Because this is a standalone install, enter the **same** IP address or hostname of this machine in both the “Hostname or IP Address” and “LAN Hostname or IP Address” fields.
3.  In the **Password** and **Password Confirm** fields, enter your **SSH** password for this host (not the GUI admin password).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/u4QKznxGBMKJjV6OSwKi.png" align="center"></figure>

<br />

---

## **Step 4: Save and Confirm**

1.  Click **Save Changes**.
2.  In the confirmation dialog, review the target IP address and click **OK**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/f2fGZb3SVYjEdRSVX5j6.png" align="center"></figure>

<br />
<br />

---

## **Step 5: Watch the Installation Progress**

1.  The installer will begin deploying the connector services via Docker.
2.  A live log will appear showing actions such as stopping old containers, pulling images, and creating new services.
3.  Wait until you see the message:

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/S11bPL8FbRAG072W3lL0.png" align="center"></figure>

---

## **Step 6: Complete the Installation**

1.  Once the log reaches the end, click **Finish Installation**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/1SlW2r00ACE7o9H6OSj9.png" align="center"></figure>

---

**Result:** Viewtilog is installed in standalone mode and is now available to run your ETL tasks.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/VIc3sU4DPnY144IRqS4i.png"></figure>

<br />

<br />