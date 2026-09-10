---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Classification Rules'
id: FG0-TVA-0IC-BQJ
slug: classification-rules
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 15:00:33'
---
# **<span align="center">Classification Rules</span>**

<br />

The **Classification Rules** section is where you define _what_ specific traffic flows you want to manage. These rules are the foundation of any Viewtify QoS policy. You can create rules based on deep packet inspection (DPI) classification or standard network parameters.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_4_img_1.png" align="center"></figure>

<br />

---

## **Types of Rules**

You can classify traffic using a wide variety of parameters. Modern versions of the Viewtify engine support recognizing over **8,100 different applications** natively via DPI. The available classification types include:

-   **Application:** Specific applications recognized by DPI (e.g., YouTube, Netflix, Office365).
-   **Protocol:** Transport layer protocols (TCP, UDP, ICMP).
-   **Port & Port Range:** Specific source/destination ports or ranges.
-   **IP, IP Range & Subnet:** Source or destination IP addresses and subnets.
-   **VLAN:** Virtual LAN tags.
-   **Time:** Time-based rules (useful when combined with other parameters).

<br />

### **Filtering Rules**

As your list of classification rules grows, you can easily find specific entries using the **Filter by type** dropdown at the top of the screen. This allows you to filter the view to only show IPs, Subnets, Ports, Protocols, or VLANs.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_5_img_1.png" align="center"></figure>

<br />

---

## **Creating a Classification Rule**

To create a new classification rule, follow this step-by-step guide:

1.  Click on the **+ ADD NEW** button at the bottom of the list.
2.  Insert a unique and descriptive **Name** for the rule in the first column.
3.  Select the **Type** of parameter you want to use from the dropdown (e.g., Ports, Subnet, Application).
4.  Enter the corresponding **Value** in the third column (e.g., `443` for a port, `192.168.1.0/24` for a subnet). The information requested will adapt based on the type you selected.
5.  Click the **SAVE CHANGES** button (with a checkmark icon) to save the new rule.

To return to the main configuration menu, simply click on the **Back** button.

<br />

---

## **Validations and Warnings**

To prevent configuration mistakes that could impact traffic flow, Viewtify QoS includes built-in validations.

### **Validation Errors**

Every rule is validated before it can be saved. **Errors must be fixed** prior to saving a policy. For example, if you leave a mandatory field blank or try to create a rule with a duplicated name, the system will highlight the fields in red.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_7_img_1.png" align="center"></figure>

<br />

### **Warnings**

Warnings notify you of potential issues, such as entering a value that already exists. Unlike strict errors, warnings serve as a heads-up to double-check your configuration.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_8_img_1.png" align="center"></figure>

<br />

---

## **Searching and Deleting Rules**

-   **Deleting Rules:** Classification rules can be deleted **only if they are not used** in any active or saved policy. This safeguard prevents breaking existing QoS configurations.
-   **Search Tool:** If you need to delete a rule but the system prevents it, use the **Search (magnifying glass icon)** option next to the rule. This feature helps you find the exact policy (Use Case) where the classification rule is currently being used, allowing you to remove it from the policy first.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_9_img_1.png" align="center"></figure>

<br />