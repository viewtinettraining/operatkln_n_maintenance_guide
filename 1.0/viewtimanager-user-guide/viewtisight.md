---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Viewtisight
id: V5M-N8MF-JIC-96Z
slug: viewtisight
isVisible: true
isSearchable: true
lastUpdated: '2026-09-10 19:55:02'
---
# **<span align="center">Viewtisight</span>**

## **Introduction**

<span align="justify">From within the Viewtimanager, the Viewtisight section provides administrative control over the Viewtisight module — the visualization and dashboarding engine of the Viewtinet platform. This interface does not allow users to interact with dashboards directly; instead, it enables system administrators to:</span>

-   <span align="justify">Monitor the health and performance of the Viewtisight service.</span>
-   <span align="justify">Start, stop or restart the module.</span>
-   <span align="justify">Configure server parameters and email notifications.</span>
-   <span align="justify">Manage cluster nodes.</span>
-   <span align="justify">Review warnings, errors, and operational issues.</span>

---

## **🖥️ Accessing the Viewtisight Administration Panel**

<br />

<div class="sd-callout" data-callout-type="info"><p>The Viewtisight interface is not always active by default. Access to this module depends on the Viewtisight feature being properly licensed in your deployment.</p></div>

<br />

To access the administration interface for Viewtisight:

1.  Log in to **Viewtimanager**.
2.  In the left-hand navigation menu, click on **Viewtisight** (icon: bar chart).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/YOhFgObKsSOcxLdgQBYj.png" align="center"></figure>

You will be redirected to the Viewtisight management panel, which includes module information and multiple tabs for operational control.

---

## **🧭 Interface Overview**

At the top of the screen, the following general controls and information are always visible:

-   **Version Info**: Displays the current version and revision (e.g., `6.3.5.3966 - Revision b11b8118`).
-   **Uptime**: Shows how long the module has been running.
-   **Module Control Buttons**:
    
    -   🔴 `STOP`
    -   🟠 `RESTART`
    -   🟢 `START`

### Tabs Available:

-   `STATUS`: Monitor resource usage (CPU, memory, IO).
-   `CONFIGURATION`: Edit network ports and SMTP email settings.
-   `HOSTS LIST`: Manage the cluster configuration.
-   `ISSUES`: View recent warnings and errors.

---

## **📈 STATUS Tab – Module Performance**

This tab offers performance metrics from the Viewtisight module itself:

-   **CPU Usage**: Displays current and historical CPU consumption in percentage.
-   **Memory Usage**: Tracks memory usage over time.
-   **IO Write**: Indicates the rate of disk write operations in kilobytes per second (K/s).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/UeCSP3R0sL99ARMPXXlQ.png" align="center"></figure>

<br />

These metrics help determine if the module is operating within normal parameters and are useful for troubleshooting performance issues.

---

## **⚙️ CONFIGURATION Tab – Service and Email Settings**

This tab allows administrators to configure network service ports and set up email notifications.

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/itd7UzNKH5WXm1xvUdXo.png"><br />

## **🔌 Server Configuration**

Administrators can enable or disable HTTP/HTTPS protocols and define the corresponding ports:

-   **HTTP Port**: Default is `8080`
-   **HTTPS Port**: Default is `8443`

You can toggle each option via checkboxes.

> ⚠️ **Important Notes**:
> 
> -   To **disable the insecure HTTP connection (port 8080)**, you must first access the platform using the secure HTTPS port (usually `8443`).<br />
>     For more details, refer to the **Login Requirements** section above.
> -   If you require the installation of **non-self-signed SSL certificates** (e.g., certificates from a trusted Certificate Authority), this must be requested through the **Viewtinet Helpdesk**.

Disabling HTTP ensures all access to Viewtisight is encrypted and secured through HTTPS, following best practices for production environments.

<br />

## **📧 Email Notifications**

Here you can configure the SMTP server used to send alert and report emails.

-   **SMTP Server**
-   **SMTP Username / Password**
-   **Connection Security**: e.g., `Default`
-   **Default sender for alarms**: `alerts@viewtinet.com`
-   **Default sender for reports**: `reports@viewtinet.com`

Control buttons at the bottom:

-   ✅ `Save Changes`
-   ❌ `Discard Changes / Reload`
-   🔄 `Reset Default Values`

## **📧 SMTP Integration Guide for Viewtinet**

Integrating an external SMTP server allows Viewtinet to enable key platform features such as:

-   🔐 Multi-Factor Authentication (MFA)
-   📄 Scheduled PDF report delivery
-   🚨 Alarm notifications via email

This guide outlines the steps required to configure and apply SMTP settings using the Viewtisight interface.

<br />

### **🔧 Configuration Steps**

#### **1\. Access Email Notification Settings**

1.  Log in to **Viewtimanager**.
2.  Click on the **Viewtisight** module.
3.  Go to the `CONFIGURATION` tab.
4.  Locate the **Email Notifications** section.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/R34Kty9mN7IIqpFvvHQN.png" align="center"></figure>

<br />

**2\. Enter SMTP Server Details**

<table><tbody><tr><th><p>Field</p></th><th><p>Description</p></th></tr><tr><td><p><strong>SMTP Server</strong></p></td><td><p>Hostname or IP address + port of your SMTP server (e.g., <code>smtp.office365.com:587</code>)</p></td></tr><tr><td><p><strong>SMTP Username</strong></p></td><td><p>Email or login for the SMTP account</p></td></tr><tr><td><p><strong>SMTP Password</strong></p></td><td><p>Password or App Password for authentication</p></td></tr><tr><td><p><strong>Default Sender for Alarm Emails</strong></p></td><td><p>Email address used to send alert emails</p></td></tr><tr><td><p><strong>Default Sender for PDF Reports</strong></p></td><td><p>Email address used to send PDF reports</p></td></tr></tbody></table>

<br />
<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/iDsXYozsge9BripHSN5T.png"><br />

#### **3\. Set Connection Security Level**

From the `Connection Security` dropdown, choose one of the available modes:

<table><tbody><tr><th><p>Option</p></th><th><p>Description</p></th></tr><tr><td><p><code>Default</code></p></td><td><p>TLS connection with default SSL context (recommended for most cases)</p></td></tr><tr><td><p><code>Insecure (Disables SSL)</code></p></td><td><p>No TLS, no SSL context (<strong>not recommended</strong>)</p></td></tr><tr><td><p><code>No SSL context creation</code></p></td><td><p>TLS connection without creating a custom SSL context</p></td></tr></tbody></table>

> 🛡️ Recommended: Use `Default` unless your SMTP server requires otherwise.

---

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/dA6N7vp38yHGIy3KYBBs.png"></figure>

#### **4\. Save and Confirm Configuration**

After entering all values:

1.  Click ✅ **SAVE CHANGES**
2.  A confirmation dialog will appear:<br />
    Click **YES** to confirm.

To apply the new SMTP configuration:

1.  Click the **RESTART** button.
2.  Confirm by selecting **YES** in the confirmation dialog.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/ye0prfSBHms6NsRmjgI8.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/sAYmgHs5oArG5KjQv5Ox.png" align="center"></figure>

<br />

**5\. Restart Viewtisight to Apply Changes**

Once saved, a red banner will appear:

> `Please restart Viewtisight to apply config changes`<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/XWtEUeqLhPBLi3VoLuQL.png"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/6wuO6F2xuOp2cdlS2y8w.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/Cq6Cqdkc6aq4kjvRm5VH.png" align="center"></figure>

<br />

### **⏳ Wait for Module Restart**

<br />

1\. Wait approximately \*\*3 minutes\*\*.

2\. Refresh the browser.

3\. Confirm that the \*\*Uptime\*\* counter starts from \`0\`.

If you refresh too early, the interface may not be available or may show errors.<br />
<br />
**⚠️ Temporary Model Loading Error**

Immediately after restart, it's normal to see a warning message: "Models have not been loaded yet"

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/NJTdiJwV7MH9TYlcntuQ.png" align="center"></figure>

This message appears in the performance graphs and will **disappear automatically after ~5 minutes**, once all components are fully initialized.

<br />

## **✅ SMTP Integration Complete**

Once Viewtisight is running and performance charts are visible:

-   MFA will be able to send verification codes via email.
-   Scheduled reports will be sent using the configured sender.
-   Alarm notifications will be delivered to recipients based on rules.

---

## **🛠️ Troubleshooting Tips**

-   Ensure SMTP credentials are valid and authorized to send from the specified address.
-   Confirm network connectivity to the SMTP server and port.
-   Check for typos in the server address or security option.
-   Use `Default` mode unless your email provider requires a different method.

---

## **🆘 Need Help?**

If you require support with SMTP integration, SSL certificate handling, or email deliverability, contact Viewtinet Helpdesk at:

📧 [support@viewtinet.com](mailto:support@viewtinet.com)

---

## **🖧 HOSTS LIST Tab – Cluster Setup**

In this tab, administrators can define and manage the list of Viewtisight hosts that form part of a cluster.

### Cluster Details

-   **Cluster Virtual Addresses**: Used for high-availability deployments (HA) with virtual IPs.
-   **Cluster Host List**: Displays the currently configured nodes in the Viewtisight cluster. Each host entry includes:
    
    -   `Hostname or IP Address`
    -   `LAN Hostname or IP Address`
    -   Password and password confirmation for secure registration

#### Actions:

-   ➕ `Add New Host`
-   🗑️ `Uninstall`
-   ✅ `Save Changes`
-   ❌ `Cancel Changes`

> ℹ️ **Note**:<br />
> During the installation of the Viewtinet platform via the standard installation bundle, a single instance of **Viewtisight** is installed by default.<br />
> This **HOSTS LIST** tab allows for the addition of new Viewtisight instances to enable **High Availability (HA)** or **clustered environments**.<br />
> Detailed instructions for HA and cluster configuration are provided in the **[Viewtisight's Cluster Installation Guide](http:#?target=NQU-2BQB-PAX-CE8)** and should be followed carefully to ensure proper deployment.

If only one host is present, High Availability mode is **not active**, and clustering features are disabled.

---

## **🚨 ISSUES Tab – Event Log and Errors**

This tab shows a list of operational messages related to the Viewtisight module:

<table><tbody><tr><th><p>Field</p></th><th><p>Description</p></th></tr><tr><td><p>Timestamp</p></td><td><p>Date and time of the event</p></td></tr><tr><td><p>Level</p></td><td><p>Severity (e.g., <code>error</code>, <code>warning</code>)</p></td></tr><tr><td><p>Message</p></td><td><p>Description of the issue</p></td></tr></tbody></table>

Features:

-   Search and filter by severity or message.
-   ☑ `Show archived` toggle
-   ❌ `Archive Page`
-   Pagination for browsing historical records

---

## **✅ Summary**

The **Viewtisight section within Viewtimanager** is dedicated to the **administration and lifecycle management** of the Viewtisight service. From this interface, platform administrators can:

-   Monitor Viewtisight’s health and performance
-   Control its runtime state (start, stop, restart)
-   Configure service ports and email notifications
-   Manage cluster participation
-   Review operational issues and system warnings

This administration panel is essential for ensuring that Viewtisight remains stable, integrated, and properly monitored within the Viewtinet platform.

\--

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/npZNU5du0pdeIWJtMxkg.png"></figure>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/EDtw3NRN0LYOgNTUZe7T.png"></figure>

<br />