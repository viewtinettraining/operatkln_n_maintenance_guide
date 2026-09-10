---
reusableId: 111
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'MFA Configuration'
id: MGK-93YX-ZIC-MJJ
slug: mfa-configuration
isVisible: true
lastUpdated: '2025-10-15 15:36:10'
---
# **<span align="center">Multi-Factor Authentication (MFA)</span>**

Viewtinet’s native MFA adds an extra security layer by requiring users to enter a one-time code sent via email after their primary login.

---

## **Prerequisites**

1.  **SMTP Integration**<br />
    Make sure outbound email is configured under **Home → Configuration → Email Notifications**.<br />
    This enables sending MFA codes via your SMTP server.

---

## **Configure MFA in the Admin UI**

1.  **Open Admin → Auth**
    
    <br />
    
    **MFA Config**
    
    -   **Use script for MFA mailing**
        
        -   _Optional_: check to use a custom shell script instead of the built-in mailer.
    -   **Sender Email**
        
        -   Change from the default `support@viewtinet.com` to your real mailbox address.
            
            -   Example: `mfa@yourdomain.com`
                
                <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/XZsC2aogPrsFViO1y4MW.png" align="center"></figure>
                
                <br />
                
    -   **Sender Name**
        
        -   Friendly name that appears in the “From:” field of MFA emails, e.g. `Security Team`.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/6hhn0mElR79cvcetTucI.png"></figure>
    
    <br />
    
2.  **Save Changes**<br />
    Click **Save Changes** at the bottom of the page.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/Xv9eLSzBHhelDomkUqL2.png" align="center"></figure>
    
    <br />
    

---

## **How It Works**

-   When users with MFA enabled log in, they receive an email containing a one-time code.
-   They must enter that code on the second screen to complete authentication.

<br />