---
reusableId: 109
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Roles
id: W27-FT60-N0W-47N
slug: roles
isVisible: true
lastUpdated: '2025-10-15 15:30:41'
---
# **<span align="center">Roles</span>**

The **Roles** feature lets you define custom permission sets that control what actions users and groups can perform within the Viewtinet platform. Once a role is created, you can assign it to individual users or to user groups, tailoring access to system functions and data.

<br />

## **Accessing the Roles Page**

1.  In the left-hand menu, click **Admin**.
2.  Select the **Roles** tab.
3.  Click **Add New** to create a new role.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/16nOqMXyycj4FF5iFmKc.png" align="center"></figure>

<br />

## **Role Details**

In the **Role Details** panel, specify:

<table><tbody><tr><th><p>Field</p></th><th><p>Description</p></th></tr><tr><td><p><strong>Name</strong></p></td><td><p>A unique identifier for the role (e.g., <code>Network Admin</code>).</p></td></tr><tr><td><p><strong>Description</strong></p></td><td><p>A brief summary of the role’s purpose or typical use case.</p></td></tr><tr><td><p><strong>Created at</strong></p></td><td><p>Timestamp when the role was created (read-only).</p></td></tr><tr><td><p><strong>Updated at</strong></p></td><td><p>Timestamp of the most recent modification (read-only).</p></td></tr></tbody></table>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/BdwbLC0d8KYTorImhfu7.png"></figure>

<br />

## **Role Permissions**

Use the dual-list interface to grant or revoke granular permissions. Select from the left (“Available”) and move into the right (“Selected”).

<table><tbody><tr><th><p>Permission</p></th><th><p>Description</p></th></tr><tr><td><p>VM_ADMIN_AUTH_FILTERED</p></td><td><p>Removes <strong>Auth</strong> tab from Admin area</p></td></tr><tr><td><p>VM_ADMIN_AUTH_INTEGRATIONS_FILTERED</p></td><td><p>Filters to allow only the <strong>Integrations</strong> section in Auth tab</p></td></tr><tr><td><p>VM_ADMIN_AUTH_ONLY</p></td><td><p>Removes all Admin tabs except <strong>Auth</strong></p></td></tr><tr><td><p>VM_ADMIN_GROUPS_FILTERED</p></td><td><p>Removes <strong>Groups</strong> tab from Admin area</p></td></tr><tr><td><p>VM_ADMIN_MODULE</p></td><td><p>Access to Viewtimanager <strong>Admin</strong> module</p></td></tr><tr><td><p>VM_ADMIN_ROLES_FILTERED</p></td><td><p>Removes <strong>Roles</strong> tab from Admin area</p></td></tr><tr><td><p>VM_ADMIN_TENANTS_FILTERED</p></td><td><p>Removes <strong>Tenants</strong> tab from Admin area</p></td></tr><tr><td><p>VM_ADMIN_USERS_FILTERED</p></td><td><p>Removes <strong>Users</strong> tab from Admin area</p></td></tr><tr><td><p>VM_BACKEND_ACCESS</p></td><td><p>Access to <strong>Backend Access</strong> module</p></td></tr><tr><td><p>VM_CONFIGURATION_MANAGER_MODULE</p></td><td><p>Access to Configuration Manager module</p></td></tr><tr><td><p>VM_DATA_SOURCES_MODULE</p></td><td><p>Access to <strong>Viewtilog</strong> / Data Sources module</p></td></tr><tr><td><p>VM_DEVEL_ACCESS</p></td><td><p>Access to all Viewtimanager, including R&amp;D areas</p></td></tr><tr><td><p>VS_DEVEL_ACCESS</p></td><td><p>Access to all Viewtisight, including advanced features</p></td></tr><tr><td><p>VM_FULL_ACCESS</p></td><td><p>Full access to Viewtimanager (excl. R&amp;D)</p></td></tr><tr><td><p>VS_FULL_ACCESS</p></td><td><p>Full access to Viewtisight</p></td></tr><tr><td><p>VM_HOME_MODULE</p></td><td><p>Access to Viewtimanager <strong>Home</strong></p></td></tr><tr><td><p>VM_INVENTORY_MODULE</p></td><td><p>Access to Viewtimanager <strong>Inventory</strong> module</p></td></tr><tr><td><p>VM_PLUGINS_MODULE</p></td><td><p>Access to <strong>V.S. Data Broker</strong></p></td></tr><tr><td><p>VM_QOS_MODULE</p></td><td><p>Access to Viewtify QoS module</p></td></tr><tr><td><p>VS_READ_ONLY</p></td><td><p>Read-only access to all Viewtisight</p></td></tr><tr><td><p>VS_READ_ONLY_ALARMS_NO_EVENTS</p></td><td><p>Read-only Viewtisight, but no alarms events</p></td></tr><tr><td><p>VM_VIEWTIFYOPT_MODULE</p></td><td><p>Access to ViewtifyOpt module</p></td></tr><tr><td><p>VM_VIEWTIMON_INSPECTORS</p></td><td><p>Allows modifying inspectors in the Viewtimon tab</p></td></tr><tr><td><p>VM_VIEWTIMON_MODULE</p></td><td><p>Access to Viewtimon module</p></td></tr><tr><td><p>VM_VIEWTISIGHT_MODULE</p></td><td><p>Access to Viewtisight module</p></td></tr><tr><td><p>VS_NO_CONTROL_CENTER</p></td><td><p>Block access to Control Center (Alarms &amp; Notifications)</p></td></tr><tr><td><p>VM_NO_QOS_CONFIGURATION</p></td><td><p>Disable QoS configuration view</p></td></tr><tr><td><p>VS_NO_SCHEDULER</p></td><td><p>Deny access to Scheduler</p></td></tr></tbody></table>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/IiaX45FmMuHcHH0JgqkO.png" align="center"></figure>

<br />

## **Role Sets (Data Access)**

In **Role Sets**, determine which database tables (“sets”) this role can query. Use the dual-list to move items from **Allowed Sets** to **Forbidden Sets**.

> **Customization Note:** Any sets placed in **Forbidden Sets** cannot be queried by this role, effectively preventing access to those underlying tables or metrics.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/L1mIRhGNajdFQj8D7DJu.png"></figure>

<br />

## **Role Groups**

The **Role Groups** panel lists user groups already associated with this role. You **cannot** modify group assignments here—use **Admin → Groups** to add or remove this role from any group.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/gZFqOWNOMOunTeyzibRH.png" align="center"></figure>

<br />

## **Role Users**

Similarly, the **Role Users** panel shows individual users who have this role. To change user-role associations, navigate to **Admin → Users**.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/BU1hXhfGc2RO1AlvZiia.png" align="center"></figure>

<br />

**Remember:** After updating any section (Details, Permissions, Sets), click **Save Changes** at the bottom of the page to apply your configuration.

<br />