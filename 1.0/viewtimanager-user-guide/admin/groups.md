---
reusableId: 108
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Groups
id: JQS-NBVT-IRA-L3E
slug: groups
isVisible: true
lastUpdated: '2025-10-15 15:32:34'
---
# **<span align="center">Groups</span>**

<br />

<span align="justify">While Roles define what actions and views a user can access in Viewtinet, Groups make it easier to manage who gets those roles. Groups are entirely internal to Viewtimanager—they don’t affect the GUI directly, but they let you assign (or change) a role for many users at once.</span>

<br />

-   **Roles** assign permissions (what users see and can do) and integrate with external Identity Providers (e.g. Active Directory).
-   **Groups** bundle users together so you can manage their roles in bulk.

> **Why use Groups?**<br />
> <span align="justify">Imagine you have a team of Log Administrators who need full access to the Viewtilog module, and another set of analysts who should only be able to view dashboards (but not create or delete them). If each user stood alone, you’d have to edit ten user records individually. But if you place all log admins in a “Log-Admins” group and dashboard-only users in a “Report-Viewers” group, you can assign or revoke the appropriate role at the group level—and everyone in that group inherits it instantly.</span>

Groups are optional but highly recommended for large deployments or frequent role changes.

<br />

## **Select Groups page**

1.  In the left-hand menu, click **Admin**.
2.  In the top tabs, select **Groups**.<br />
    

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/4eCAgTWC2KlvkXlyRD9t.png"></figure>

<br />

## **Create a new Group**

1.  Click **\+ ADD NEW** at the bottom of the group list.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/LPqqImCR4ELROBZ1vbxj.png" align="center"></figure>
    

## **Fill in Group Details**

-   **Name**: A unique identifier for your group (e.g. `Log-Analysts`).
-   **Description** (optional): Brief notes on the group's purpose.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/5MlUlUkPy5Dq4tXeTJuI.png" align="center"></figure>
    

<br />

## **Assign Roles to the Group**

1.  Expand the **Group Roles** section.
2.  In the **Available** column, check the box next to each Role you want this group to inherit.
3.  Click the single-arrow **&gt;** button to move them to **Selected**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/3RaQpKMJpHhNvpKsybMp.png" align="center"></figure>

<br />

## **Save Your Changes**

Click **✔ SAVE CHANGES** at the bottom to create the group and apply its Roles to all current (and future) members.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/kLmRaA2L41WM9INyXOmd.png" align="center"></figure>

<br />

<div class="sd-callout" data-callout-type="tip">Tip:<br>When you add or remove a user from a group, they instantly gain or lose every Role assigned to that group—no further edits are needed on their individual user account.</div>

<br />