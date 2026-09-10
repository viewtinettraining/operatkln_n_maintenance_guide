---
reusableId: 116
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: License
id: NFD-NF8N-8A9-479
slug: license
isVisible: true
lastUpdated: '2025-10-15 15:51:35'
---
# **<span align="center">License Enforcement</span>**

<br />

## **1\. Introduction**

Viewtinet’s new license enforcement system ensures that only properly licensed modules and features remain active, and provides clear warnings or restrictions as license terms approach or exceed their limits

<br />

## **2\. License Enforcement Behavior**

1.  **Expiration Check**
    
    -   If a temporal license has expired, Viewtimon, Viewtify QoS, Viewtilog, and other modules become disabled, though you can still log in to Viewtimanager.
    -   Viewtisight is entirely inaccessible until a valid license is loaded.
2.  **Warning for Imminent Expiry**
    
    -   When a temporal license is within 30 days of its expiration date, or a permanent-license support period is within 30 days of ending, Viewtmanager displays a popup warning.
3.  **Module Enable/Disable**
    
    -   If a module is **disabled** in the license file, its tables or features are blocked:
        
        -   **Viewtimon**: queries against `dpi_records` and `voip_records` are denied.
        -   **Viewtify QoS**: `qos_records` queries are denied.
        -   **Viewtimon Sniffer**: access to `pcap_storage_records` is denied.
        -   **Viewtilog**: all tables except `dpi_records`, `voip_records`, `qos_records`, and `self_monitoring*` are denied.
            
            <br />
            

## **3\. License Scenarios**

### **3.1 Compliant License**

All usage is below warning and deny limits. The GUI and all modules function normally, with the license serial number displayed at the top of the License

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/wHQ3P0X0g3FDEb1yXaDL.png" align="center"></figure>

<br />

<br />

### **3.2 Temporal License About to Expire**

Within 30 days of expiry, Viewtmanager shows a yellow warning popup. Functionality remains uninterrupted

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/OsFnEamRXX1XmJWqJWVn.png" align="center"></figure>

<br />

### **3.3 Permanent License Support About to Expire**

Within 30 days of support end, a similar warning is displayed in Viewtmanager. Modules continue working until expiry:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/vbHh9HeVJ5d8OF72bhin.png" align="center"></figure>

<br />

### **3.4 Temporal License Expired**

After the expiration date, all modules except Viewtimanager itself are disabled. Viewtisight is inaccessible and shows a disabled banner :

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/HU8Y2TkrlbLp5wkUCdMW.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/nNjs5PZGIMh1Tr2XbuFL.png" align="center"></figure>

<br />

### **3.5 Permanent License Support Period Expired**

Modules remain functional, but Viewtmanager displays a support-expired message at the top of the License section:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/Uty7zaPj5J2ZW0SfzYth.png" align="center"></figure>

<br />

### **3.6 Module(s) Above Warning Limits**

When usage (GB/day, throughput, or device count) exceeds the warning threshold, Viewtmanager displays a non-blocking alert in the License section to caution you before hitting deny limits:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/7tT9sAysLa1YhvJ2eMmA.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/xxbnLMcqQYIipSRsgWE0.png" align="center"></figure>

<br />

### **3.7 Module(s) Above Deny Limits but Still Compliant**

If usage has reached the deny threshold but not long enough to declare non-compliance, the system shows a warning and logs events in the License history. Functionality remains active until non-compliance is declared:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/EWjbMsUh0A39Goc87TrF.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/MtTVP0ArwxlFYQn15E3V.png" align="center"></figure>

<br />

### **3.8 Module(s) Non‐Compliant**

Once usage exceeds deny limits for seven days (or equivalent rule for throughput buckets), the module is declared non-compliant:

-   All related tables are blocked (only minimal “self\_monitoring” tables remain).
-   An error message appears in Viewtmanager and Viewtisight restricts affected views.
-   You must wait 30 days from the last non-compliant check—or load a new license with expanded limits—to restore functionality:
    
    <br />
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/d5PNMk4xuW02QY0Pe2zo.png" align="center"></figure>

---

<br />