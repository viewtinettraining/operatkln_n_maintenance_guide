---
reusableId: 90
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Provisioning via CSV'
id: XC0-NIT9-X2F-TW5
slug: provisioning-via-csv
isVisible: true
isSearchable: true
lastUpdated: '2026-03-11 09:04:27'
---
## **<span align="center"><span class="text-large">Provisioning via CSV File</span></span>**

<br />

Viewtinet supports bulk onboarding of devices through a simple CSV import. You can design the CSV layout to suit your environment, but the following rules apply:

-   **Mandatory Field**
    
    -   `ip_address` _or_ `hostname`<br />
        One of these columns **must** be present in every row.
        
        -   If you choose `hostname`, ensure Viewtinet can resolve DNS names in your deployment network.
-   **Recommended Fields**<br />
    Adding extra columns will greatly improve your ability to filter, group, and manage devices. Common suggestions include:
    
    -   `location` (e.g. “Data Center 1”, “Building A”)
    -   `device_type` (e.g. “router”, “switch”, “firewall”)
    -   `vendor` (e.g. “Cisco”, “Juniper”, “Arista”)
    -   `model` (e.g. “ISR4451”, “EX4300”)
    -   `os_version` (e.g. “IOS XE 17.3.1”)
    -   `department` (e.g. “IT”, “Engineering”)

<br />

### **CSV File Guidelines**

1.  **Header Row**<br />
    The first line must contain column names. At minimum, include `ip_address` or `hostname`.
2.  **Delimiter**<br />
    Use comma (`,`) as the field separator. Quoted strings are supported.
3.  **Encoding**<br />
    UTF-8 without BOM is recommended to avoid parsing issues.
4.  **File Size**<br />
    For large inventories (&gt;10 000 rows), split into multiple CSVs of no more than 5 000 rows each to ensure smooth import.

### **Example CSV**<br />

```csv
ip,device,vendor,operating_system,sw_version
192.168.1.101,training,LINUX,Ubuntu 22.04,PROXMOX 8.1.4
10.30.23.1,cancerbero,LINUX,Free BSD,PFSense 2.7.2
10.30.23.2,guacamole,LINUX,Ubuntu 23.04,APACHE GUACAMOLE
10.30.23.4,ares,LINUX,Ubuntu 20.04,Viewtinet 6.3.5-Viewtify
10.30.23.5,zeus,LINUX,Ubuntu 20.04,Viewtinet 6.3.5-Viewtilog
10.30.23.6,dante,LINUX,Ubuntu 20.04,Viewtinet 6.3.5-Viewtilog
10.30.23.7,apolo,LINUX,Ubuntu 24.04,Viewtinet 6.3.5-Viewtilog
10.30.23.8,perseo,MICROSOFT,Windows Server,2022
10.30.23.9,hades,LINUX,Ubuntu 24.04,Viewtinet 6.3.5-Viewtilog
10.30.23.10,jupiter,LINUX,Ubuntu 20.04,Apache HTTP
```

---

### **CSV Import**

You can quickly onboard devices into Viewtinet by importing a CSV file. Follow these steps:

1.  **Log in and open the Inventory page**<br />
    In the Viewtinet web console, click **Inventory** in the left-hand menu.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/N6jH7knUvf9zoOcY34yx.png" align="center"></figure>
    

<br />

2.  **Start the CSV import**<br />
    Click **IMPORT A LIST OF DEVICES AND/OR CREDENTIALS FROM CSV** at the top of the Devices tab.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Cx0SvdM6m7fGvfYKnXcX.png"></figure>
    
    <br />
    
3.  **Select your CSV file**<br />
    In the file chooser dialog, locate and select your CSV (for example, `inventory_example_guide.csv`), then click **Open**.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/D4zbqtfjdvBxl1Om8KwN.png"></figure>
    
    <br />
    
4.  **Preview and map columns**<br />
    The “Select which columns are to be imported” dialog shows a preview of your CSV.
    
    -   Verify the **Separator** (`,` by default) and the **Source name** (your filename).
    -   Click **AUTO-ASSIGN COLUMNS** to map CSV headers to Viewtinet inventory fields (`dev.ip`, `dev.hostname`, etc.).
        
        <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/1oWZI2Uhxc8a68bBR0qs.png"></figure>
        
        <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/nWfwLlJoqY3QbNoDdXMI.png"></figure>
        
        <br />
        
5.  **Import the fields**<br />
    Once all required fields (IP or Hostname) and any additional device attributes are mapped, click **IMPORT FIELDS** to begin provisioning.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/ihRlKdmQf7gqtinVxyuh.png" align="center"></figure>

6.  **Save the imported devices**<br />
    After the import completes, click the **SAVE** button at the bottom right of the Inventory page to finalize adding the devices to your inventory.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/XgoF5nshV58Sdb50dUdO.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/hvJbPy2IMu4KeCFzLrLq.png" align="center"></figure>

<br />

<span align="justify">Upon completion, Viewtinet will display a summary of imported devices and any rows that failed validation. You can now manage and filter your newly onboarded inventory.</span>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/reTQUSzvvS1jpIg7v8GV.png" align="center"></figure>

---

## **Inventory Filtering**

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
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/J9yZF7DSaR7OmXmxACea.png"></figure>
    
    <br />
    
4.  **Choose an Operator**<br />
    Pick an operator to define your match criteria:
    
    -   `==` (equals)
    -   `!=` (not equals)
    -   `Contains` / `Not contains`
    -   `Starts with` / `Ends with`
    -   `Is empty` / `Is not empty`
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/YJguyKOwmLxzeQJQyUHg.png" align="center"></figure>
    
    <br />
    
5.  **Enter a Value and Apply**<br />
    Type the comparison value (e.g., `LINUX`) and click **OK**. The filter expression appears in the main Inventory view.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/dB67Z20w8MeyW7BM6Vn9.png"></figure>
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/qVnFCJbEAFtP9ThWWk6l.png"></figure>
    
    <br />
    
6.  **Save Your Filter**<br />
    To reuse this filter later, click **SAVE FILTER**, give it a name, and click **OK**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/eFHC6n7zUpb9Tz27mKS6.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/vLtyFf0e0GAkDSPqPR4n.png" align="center"></figure>

<span align="justify">With the Filter Builder you can quickly drill down into your inventory, combine complex conditions, and save your most-used queries for one-click access. Next, we’ll show how to create dynamic groups based on these filters.</span>

<br />

---

## **Selecting and Assigning OID Groups**

<span align="justify">An OID Group is a named collection of SNMP Object Identifiers (OIDs) that specifies exactly which metrics and counters to poll from a device. By assigning OID groups, you ensure Viewtinet collects the correct set of SNMP data for each device type.</span>

<br />

### **Step 1: Add the OID Groups Column**

<br />

1.  In the Inventory view, click the **?** help icon, then choose **Add New Column**.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/sdPthHO5Dg0kgR3mAPX2.png"></figure>
    
    <br />
    
2.  In the **System Fields** modal, expand **VSDB** and click the **+** next to **oid\_group\_names**, then click **OK**.<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Z8nyy9z58mAbOekycAzm.png" align="center"></figure>
    
    <br />
    
    <figure align="center" style="width:44%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Y33N4DyecgDc0zPA5I5h.png" width="44%" align="center"></figure>
    
    <br />
    
3.  The new **oid\_group\_names** column now appears in your device list.<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/VZArdNK8ZbIiRV1ErQwZ.png" align="center"></figure>
    
    ⚠️ **Note:** The **oid\_group\_names** column only needs to be added **once**; it will remain available in the inventory view thereafter.
    
    <br />
    

### **Step 2: Filter and Assign OID Group Values**<br />

1.  Filter your data sources\*\*.\*\* Use the inventory filters to narrow down the devices you wish to configure—e.g., filter by operating system `LINUX`—so that OID groups are assigned only to the relevant subset.<br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/dcS8MkP7PhxomoJYCiiG.png"></figure>
    
2.  Enter the OID group name\*\*.\*\* In the oid\_group\_names header input (or per-row cell), type the OID group name—comma-separated if assigning multiple groups (e.g. `net-SNMPAgent,general`)—and press **Enter**. A dropdown will suggest existing group names as you type.<br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/tPKqQ4K0lAUqvLuo4k86.png"></figure>
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/LNtl0YM0YgvSEUias498.png" align="center"></figure>
    
    <br />
    
3.  **Apply to your selection.** After pressing **Enter**, the group name is applied to all filtered (selected) rows or to individual rows as needed.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/LC7E0ZcptPmlxd8z6bcC.png"></figure>
    

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/VYeFNAJTehxVnmjdiXcM.png" align="center"></figure>

<br />

### **Step 3: Save Your Changes**

<br />

Click **SAVE CHANGES** at the bottom right to persist your OID group assignments.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/DCkyap8nQzAZPY5XjIbx.png" align="center"></figure>

A confirmation banner will appear once the inventory is successfully saved.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/b6EsvUPa4hddixDTteBa.png" align="center"></figure>

---

### **Configuring Credentials**

<span align="justify">In Viewtinet, Credentials define how the system authenticates to your devices and external data sources. Credentials are used both for collecting counters &amp; metrics (SNMP &amp; ICMP) and for managing configurations over SSH/Telnet (via Configuration Manager, covered in a later chapter).</span>

<br />
**Supported Protocols**

-   **ICMP**
-   **SNMP v1 / v2c / v3**
-   **SSH**
-   **Telnet**

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

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/1NxpXIbO7NMhXE4xJIhq.png" align="center" data-drop-shadow="disabled"></figure>

### **Step 2: Filter Devices**

Use the filter box or Query Builder to narrow the device list. You can pick a specific subset (for example `dev.sw_version == '2c'` or `dev.vendor == 'LINUX'`), or choose the All devices filter if every data source uses the same SNMP community (or for simple protocols like ICMP).

<br />

### **Step 3: Select Devices**

Once filtered, use the checkboxes in the first column to select all matching devices (or pick individual entries).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/B957jDadVBKuoqvX4pAo.png" align="center"></figure>

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

Viewtinet uses a **plugin framework** to map inventory data into data‐processing pipelines. In this section we’ll install the **Network Monitoring** plugin for all of your data sources.

<br />

> ⚠️ **Disclaimer:** Because we’re applying **all** data sources to the **Network Monitoring** plugin, **no filters** are used in this step. Filters become essential when you want to install **vendor-specific** plugins only on certain devices.

---

<br />

### **Step 1: Open the Plugins Tab**

In the Inventory console, click **PLUGINS**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/2SiOKpo4yqgk0Y5Stzmb.png" align="center"></figure>

### **Step 2: (No Filters) Select “All devices”**

Since we’re installing across every data source, check the **All devices** filter.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/XwzPHTpvcjM6LwxBrGXL.png"><br />

### **Step 3: Pick the Network Monitoring Plugin**

In the **Plugins** panel, expand **network monitoring** and select:

-   **snmp\_device\_config**
-   **snmp\_if\_config**
-   **icmp**<br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/qJQlxOW78mTTJYjCoBL7.png">
    

### <br />

**Step 4: Modify and Install**

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