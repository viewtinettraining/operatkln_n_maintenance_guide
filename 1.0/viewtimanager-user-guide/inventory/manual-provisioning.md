---
reusableId: 92
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Manual Provisioning'
id: 0ZW-JMJT-U8F-TQY
slug: manual-provisioning
isVisible: true
isSearchable: true
lastUpdated: '2026-06-04 07:53:27'
---
# **<span align="center">Manual Provisioning</span>**

<span align="justify">Manual provisioning is the last resort for onboarding data sources into your inventory when CSV import or Autodiscovery are not feasible (for example, for isolated devices or one-off entries). It allows you to add individual devices one at a time and fill in only the fields you need.</span>

---

## **Step 1: Open the Devices Overview**

1.  In the Viewtinet web console, click **Inventory** in the left menu.
2.  Select the **OVERVIEW** tab.
3.  Ensure **DEVICES** is active.
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/0tBi4Nrk7U6B7I4LzHrT.png"><br />
    

---

### **Step 2: Add a New Device Row**

Scroll to the bottom of the device list and click **\+ ADD NEW DEVICE**.<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/F5rfRcbeKTL193zgcOwR.png"></figure>

A blank row appears at the top or bottom of the table where you can enter device details.

---

### **Step 3: Fill in Mandatory and Optional Fields**

Enter the required information and any additional details:

<table><tbody><tr><th><p>Field</p></th><th><p>Description</p></th><th><p>Required?</p></th></tr><tr><td><p><strong>IP / Hostname</strong></p></td><td><p>Device’s IP address or DNS name</p></td><td><p>Yes ⭐</p></td></tr><tr><td><p><strong>oid_group_names</strong></p></td><td><p>Comma-separated OID group(s)</p></td><td><p>Yes ⭐</p></td></tr><tr><td><p><strong>sw_version</strong></p></td><td><p>Software/OS version (e.g. Forti OS 7.10)</p></td><td><p>No</p></td></tr><tr><td><p><strong>source</strong></p></td><td><p>Inventory source (e.g. <code>user_defined</code>)</p></td><td><p>No</p></td></tr><tr><td><p><strong>device</strong></p></td><td><p>Friendly device name</p></td><td><p>No</p></td></tr><tr><td><p><strong>mac</strong></p></td><td><p>MAC address</p></td><td><p>No</p></td></tr><tr><td><p><strong>sys_object_id</strong></p></td><td><p>SNMP sysObjectID</p></td><td><p>No</p></td></tr><tr><td><p><strong>system_name</strong></p></td><td><p>SNMP systemName</p></td><td><p>No</p></td></tr></tbody></table>

> In the example below, **red** outlines indicate mandatory fields; **blue** outlines show optional fields:<br />
> 
> <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/28EBGy32GS1VuH0daxa1.png" align="center"></figure>

---

### **Step 4: Save Your Entry**

Once you’ve completed the fields, scroll down and click **SAVE CHANGES**. A confirmation banner will appear:

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/CfVxgjH8g4f4g0NSrgEs.png" align="center"></figure>

<span align="justify">Your device is now in the inventory and ready for credential assignments, relation mapping, and plugin configuration as detailed in earlier chapters.</span>

### **Configuring Credentials**

<span align="justify">In Viewtinet, Credentials define how the system authenticates both to collect counters &amp; metrics (SNMP &amp; ICMP) and to manage configurations (SSH/Telnet) on your devices. Each protocol requires its own credential entry:</span>

-   **ICMP**: Basic reachability and latency checks.
-   **SNMP v1/v2c/v3**: Poll counters, tables and other device metrics.
-   **SSH / Telnet**: CLI access for advanced configuration.<br />
    

### **Step 1: Open the Credentials Tab**<br />

1.  In the Viewtinet web console, click **Inventory → Credentials**.
2.  The Credentials table shows existing entries and supported protocol columns.
    
    <br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/hqDwDbbd9JssBb4T7vcQ.png">
    

<br />

### **Step 2: Add a New Credential**<br />

1.  Click **\+ ADD NEW CREDENTIAL** at the bottom of the table.
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/4Iyvj9HhwA7wAEGhMEIN.png"><br />
    
2.  A new blank row is added. Under **Protocol**, select the desired protocol (e.g., **snmp**).
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/ZwfBwI3MFDPy4wETiOyx.png"><br />
    

### **Step 3: Configure SNMP Credentials**<br />

1.  In the **SNMP Version** column, choose **2c** (or v1/v3 as needed).
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/sL9Qqkc4gIvotWf4RNvL.png"><br />
    
2.  Enter the **Community** string (mandatory for v1/v2c).
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/XjTleODdmXQNcldspFk8.png"><br />
    <span align="center">(In this example, we use training.)</span><br />
    
3.  For **SNMP v3**, you would also fill in **Security Level**, **Auth Protocol**, **Auth Passphrase**, **Priv Protocol**, and **Priv Passphrase**.

<br />

### **Step 4: Save Your Changes**

1.  After completing all required fields, click the **SAVE CHANGES** button at the bottom right.
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/gATCIy4xaapGL0n371bV.png"><br />
    
2.  A success notification confirms your credentials were saved.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/CfVxgjH8g4f4g0NSrgEs.png" align="center"></figure>
    

---

<br />

## **Mapping Credentials to Manually Added Devices**

Once you’ve added devices manually, you can assign one or more credential sets (ICMP, SNMP, etc.) to them via the **Relations** tab:

<br />

### 1\. Switch to the Relations View

Click **Relations** under the Inventory header.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/M434Wi0r1xSTV0mZ8uVO.png" align="center"></figure>

### **2 Isolate Your Manual Device**

Use the filter box or Query Builder to select just your manually added host (e.g. `dev.ip == '10.10.10.1'`).

-   Click the pencil icon to open Query Builder.
-   Add a rule: **ip == 10.10.10.1**, then click **OK**.

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/PFvq1gQUmWnNQz9uEcPE.png"><br />
<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/gWZoUG7ischO3WERtMW7.png"><br />
<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/k5J2VLIUXSHI7fwv5tiV.png"><br />
<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/GXCSoUvQJob9PB30VKBy.png"><br />

### **3\. Select the Device(s)**

Check the box next to the device row(s) you want to map credentials for.<br />

### 4\. Select Credential(s)

Scroll down to the **Credentials** pane, apply any filters if needed, and check the boxes for the credentials to assign (e.g. ICMP & SNMP).<br />

### 5\. Save the Relations

Click **SAVE CHANGES** at the bottom right. A confirmation banner will appear.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/kWCwmObEro6HVfTWQHsr.png"><br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/M37UrzvpYxOBhrhKY7bS.png" align="center"></figure>

Your manually added device(s) are now correctly related to the chosen credential sets.

---

## **Installing Plugins**

The final step in provisioning your data sources is to install—or modify—one or more Viewtinet plugins. In this guide, we’ll demonstrate installing the **Network Monitoring** plugin for the devices you’ve just defined.

> **Note:** In this example we’re installing **all** data‐source plugins under **Network Monitoring**, so we don’t apply a device filter. However, you _can_ use filters when you need to install plugins only for a specific vendor or device group.

<br />

### **1\. Switch to the Plugins Tab**

Click **PLUGINS** in the Inventory header.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/EuzQxt95Yl2BNABFbOFA.png">

<br />

### **2\. Define a Filter for Your Plugin Scope**

If you only want to modify/install for a specific device group, click **\+ ADD NEW FILTER**, name it, open the Query Builder, add a rule (e.g. `dev.ip == '10.10.10.1'`), and click **OK**.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/MPI9StDO2yZmtp92gmyp.png"><br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/d6mgL8jo92Cx4c8K7O0Y.png" align="center"></figure>

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/cBQ7Ml5ZS0kfJHMiFZI1.png"><br />

<br />

### **3\. Associate Devices with Plugins**

In the PLUGINS list, expand network monitoring and check the boxes for:

-   snmp\_device\_config
-   snmp\_if\_config
-   icmp

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/MHwRhXZFN3Of76WJw4mV.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/EIfmkGcsTFdR7XBQrY0J.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/LEBBavUUpm7aaeOOlLHP.png" align="center"></figure>

<br />

### **4\. Start the Modify & Install Process**

<br />

Click **MODIFY AND INSTALL PLUGINS** at the bottom right.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/njWjunon8KXcL25Cizes.png"><br />

<br />

### **5\. Confirm Plugin Actions**

In the “Select plugins” dialog:

-   Ensure **Network Monitoring** is checked under **PLUGINS TO BE MODIFIED**
-   Check **Also INSTALL them**
-   Check **Unattended installation**
-   Click **OK**

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/5OhwEfQMIXOOSf0Nwvxh.png" align="center"></figure>

<br />

### **6\. Finish Installation**

A success banner confirms the plugin was modified. You’ll be redirected to the Visual Smart Data Broker console—click **FINISH INSTALLATION** to complete.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Y8TUddYn4gzRAFtsIVkg.png" align="center"></figure>

With this complete, your pipelines will now begin pulling metrics, counters, and other data dimensions into the database according to the configuration you’ve defined.

<br />
<br />
<br />
<br />
<br />
<br />

<br />