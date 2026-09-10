---
reusableId: 91
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Autodiscovery
id: 886-AHCG-3JX-Q97
slug: autodiscovery
isVisible: false
isSearchable: true
lastUpdated: '2026-05-26 16:07:32'
---
## **<span align="center"><span class="text-large">Provisioning via Autodiscovery</span></span>**

<br />

<span align="justify">Autodiscovery allows you to dynamically scan your network ranges and automatically onboard devices into Viewtinet—no CSV file required. Unlike CSV import (which relies on a static list of IPs/hostnames), Autodiscovery:</span>

-   **Discovers unknown devices** on the fly
-   **Gathers live SNMP/ICMP data** during the scan
-   **Auto-populates inventory fields** such as MAC address, sysObjectID, and systemName

---

### **Step 1: Launch Autodiscovery**

1.  In the Viewtinet web console, click **Inventory** → **AUTODISCOVERY**.
2.  Click **LAUNCH NEW AUTO DISCOVERY**.<br />
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/ph8kCTL7Ob1x3I4Jk7F5.png" align="center"></figure>

---

### **Step 2: Specify Targets**

Enter one or more nmap‐compatible target specifications in the **Targets** field. Supported formats include:

-   **Single IP**: `10.30.23.41`
-   **Range of IPs**: `10.30.23.41-50`
-   **CIDR block**: `10.30.23.0/24`
-   **Comma‐separated list**: `10.30.23.41,10.30.23.42,10.30.23.50`
-   **Hostname or DNS name**: `router1.example.com`
-   Then fill in **Pipeline Name**, **Depth**, **Execute Timeout**, and **Community string**, and click **RUN** to start the discovery.<br />
    

l

---

### **Step 3: Review & Pre-Process Results**

Once the scan completes (✅ icon):

1.  Select the execution ID in the left pane.
2.  Switch to the **DEVICES** tab under Autodiscovery.
3.  A preview table lists discovered hosts with columns like IP/Hostname, MAC, sw\_version, sys\_object\_id, and system\_name.
4.  Use the filter box or Query Builder to include or exclude devices before import.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/KqkUIcnfHxf2LnQNavEx.png" align="center"></figure>

---

### **Step 4: Import into Inventory**

1.  Tick the checkboxes for the devices you want to onboard (or use the header checkbox to select all).
2.  Click **IMPORT INTO INVENTORY** at the top right.
3.  The selected hosts are added to your main Inventory view, ready for credential relations and plugin assignments.
4.  Switch to the \*\*OVERVIEW\*\* tab under \*\*Inventory\*\* to see the newly imported hosts.<br />
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/kmSiJa5aXDQgeBSmESFX.png" align="center"></figure>

<br />

<figure align="center" style="width:53%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/M21oAe0BoMhZzRSviYRZ.png" width="53%" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/RAj1n2Zz3yTK9QIhfhjM.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/honsa5vZ8iuUF32xMGZj.png" align="center"></figure>

---

### **Step 5: Inventory Filtering**

<span align="justify">Viewtinet’s Inventory includes a powerful, flexible Filter Builder that lets you query, combine, and save device filters on‐the‐fly. Use filters to narrow down large inventories by any device attribute—IP/Hostname, vendor, OS version, and more.</span>

<br />

1.  **Open the Query Builder**<br />
    Click the pencil icon next to the filter box to launch the advanced Query Builder.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/MXu73yQf9PQRXkztxfqm.png"></figure>
    
    <br />
    
2.  **Add Rules or Groups**<br />
    In the builder modal, click **\+ Add Rule** to add a single condition, or **\+ Add Group** to combine multiple rules with AND/OR logic.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/tDSps7m7zKJLOrEJklbl.png"></figure>
    
    <br />
    
3.  **Select a Field**<br />
    For each rule, choose the inventory field you want to filter on (e.g., `device`, `ip`, `vendor`, `operating_system`).
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/xlDB8Eocp9EaZu4u55ye.png"></figure>
    
    <br />
    
4.  **Choose an Operator**<br />
    Pick an operator to define your match criteria:
    
    -   `==` (equals)
    -   `!=` (not equals)
    -   `Contains` / `Not contains`
    -   `Starts with` / `Ends with`
    -   `Is empty` / `Is not empty`
    
    <br />
    
5.  **Enter a Value and Apply**<br />
    Type the comparison value (e.g., `contains vlog`) and click **OK**. The filter expression appears in the main Inventory view.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/pQiVYiyFoCxueO9OLiWQ.png"></figure>
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/BUObc67Y0idfUhnNYFDb.png"></figure>
    
    <br />
    
6.  **Save Your Filter**<br />
    To reuse this filter later, click **SAVE FILTER**, give it a name, and click **OK**.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/ETWH7S4Rbm8yYQn3qAX5.png"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/TyELEQPUtYFvh4oPpzdK.png" align="center"></figure>

<br />
<span align="justify">With the Filter Builder you can quickly drill down into your inventory, combine complex conditions, and save your most-used queries for one-click access. Next, we’ll show how to create dynamic groups based on these filters.</span>

### <br />

**Step 6: Selecting and Assigning OID Groups**

<span align="justify">An OID Group is a named collection of SNMP Object Identifiers (OIDs) that specifies exactly which metrics and counters to poll from a device. By assigning OID groups, you ensure Viewtinet collects the correct set of SNMP data for each device type.</span>

### **Add the OID Groups Column**<br />

1.  In the Inventory view, click the **?** help icon, then choose **Add New Column**.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/sdPthHO5Dg0kgR3mAPX2.png"></figure>
    
    <br />
    
2.  In the **System Fields** modal, expand **VSDB** and click the **+** next to **oid\_group\_names**, then click **OK**.<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Z8nyy9z58mAbOekycAzm.png" align="center"></figure>
    
    <br />
    
    <figure align="center" style="width:44%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Y33N4DyecgDc0zPA5I5h.png" width="44%" align="center"></figure>
    
    <br />
    
3.  The new **oid\_group\_names** column now appears in your device list.
    
    <br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/OizNID3L0VLDfPz27pTq.png"></figure>
    
    ⚠️ **Note:** The **oid\_group\_names** column only needs to be added **once**; it will remain available in the inventory view thereafter.
    
    <br />
    
    **Filter and Assign OID Group Values**
    
    <br />
    
4.  Filter your data sources\*\*.\*\* Use the inventory filters to narrow down the devices you wish to configure—e.g., filter by system\_name `vlog`—so that OID groups are assigned only to the relevant subset.<br />
    
5.  Enter the OID group name\*\*.\*\* In the oid\_group\_names header input (or per-row cell), type the OID group name—comma-separated if assigning multiple groups (e.g. `net-SNMPAgent,general`)—and press **Enter**. A dropdown will suggest existing group names as you type.<br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/rcbmo0FluC7TpecKN6SD.png"></figure>
    
    <br />
    
6.  **Apply to your selection.** After pressing **Enter**, the group name is applied to all filtered (selected) rows or to individual rows as needed.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/4aZZbkyLX9r1YOx9hcBt.png" align="center"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/PZYnOtxUxQ4ZWC29hrjD.png"></figure>

### **Step 3: Save Your Changes**

<br />
Click **SAVE CHANGES** at the bottom right to persist your OID group assignments.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/DCkyap8nQzAZPY5XjIbx.png" align="center"></figure>

A confirmation banner will appear once the inventory is successfully saved.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/b6EsvUPa4hddixDTteBa.png" align="center"></figure>

---

### **Configuring Credentials**

In Viewtinet, **Credentials** define how the system authenticates both to **collect counters & metrics** (SNMP, ICMP, WMI) and to **manage configurations** (SSH/HTTPS) on your devices. Each protocol requires its own credential entry:

-   **ICMP**: Basic reachability and latency checks.
-   **SNMP v1/v2c/v3**: Poll counters, tables and other device metrics.
-   **SSH / Telnet**: CLI access for advanced configuration.

> ⚠️ **Note:** If during Autodiscovery you chose **Import credentials**, any SNMP credentials discovered will be automatically added to your inventory. In that case, the **only credential** you need to create manually is **ICMP**

If SNMP credentials were **not** imported via Autodiscovery, the following steps will show you how to configure them manually.

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
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/cPxzfyd6SZPeuSnc7Zr4.png" align="center"></figure>
    

<br />

## **Managing Device–Credential Relations**

<span align="justify">The Relations tab lets you assign one or more credential entries to a set of devices. You can use filters to select exactly the devices you need—e.g. all switches using SNMP v2c with a specific community—and then relate them to the matching SNMP credential.</span>

<br />

### **Step 1: Open the Relations Tab**

In the Inventory console, click **Relations** to view the device–credential mapping interface.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/DFACzLKlGIcuFAkiJkyt.png"></figure>

### **Step 2: Filter Devices**

Use the filter box or Query Builder to narrow the device list. You can pick a specific subset (for example `dev.sw_version == '2c'` or `dev.vendor == 'LINUX'`), or choose the All devices filter if every data source uses the same SNMP community (or for simple protocols like ICMP).

### <br />

**Step 3: Select Devices**

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/vJU5IFke2vtFfn3lKfHc.png"></figure>

Once filtered, use the checkboxes in the first column to select all matching devices (or pick individual entries).

### **Step 4: Select Credentials**

Scroll down to the Credentials panel. Use its filter to find the credential entry you want (for instance, your `snmp-2c-training` community). Then select the checkbox next to that credential.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/liOmqW0ZkTVsNPw0xenp.png" align="center"></figure>

### **Step 5: Save Relations**

Click **SAVE CHANGES** at the bottom right to apply your assignments. A confirmation toast will appear once the relations are saved.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/rqPy2bh7qTD1TmfvbVPH.png" align="center"></figure>

<span align="justify">By using filters together with bulk selection, you can quickly assign specific credential sets—SNMP communities, SSH keys, or ICMP settings—to exactly the devices that need them, ensuring each device uses the correct authentication parameters</span>.

---

## **Installing Plugins**

<br />

Viewtinet uses a **plugin framework** to map inventory data into data‐processing pipelines. In this section we’ll install the **Network Monitoring** plugin for all of your data sources.

<br />

> ⚠️ **Disclaimer:** Because we’re applying **all** data sources to the **Network Monitoring** plugin, **no filters** are used in this step. Filters become essential when you want to install **vendor-specific** plugins only on certain devices.

---

<br />

### **Step 1: Open the Plugins Tab**

In the Inventory console, click **PLUGINS**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/2SiOKpo4yqgk0Y5Stzmb.png" align="center"></figure>

### <br />

**Step 2: (No Filters) Select “All devices”**

Since we’re installing across every data source, check the **All devices** filter.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/XwzPHTpvcjM6LwxBrGXL.png"><br />

### **Step 3: Pick the Network Monitoring Plugin**

In the **Plugins** panel, expand **network monitoring** and select:

-   **snmp\_device\_config**
-   **snmp\_if\_config**
-   **icmp**<br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/qJQlxOW78mTTJYjCoBL7.png">

<br />

### **Step 4: Modify and Install**

Click **MODIFY AND INSTALL PLUGINS** at the bottom right.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/kq16Kb1vv4xS6zHgQp2P.png"><br />

### **Step 5: Confirm Plugin Selection**

In the **Select plugins** modal:

1.  Ensure **network monitoring** is checked under **PLUGINS TO BE MODIFIED**
2.  Check **Also INSTALL them**
3.  (Optional) Check **Unattended installation**
4.  Click **OK**<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/aIftba2pgGkskspMAdit.png" align="center"></figure>
    
    <br />
    

### **Step 6: Installation Success**

A green toast confirms:

> **1 plugins successfully modified. Redirecting to V.S. Data Broker…**<br />
> 
> <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/HU2IAsKk1LIqnsKJpa6V.png" align="center"></figure>
> 
> <br />

You’ll be redirected to **Visual Smart Data Broker**. Click **FINISH INSTALLATION** to complete the process.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/BIvAlNoBMTl2Hm4sYHMi.png" align="center"></figure>

At this point, according to your pipeline configuration, **metrics, counters, and all dimensions** from your data sources are now being ingested into the database for analysis and dashboarding.

With Autodiscovery, you can keep your inventory fresh and accurate by discovering, filtering, and importing devices in a single workflow—no manual CSV editing necessary<br />