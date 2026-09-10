---
reusableId: 112
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Prerequisites
id: TC5-RB9Y-U44-GEU
slug: prerequisites
isVisible: true
lastUpdated: '2025-10-15 15:41:10'
---
# **<span align="center">Prerequisites</span>**

<span align="justify">Integrating Viewtimanager with LDAP Server requires specific configurations to ensure seamless authentication and user management. This chapter outlines the necessary prerequisites, including user permissions, network requirements, and configuration details.</span>

<br />

## **1\. LDAP User Account Requirements**

To connect Viewtimanager with LDAP Server, a dedicated user account must be created in the domain. This account should have the following properties:

-   **Username:** A unique service account (e.g., `viewtinet_user`).
-   **Permissions:** Read access to the LDAP tree structure to retrieve user and group information.
-   **Non-Expiring Password:** It is recommended to configure the account with a non-expiring password to prevent authentication failures.
    
    <br />
    

## **2\. Network and Firewall Requirements**

The following ports must be open for proper communication between Viewtimanager and the LDAP server:

-   **TCP 389:** Standard LDAP port for directory queries (non-secure mode).
-   **TCP 636:** Standard LDAPS port for directory queries (secure mode).
    
    <br />
    

## **3\. LDAP Server Information**

Gather the following details before starting the integration:

-   **Domain Name:** (e.g., `viewtinet.local`)
-   **LDAP Server IP Address:** (e.g., `10.30.23.8 or dc01.viewtinet.local`)
-   **Base DN (Distinguished Name):** (e.g., `DC=viewtinet,DC=local`)
-   **Admin Access DN (Service Account DN):** (e.g., `CN=viewtinet_user,DC=viewtinet,DC=local`)
    
    <br />
    

## **4\. Time Synchronization**

Both Viewtimanager and the LDAP server must have synchronized time settings to avoid authentication failures due to time drift.

<br />

## **5\. Role by Default**

Unlike Active Directory integration, this version does not support mapping AD groups to specific Viewtinet roles. LDAP users will be auto-provisioned with a single default role on first login. You may use one of the pre-defined roles, or—if a specific role is required create it following the steps in the Roles section of the Viewtimanager User Guide.

<br />

### **Next Steps**

<span align="justify">Once these prerequisites are met, the next chapter will guide you through the step-by-step process of configuring Viewtimanager to integrate with LDAP Server, including role assignment to modify the graphical user interface behavior based on user permissions.</span>

<br />