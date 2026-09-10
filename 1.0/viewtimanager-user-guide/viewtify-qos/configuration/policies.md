---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'QoS Policies'
id: ZXW-9YD-UAF-XIM
slug: policies
isVisible: true
isSearchable: true
lastUpdated: '2026-05-27 16:45:17'
---
# **<span align="center">QoS Policies</span>**

<br />

The **Policies** section is where the magic happens. It is the canvas where you link your Classification Rules with your QoS Profiles to build the final logic that the Viewtify engine will execute.

<br />

## **Visual Hierarchy Tree**

Viewtify QoS represents your network policies as a visual, intuitive, multi-level hierarchy tree. Traffic flows from the root of the tree down through the branches, being evaluated at each node until it finds a match.

### Detailed View

By checking the **Detailed View** box at the top, the nodes on the tree expand to show you the exact IP ranges, rules, and bandwidth limits configured at every single step, allowing you to see all policy details at a glance.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_15_img_1.png" align="center"></figure>

<br />

---

## **Adding and Editing Policies**

Policies are created within a tree structure where the parent node is the Use Case itself. From there, it branches out into child and sibling nodes (at the same level). The application is fully capable of capturing logical errors during the creation of these policies.

### **How to Create a Policy**

1.  **Locate the target node:** Find the node (e.g., the Use Case root or an existing policy) over which you want to create the new policy.
2.  **Left-click on the node:** This action will open a contextual menu.<br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-create-1.png" align="center"></figure>
    
    <br />
    
3.  **Select "Add Child Policy":** From the opened menu, click on this option.<br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-create-2.png" align="center"></figure>
    
    <br />
    
4.  **Configure Classification Rules:** A new screen will open to configure the policy. In the first section, you configure the classification rules.
    
    -   You can define rules by IP, IP Ranges, Subnets, Ports, Protocols, etc. These can be applied as either connection initiators or connection destinations.
    -   Additionally, you must select the **Classification Type**:
        
        -   **Application:** Traffic is classified based on the individual rules configured for a specifically selected application.<br />
            
            <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-create-3.png" align="center"></figure>
            
            <br />
            
        -   **Application Group:** In this case, traffic will be classified for the entire selected group of applications.<br />
            
            <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-create-4.png" align="center"></figure>
            
5.  **Add Multiple Rules and Description:** You can add multiple classification rules to the same policy by clicking the **\+ ADD NEW RULE** button, provided that the application type (Application or Application Group) remains the same for all rules within that node. Additionally, you can add a custom description in the **Connector description** field to better identify the policy's purpose.<br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-create-5.png" align="center"></figure>
    
6.  **Select a Profile and Configure its Schedule:** Once the classification rules are set, the next step is to choose the profile (the action to take when the rules are met) in the **Profiles** section below.
    
    -   **Default Profile:** By default, a profile is assigned with the "default" schedule, meaning it applies 24/7, regardless of the time and day. You can change this profile by selecting the desired one from the dropdown menu.<br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-profile-1.png" align="center"></figure>
        
        <br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-profile-2.png" align="center"></figure>
        
        <br />
        
    -   **Adding a Scheduled Profile:** If you want to apply a different profile (or the same one) but restricted to a specific schedule, click the **\+ ADD NEW PROFILE** button.
    -   **Modifying the Schedule:** After adding a new profile entry, click the **pencil icon** next to it to edit its time range.<br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-profile-3.png" align="center"></figure>
        
        <br />
        
    -   You will then be prompted to configure the exact **Start Time** and **End Time** for when this specific profile should be active.<br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-profile-4.png" align="center"></figure>
        
        <br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-profile-5.png" align="center"></figure>
        

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-example-1.png" align="center"></figure>

### **Policy Creation Example**

Let's look at a practical example of a completed policy configuration based on the steps above.

In the following image, we have created a policy that:

1.  **Classifies traffic:** It specifically targets connections originating from **Range Test 1** (IPs `10.30.24.141` to `10.30.24.146`) when they connect to the **facebook** application.
2.  **Applies a default profile:** A standard profile (`Max_Rate_10Mbps`) limits their bandwidth to **10 Mbps** by default (24/7).
3.  **Applies a scheduled profile:** However, we have added a second profile entry (`Max_Rate_50Mbps`) that grants them a higher bandwidth limit of **50 Mbps**, but strictly during the off-hours schedule from **06:00 PM to 08:00 AM**.

---

## **Policy Validations**

Because policies are evaluated sequentially, their structural order matters heavily. Viewtify QoS includes strict validations to prevent logical errors.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_23_img_1.png" align="center"></figure>

<br />

-   **Error Highlighting:** If changes in profiles create issues (like assigning a profile that no longer exists, or allocating more Min Rate bandwidth than the parent node has available), a validation error will prevent saving, and the affected node will be highlighted in red.
-   **Masked Rules Warning:** The system will warn you if a highly specific classification rule is placed _below_ a very generic one (e.g., placing an IP rule below an "Any IP" rule), meaning the specific rule would never be reached.
-   **App-ID Positioning:** Policies based exclusively on Application ID (DPI signatures) must be placed at the rightmost position before the "Others" node.

<br />