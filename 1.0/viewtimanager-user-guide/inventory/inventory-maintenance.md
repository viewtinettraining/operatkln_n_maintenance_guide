---
reusableId: 93
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Inventory Maintenance'
id: 9Y5-B4O0-0S1-PP5
slug: inventory-maintenance
isVisible: true
lastUpdated: '2025-10-15 14:51:03'
---
## **<span align="center"><span class="text-large">Inventory Maintenance Functions</span></span>**

<br />

<span align="justify">Beyond provisioning devices and credentials, the Inventory feature offers powerful maintenance capabilities to keep your data clean, organized, and tailored to your needs. In this chapter, you’ll learn how to manage columns, merge or delete records, export datasets, and perform other housekeeping tasks that ensure your inventory remains accurate and actionable.</span>

## **Toggling Visible Columns**

The “Visible columns” picker lets you control which device attributes are shown in the Inventory table. These fields are defined by your provisioning method (CSV import, Autodiscovery or manual entry). This is **not** the place to add new columns—only to enable or disable existing ones.

<br />

1.  **Open the Column Picker<br />
    **Click the dropdown arrow (▾) next to **Visible columns** above the devices table.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/DY2Cg7yu4bKqgoTxWrn5.png" align="center"></figure>
    
    <br />
    
2.  **Enable or Disable Fields<br />
    **In the list that appears, simply check the box beside any column you want to show, or uncheck to hide it. Columns include attributes such as `device`, `mac`, `oid_group_names`, `sw_version`, `sys_object_id`, `system_name`, etc.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/rtVWUP5HO07vwh8CGcYW.png" align="center"></figure>
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/xXeLFpEhNYLTZyWJkxhI.png" align="center"></figure>
    
    <br />
    
3.  **Save Layout**<br />
    Finally, click **Save Changes** to persist your column configuration across sessions.

---

## **Adding Custom Columns**

<br />
You can extend your Inventory schema by creating new custom columns to capture device attributes beyond those provided by CSV, Autodiscovery, or manual provisioning.

1.  **Open the “Add New Column” Dialog**<br />
    In the Inventory view, click **\+ Add New Column** next to the column-picker dropdown.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/nKy2hAosimX1vN0n1gFi.png" align="center"></figure>
    
    <br />
    
2.  **Define Your Column**<br />
    In the modal that appears:
    
    -   **Name**: Enter a unique key for the column (e.g. `example_new_column2`, `rack_label`).
    -   **Copy values from another column** (optional): If you’d like to initialize your new field with data from an existing column, check this box and select the source (e.g. `system_name`).
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/emNG7WEfCgkev80asBxJ.png" align="center"></figure>
    
    <br />
    
3.  **Confirm Addition**<br />
    Click **OK**. The new column will appear at the end of your table and in the “Visible columns” picker:
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/SrtVIIkud1VqINFxJxxZ.png" align="center"></figure>
    
    <br />
    
4.  **Populate or Adjust Values**
    
    -   If you copied values in step 2, your new column will already be prefilled.
    -   Otherwise, click **Apply to all** above the column to set a default, or edit cells individually.
5.  **Save Your Layout**<br />
    Click **Save Changes** to persist the new column and its contents across sessions.

> **Tip:** Custom columns are fully integrated—available for filtering, bulk editing, and CSV export just like built-in fields.

---

## **Merging Duplicate Rows**

<br />

When multiple rows represent the same device, you can merge them:

1.  Select the checkbox next to each duplicate row.
2.  Click **Merge Duplicated Rows** in the toolbar.
3.  Confirm which values to retain for each column.
4.  Click **Merge** to consolidate into a single record.

---

## **Deleting Records**

To remove obsolete entries:

1.  Select one or more rows using their checkboxes.
2.  Click **Delete Selected Rows** (trash icon).
3.  Confirm deletion in the prompt.

---

## **Exporting Your Inventory**

You can export any current view to CSV:

1.  Apply filters and adjust columns as needed.
2.  Click **Export** in the upper-right corner of the devices table.
3.  Download the generated CSV file.

---

## **Finding Plugins & Pipelines for a Specific Device**

Sometimes you need to know exactly which monitoring plugins (and their underlying pipelines) are collecting data from a given device. The Inventory view makes this easy:

1.  **Locate Your Device**<br />
    In **Overview → Devices**, scroll or filter to the target row (e.g. `10.10.10.1` or `10.30.23.45`).<br />
    
2.  **Click the Device-Level Search Icon**<br />
    On the rightmost column of that row, click the 🔍 **“Show plugins using this device”** icon.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/6YglcrKNtQFo78sql1bT.png"></figure>
    
    <br />
    
3.  **See Plugin Assignment Filters**<br />
    You’ll be taken to the **Plugins** tab, where the filter box is prefilled with your device’s IP. Only plugins currently tied to that device will be listed.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/uXz7m93Ue00vaqnUqlNj.png"></figure>
    

---

## **Finding Devices Associated with a Pipeline**

If you need to know which inventory devices are tied to a specific data-collection pipeline, follow these steps:

1.  **Open the Plugins View**<br />
    In the Inventory screen, click the **Plugins** tab.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/FZCZO3yfmANnfZhKN1h8.png" align="center"></figure>
    
    <br />
    
2.  **Expand the Desired Plugin**<br />
    Find the plugin that contains your pipeline (e.g. **network monitoring**) and click the ▶️ arrow to reveal its pipelines.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/oUqdKoqIxhHCDwKF8mHU.png" align="center"></figure>
    
3.  **Search on the Pipeline Row**<br />
    Locate the pipeline you care about (e.g. `snmp_device_config`) and click the 🔍 **“Show devices assigned to this pipeline”** icon on that row.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/qYi87vjl83SdIacdY4aJ.png" align="center"></figure>
    
4.  **View the Filtered Device List**<br />
    A device picker appears, showing only those rows matching the pipeline’s filter (e.g. from the “All devices” or a custom filter like `dev.ip == '10.10.10.1'`). You can scroll through the list or further refine it via the search bar.<br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/TlJWz6vwmnWoy25V77rM.png">
    
    <br />
    
5.  **Inspect or Confirm**
    
    -   Review which IP/Hostnames, OID groups, SNMP versions, etc. are active.
    -   When you’re done, click **OK** to close the device list.

> **Tip:** Use this drill-down anytime you want to audit or troubleshoot exactly which network assets a particular collection pipeline is targeting.

<br />
With these tools, you can maintain a lean, accurate inventory that reflects your network’s true state making downstream monitoring, analytics, and reporting far more reliable.