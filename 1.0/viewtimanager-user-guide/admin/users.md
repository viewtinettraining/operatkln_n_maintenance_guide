---
reusableId: 107
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Users
id: P4I-KSRN-3QJ-RPV
slug: users
isVisible: true
lastUpdated: '2025-10-15 15:33:55'
---
# **<span align="center">User Accounts</span>**

<span align="justify">Viewtimanager’s Users page lets you create, manage, and audit local user accounts—whether they’re administrators, Viewtisight analysts, or Viewtilog operators. Follow the steps below to add a new user and configure their settings.</span>

<br />

## **1\. Navigate to the Users Page**

1.  In the left-hand sidebar, click **Admin**.
2.  In the top tabs, select **Users**.
3.  Click **\+ ADD NEW** at the bottom of the user list.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/uENnMqUEY27o9Qdbey8t.png" align="center"></figure>
    

## **2\. Enter Basic User Details**

Fill out the **User Details** form:

<table><tbody><tr><th><p>Field</p></th><th><p>Description</p></th></tr><tr><td><p><strong>Username</strong></p></td><td><p>Unique login name (e.g. <code>jdoe</code>, <code>analyst1</code>).</p></td></tr><tr><td><p><strong>Password</strong></p></td><td><p>Must meet the secure-password policy (see below).</p></td></tr><tr><td><p><strong>Repeat Password</strong></p></td><td><p>Must match the Password exactly.</p></td></tr><tr><td><p><strong>Email</strong></p></td><td><p>User’s email address (required for MFA codes).</p></td></tr><tr><td><p><strong>Tenant</strong></p></td><td><p>Assign a Tenant if using Multi-Tenant mode (see <a href="#tenants" target="_self">Tenants</a>). Otherwise select your default tenant (e.g. <code>Viewtinet</code>).</p></td></tr><tr><td><p><strong>Name/Last Name</strong></p></td><td><p>Optional: full name fields for reference.</p></td></tr></tbody></table>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/UEPNPtnqewIEN0PKcGew.png"></figure>

### **Password Policy:**

-   Minimum **12** characters
-   At least **1 digit** (`0`–`9`)
-   At least **1 uppercase** letter (`A`–`Z`)
-   At least **1 special** character (`! " @ # $ % ^ & * ( )`)

---

## **3\. Configure Account Flags**

Below the main fields are several checkboxes that control login behavior:

<table><tbody><tr><th><p>Checkbox</p></th><th><p>Effect</p></th></tr><tr><td><p><strong>Two Factor Authentication</strong></p></td><td><p>Sends a one-time code via email on each login. Requires a valid Email and Tenant assignment.</p></td></tr><tr><td><p><strong>Password changed</strong></p></td><td><p><em>Uncheck</em> to force the user to change their password on first login. <em>Check</em> to disable that prompt.</p></td></tr><tr><td><p><strong>Logged in</strong></p></td><td><p>Indicates if the user is currently logged in. <em>Uncheck</em> to immediately log them out.</p></td></tr><tr><td><p><strong>Session Never Expires</strong></p></td><td><p><em>Check</em> to grant this user an immortal session (no automatic timeout).</p></td></tr></tbody></table>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/Jto9BxEaHjIgf4eJ6qih.png"></figure>

<br />

## **4\. Assign User Groups _(Optional)_**

Groups are an organizational convenience—you can assign users to a group so that later you can bulk-manage their roles instead of editing users one-by-one. This step is **optional**.

1.  Expand the **User Groups** section.
2.  Select one or more groups under **Available**.
3.  Click **&gt;** to move them to **Selected**.

## <br />
**5\. Assign User Roles _(Required)_**

Roles define what the user actually **sees** and **can do** in the GUI. Every user **must** have at least one role.

1.  Expand the **User Roles** section.
2.  Select the desired role(s) under **Available**.
3.  Click **&gt;** to move them to **Selected**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/WY8FBcwivBSRdjB2Yg7X.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/1lYcZMkWM1ce2BzRPLSf.png" align="center"></figure>

## **6\. Save the New User**

After configuring details, flags, groups, and roles, click **✔ SAVE CHANGES** at the bottom of the form. The new user will now appear in the list.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/SjJ6uLhOXU1DxhTKJrP0.png" align="center"></figure>

**Tips:**

-   Groups are optional—but they simplify bulk role changes: change a group’s roles once, and all its members inherit those changes instantly.
-   Roles are mandatory: without a role, a user cannot log in or view any dashboards.
-   Use the Logged in flag to immediately terminate a user’s active session (e.g., after a suspected credential leak).
-   Limit the use of Session Never Expires to service or machine accounts only.<br />
    

**Note:** When Viewtinet is integrated with Active Directory (AD) or LDAP, users can be **auto-provisioned**, meaning accounts are created automatically upon first login without manual entry here.

<br />