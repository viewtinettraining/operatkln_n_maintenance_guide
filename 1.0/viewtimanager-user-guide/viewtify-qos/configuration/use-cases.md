---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Use Cases'
id: GJV-9YI-K8L-7S9
slug: use-cases
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 15:00:50'
---
# **<span align="center">Use Cases</span>**

<br />

In Viewtify QoS, every entire policy tree that you build and save is stored as a **Use Case**. This structure allows you to maintain multiple different network policy designs simultaneously without losing your work. A **Policy Tree** is the hierarchical structure where you define the different traffic management rules, linking classification rules to QoS profiles, determining priorities and bandwidth allocations for each traffic type.

<br />

---

## **Creating a Use Case**

To add a new Use Case, follow these steps:

1.  From the Configuration Home, click on the **POLICIES** button.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-use-cases-create-0.png" align="center"></figure>

<br />

2.  Click on the **+ ADD NEW USE CASE** button.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-use-cases-create-1.png" align="center"></figure>

<br />

3.  This will take you to the Use Case configuration section. Here you must enter a descriptive name and configure both the **Download bandwidth** and **Upload bandwidth**. **Note:** This represents the maximum total bandwidth that will be available for this specific Use Case.
4.  Click on **SAVE** to generate and save the change at the policy structure level.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-use-cases-create-2.png" align="center"></figure>

<br />

5.  This action will lead you to the screen where you can start building the policy tree (this process will be explained in detail later).
6.  Once your Use Case and policy tree are ready, you must click on the **APPLY QOS** button. This final step is what actually applies and enforces the Use Case along with all its created policies on the network traffic.

<br />

---

## **Managing Multiple Use Cases**

The platform has the capability to store several Use Cases (each being a complete set of policies), but **only one can be active at a time**. 

To activate a Use Case or switch to a different one, simply follow these steps:
1. Select the desired Use Case from the dropdown menu.
2. Click on the **APPLY QOS** button.

The currently active Use Case will be marked with the word **(active)** in the dropdown.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-dropdown.png" align="center"></figure>

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-apply.png" align="center"></figure>

<br />

---

## **Exporting and Importing**

Network deployments often span multiple sites or require migrating configurations between different Viewtimanager instances. This feature is also highly useful for creating **backups** of your policies, allowing you to quickly recover your entire policy set in the event of a disaster or a corrupted use case.

### **How to Export a Use Case**
1. Click on the **parent node** (the very top node) of the entire policy tree.
2. From the context menu, click on **Export Use Case**.
3. The configuration will be saved to your local disk as a JSON file.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-export.png" align="center"></figure>

<br />

### **How to Import a Use Case**
1. Click on the **IMPORT USE CASE** button located at the top right of the screen.
2. Select the previously exported backup file from your local disk to restore or replicate the policy tree.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-import.png" align="center"></figure>

<br />

---

## **History View**

To track the historical changes made to your Use Cases and policies, you can utilize the **History View** functionality.

- Click on the **SWITCH TO HISTORY VIEW** button to access this feature.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-history-1.png" align="center"></figure>
  <br />

- Once activated, the main dropdown will present a chronological list of changes and applied use cases.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-history-2.png" align="center"></figure>
  <br />

- To return to the standard active and draft use cases list, simply click on the **SWITCH TO USE CASES VIEW** button.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-history-3.png" align="center"></figure>

<br />

---

## **Search within a Use Case**

As your policy trees grow more complex, you can easily locate specific elements using the built-in search tool. This feature allows you to find an IP, a classification rule, or a QoS profile.

To use the search tool:
1. Type your search criteria in the **search box** located above the policy tree area.
2. The system will automatically highlight the matching node and trace the path from the parent node down to the result.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-search.png" align="center"></figure>

<br />

---

## **Detailed View**

To inspect the deeper configurations of your Use Case, you can enable the **Detailed View** functionality. 

- By clicking the **Detailed View** checkbox located above the tree, the visual representation will expand.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-detailed-1.png" align="center"></figure>
  <br />

- The expanded view displays detailed information directly on the canvas, including specific parameters for nodes, connectors, and policies (such as exact max up/down rates, configured IP subsets, and component IDs).
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-detailed-2.png" align="center"></figure>

<br />