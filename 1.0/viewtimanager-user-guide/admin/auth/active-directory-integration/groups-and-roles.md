---
reusableId: 61
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Groups & Roles'
id: 0QA-TLZ4-4U4-TO8
slug: groups-and-roles
isVisible: true
lastUpdated: '2025-10-15 15:39:00'
---
# **<span align="center">AD Groups &amp; Viewtinet Roles</span>**

<br />

<span align="justify">This chapter will guide you through the process of creating and mapping roles in Viewtimanager, which will be linked to groups in your Active Directory. While the setup and preparation of Active Directory are outside the scope of this guide, it is important to note that the appropriate groups must already exist within your directory. By configuring roles in Viewtimanager and mapping them to these pre-existing groups, you ensure that users are assigned the correct permissions and access within the Viewtimanager interface, aligned with their organizational roles.</span>

For the purpose of this guide, an Organizational Unit (OU) named **"Viewtinet\_Users"** has been created in Active Directory. Within this OU, three groups have been defined to manage user access in Viewtimanager:

-   **Admins\_Viewtinet**: This group includes administrator users with full access to both Viewtimanager and Viewtisight.
-   **ReadOnly\_Viewtinet**: This group consists of users with read-only access to Viewtisight, without permissions to create dashboards.
-   **Viewtisight\_Viewtinet**: This group contains users with administrative access to Viewtisight but no access to Viewtimanager.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/xEEtWoUK537P4eDPCSbj.png" align="center"></figure>

<br />

## **ROLES**

<span align="justify">Roles define the permissions and access levels that users have within the platform. They determine what actions a user can perform, which modules they can access, and how they can interact with different features. Roles can be customized to align with an organization’s security policies, ensuring that users only have access to the functionalities relevant to their responsibilities. Additionally, roles can be mapped to Active Directory groups, allowing for seamless integration with existing user management structures.</span>

<br />

<span align="justify">As the first step, you must be logged in with the admin user or a user with administrative permissions in </span> Viewtimanager at `http://x.x.x.x:5000` (insecure mode) or `https://x.x.x.x:50001` (secure mode), where `x.x.x.x` is the management IP address of Viewtimanager.

<br />

To create a role, click on the **Admin** menu, navigate to the **Details** section, and enter the required information for the role you want to create. The role name must match the Active Directory group that you want to map it to.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/neD5NA2oab2gjjq8pGMW.png"></figure>

<div class="sd-callout" data-callout-type="info">There are two predefined permissions: VS_FULL_ACCESS and VM_FULL_ACCESS, which grant full access to all elements in the GUI. All other elements can be selected to create roles with customized access to the GUI.</div>

The 'Role Permissions' section allows you to assign or filter the visibility of elements in the GUI.

Permissions are structured as: **_Module\_Menu\_Tab\_Permission_**, where:

-   Module
    
    -   VM = Viewtimanager
    -   VS = Viewtisight
-   Menu: The Viewtimanager or Viewtisight menu where the permission will be applied
-   Tab: This applies exclusively to Viewtimanager and refers to sections within the menus.
-   Permission: Define the permission to be applied. It will only appear when access to the tab is to be denied, indicated by the word 'FILTERED'. If the word 'FILTERED' is not present, access is allowed.

For this example, we will assign the VS\_FULL\_ACCESS and VM\_FULL\_ACCESS permissions to the role, as it is being mapped to the Admins\_Viewtinet group

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/aeLT3nKo3m8nJDcaYJRr.png" align="center"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/P3b4vMMTPpkTkFIgr8y5.png"></figure>

Finally, we will save the changes by clicking the 'SAVE' button

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/KOFw115qHO2WRtmUUDOS.png" align="center"></figure>

For each group defined in Active Directory, it will be necessary to create a role following the indicated process and assigning the required permissions for each case

<br />

For demonstration purposes, the three roles that map the Active Directory groups have been created as shown below:

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/miwrxO52RXzDr4JqNJw0.png" align="center"></figure>

The 'ReadOnly\_Viewtinet' role has the VS\_READ\_ONLY permission assigned, which grants access only to the Viewtisight module without the ability to create dashboards

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/gtU8Kj35k8qmxCqp1a2Q.png" align="center"></figure>

<br />

Meanwhile, the 'Viewtisight\_Viewtinet' role has the VS\_FULL\_ACCESS permission, which grants access only to the Viewtisight module with permission to create dashboards

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/nDag22GB9Wd85nutrc0V.png" align="center"></figure>

<br />