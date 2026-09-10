---
reusableId: 60
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: ' Prerequisites'
id: CHL-R7JE-YJF-9EG
slug: prerequisites
isVisible: true
lastUpdated: '2025-10-15 15:38:04'
---
# **<span align="center">Prerequisites</span>**

<span align="justify">Integrating Viewtimanager with Active Directory requires specific configurations to ensure seamless authentication and user management. This chapter outlines the necessary prerequisites, including user permissions, network requirements, and configuration details.</span>

<br />

## **1\. Active Directory User Account Requirements**

To connect Viewtimanager with Active Directory, a dedicated user account must be created in the domain. This account should have the following properties:

-   **Username:** A unique service account (e.g., `viewtinet_user`).
-   **Permissions:** Read access to the Active Directory structure to retrieve user and group information.
-   **Domain Scope:** Ensure the account has access to the necessary Organizational Units (OUs) where the users are stored.
-   **Non-Expiring Password:** It is recommended to configure the account with a non-expiring password to prevent authentication failures.

## **2\. Network and Firewall Requirements**

The following ports must be open for proper communication between Viewtimanager and the Active Directory server:

-   **TCP 389:** Standard LDAP port for directory queries (non-secure mode).
-   **TCP 636:** Standard LDAPS port for directory queries (secure mode).

## **3\. Active Directory Structure Considerations**

-   Ensure that the required users and groups are located in a known Organizational Unit (OU) or group for easier management.
-   If Role-Based Access Control (RBAC) is being implemented, predefine the security groups that will map to different Viewtimanager roles.

## **4\. Domain Controller Information**

Gather the following details before starting the integration:

-   **Domain Name:** (e.g., `viewtinet.local`)
-   **Domain Controller IP or Hostname:** (e.g., `10.30.23.8 or dc01.viewtinet.local`)
-   **Base DN (Distinguished Name):** (e.g., `DC=viewtinet,DC=local`)
-   **Bind DN (Service Account DN):** (e.g., `CN=viewtinet_user,DC=viewtinet,DC=local`)

<div class="sd-callout" data-callout-type="info"><span align="justify">The structure of the service user, including its groups and Organizational Units (OUs), presented in this manual is for informational purposes only and does not represent a mandatory configuration. Each company should maintain its users, groups, and OUs according to its own policies and requirements. However, it is mandatory that the service user has read permissions on the Active Directory tree, as this is necessary to perform the mapping between users and groups within the platform.</span></div>

## **5\. Time Synchronization**

Both Viewtimanager and the Active Directory server must have synchronized time settings to avoid authentication failures due to time drift.

<br />

### **Next Steps**

Once these prerequisites are met, the next chapter will guide you through the step-by-step process of configuring Viewtimanager to integrate with Active Directory, including role assignment to modify the graphical user interface behavior based on user permissions.

<br />