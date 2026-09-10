---
reusableId: 67
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Operating System Setup'
id: DM2-XF36-ELR-TFC
slug: operating-system-setup
isVisible: true
lastUpdated: '2025-10-14 09:43:46'
---
# **<span align="center">Operating System Profile Setup</span>**

In this step, you will configure the default user profile for the operating system installation.

All Viewtinet modules, containers, and services run under the dedicated `viewtinet` user. Therefore, it is **mandatory** to create this user exactly as specified below. The server's hostname and the user's password are at your discretion.

---

## **Creating the Viewtinet User and Setting Hostname**

During the Ubuntu Server installation, you will encounter the **Profile setup** screen. Complete the fields as follows:

-   **Your name:**<br />
    Enter `viewtinet`.
-   **Your server’s name:**<br />
    Enter your desired hostname. This hostname is how the server will identify itself within your network.
-   **Pick a username:**<br />
    Enter `viewtinet`. _(This username is mandatory.)_
-   **Choose a password:**<br />
    Enter a strong, secure password following your organization's security guidelines.
-   **Confirm your password:**<br />
    Re-enter the password to confirm.

Ensure all fields are correctly filled as shown in the example below:

<br />

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/hFmxz31pTGJmrTg53sRY.png"></figure>

Once the fields are filled, select `[Done]` to proceed with the installation.

---

**Important:**

-   Do not deviate from using `viewtinet` as the system username, as this is required for correct operation of the platform.
-   Ensure that the password you set complies with your organization's password policies.

Proceed to the following chapters once the profile setup is complete.

---

<br />