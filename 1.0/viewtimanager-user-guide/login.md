---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Login
id: HLG-ZK7U-1XT-GW7
slug: login
isVisible: true
isSearchable: true
lastUpdated: '2026-09-10 19:54:19'
---
# **<span align="center">Accessing the Viewtinet Platform</span>**

<br />
<span align="justify">Access to the Viewtinet platform is handled through the Viewtiauth module, which provides centralized authentication for all components. Users must authenticate via a login page before being allowed to access Viewtimanager, Viewtisight, or other system modules.</span>

<br />

### **🌐 Access URLs**

The Viewtiauth module listens on two different ports, depending on the security mode used:

<table><tbody><tr><th><p>Protocol</p></th><th><p>URL Format</p></th><th><p>Description</p></th></tr><tr><td><p>HTTP</p></td><td><p><code>http://&lt;platform-ip&gt;:4200</code></p></td><td><p>Insecure connection (not recommended for production)</p></td></tr><tr><td><p>HTTPS</p></td><td><p><code>https://&lt;platform-ip&gt;:4201</code></p></td><td><p>Secure connection with encryption (recommended)</p></td></tr></tbody></table>

> ⚠️ **Important:**<br />
> Although both HTTP and HTTPS are supported by default, it is strongly recommended to access the platform using **HTTPS (port 4201)**. This ensures that credentials and session data are encrypted during transmission.<br />
> The platform may display a browser warning if **self-signed certificates** are used. To install trusted certificates, please contact the **Viewtinet Helpdesk**.

---

### 🔑 Login Form

Once connected to the login URL, the user will be presented with a login form requiring:

-   **Username**
-   **Password**
-   **Language selection** (bottom dropdown)

Click the **Login** button to submit your credentials for validation.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/VCW02tM70cpSzc0AXJl3.png" align="center"></figure>

---

### 🔄 Authentication Flow

1.  The credentials are validated by the **Viewtiauth** module.
2.  Upon successful login, the user is redirected to the **App Selector** screen.

---

### 🧭 App Selector

After login, the App Selector will display the available modules the user has permission to access:

-   📊 **Viewtisight** – Visualization and dashboards.
-   ⚙️ **Viewtimanager** – System and module administration.

Click on the desired module to enter its interface.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/u8RnjfTOSw9cb8OXCY3M.png" align="center"></figure>

<br />

> 🔐 **Note**: Access rights are managed within the Viewtinet platform. If a user does not have permission to access a module, it may not appear in the selector.

---

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/EH3vMbAvcD9s2bNsJD5n.png" align="center"></figure>

<br />

### **🔁 Direct Access to Modules**

It is also possible to access the modules directly via their dedicated ports:

<table><tbody><tr><th><p>Module</p></th><th><p>Protocol</p></th><th><p>URL Format</p></th></tr><tr><td><p>Viewtimanager</p></td><td><p>HTTP</p></td><td><p><code>http://&lt;platform-ip&gt;:5000</code></p></td></tr><tr><td><p>Viewtimanager</p></td><td><p>HTTPS</p></td><td><p><code>https://&lt;platform-ip&gt;:5001</code></p></td></tr></tbody></table>

> 📌 **Note**:<br />
> When accessing these ports directly, if a valid session does not already exist in the browser, the user will be automatically redirected to the **Viewtiauth** login page to authenticate before being granted access to the requested module.

This allows for bookmarking or scripting access to modules while still preserving centralized session management and authentication.

<br />

### ✅ Summary

-   Authentication is centralized via **Viewtiauth**, accessible on:
    
    -   `http://&lt;platform-ip&gt;:4200` (HTTP – insecure)
    -   `https://&lt;platform-ip&gt;:4201` (HTTPS – secure)
-   Login is required to access **Viewtimanager** or **Viewtisight**.
-   Upon successful login, the **App Selector** will appear.
-   Always use HTTPS in production environments for secure access.

<br />
<br />