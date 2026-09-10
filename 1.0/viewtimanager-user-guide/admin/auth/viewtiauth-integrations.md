---
reusableId: 114
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtiauth Integrations'
id: ZIC-1AVN-68A-KLJ
slug: viewtiauth-integrations
isVisible: true
lastUpdated: '2025-10-15 15:37:12'
---
# **<span align="center">Viewtiauth Integrations</span>**

<br />

The Viewtiauth Integrations section defines how Viewtinet authenticates users by specifying one or more authentication backends, their precedence, and the default role assigned on successful login. Viewtiauth processes entries in ascending order (`1` = highest precedence). If an entry is marked Inactive, or authentication fails against that backend, it will fall back to the next active entry.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/D0gtafaAW98qdp3xdHbr.png" align="center"></figure>

<br />

## **Configuration Fields**

<table><tbody><tr><th><p>Field</p></th><th><p>Description</p></th></tr><tr><td><p><strong>Active</strong></p></td><td><p>Enable (☑) or disable (☐) this authentication backend. Inactive entries are skipped.</p></td></tr><tr><td><p><strong>Order</strong></p></td><td><p>Precedence of this backend (integer). Lower numbers are tried first. For example, <code>1</code> is highest priority.</p></td></tr><tr><td><p><strong>Type</strong></p></td><td><p>Authentication method:</p></td></tr></tbody></table>

-   `ad` (Active Directory)
-   `local` (built-in Viewtinet database)
-   `ldap` (external LDAP server)
-   `saml2` (SAML 2.0 IdP) | | **Default Role**| Role automatically assigned to users authenticated via this backend. Select any role defined in **Admin ➔ Roles**. |

<br />

## **Authentication Flow**

1.  Viewtiauth reads all configured entries sorted by **Order** ascending.
2.  For each entry in sequence:
    
    -   If **Active** is unchecked, skip to the next.
    -   Otherwise, attempt authentication using the specified **Type**.
    -   On success, assign the **Default Role** and grant access.
    -   On failure, move to the next active entry.
3.  If all active entries fail, authentication is denied.

> **Example:**
> 
> -   Entry `Order = 1`, **Active** = ☐ (inactive)
> -   Entry `Order = 2`, **Active** = ☑, **Type** = `local`
> -   Entry `Order = 3`, **Active** = ☑, **Type** = `ldap`
> -   Entry `Order = 4`, **Active** = ☐ (inactive)
> 
> Viewtiauth will first try the **local** database (order 2). If the user isn’t found or the password is incorrect, it will then try the LDAP server (order 3).

<br />

## **Saving Your Changes**

1.  After adjusting **Active**, **Order**, **Type**, or **Default Role**, click **Save Changes** at the bottom of the page.
2.  A confirmation message will appear once the new authentication sequence is applied.

> **Note:** Changes here affect how **all** users authenticate. Be cautious when disabling or reordering entries to avoid inadvertently locking out administrative access.

<br />