---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'SCP Producer'
id: SCP-PRD-FL1-TR4
slug: scp-producer
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 16:31:00'
---
# **<span align="center">SCP Producer</span>**

<br />

The **SCP Producer** allows you to securely transfer files from the Viewtinet server to a remote host using the **SCP (Secure Copy Protocol)** over SSH. Instead of exporting individual grid rows like other producers, the SCP Producer works at the **file level**, picking up files from a local directory and delivering them to a specified path on the remote server.

<br />

---

## **Prerequisite: File List Connector**

<div class="sd-callout" data-callout-type="warning"><strong>Important:</strong> The SCP Producer does <strong>not</strong> work independently. It requires the <strong>File List Connector</strong> to be configured in the <strong>Extract stage</strong> of the same pipeline.<br /><br />The File List Connector is responsible for collecting files from a <code>to-collect</code> directory and moving them to a <code>to-send</code> directory. The SCP Producer then takes the files from the <code>to-send</code> directory and transfers them to the remote destination via SCP.<br /><br />Please refer to the <strong>File List Connector</strong> documentation in the <strong>Extract</strong> section for its full configuration details.</div>

<br />

---

## **Configuration Parameters**

Once you select `SCP Producer` from the Producer Type dropdown, the following connection and transfer parameters become available:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/scp-producer-config.png" align="center"></figure>

<br />

-   **Host:** The IP address or hostname of the remote server where the files will be delivered (e.g., `10.30.23.10`).
-   **Destination path:** The absolute directory path on the remote server where the files will be placed (e.g., `/home/remote_directory`).
-   **Port:** The SSH port on the remote server. The standard default is `22`.
-   **Username:** The SSH user account used to authenticate the connection on the remote host (e.g., `remote_user`).
-   **Password:** The password for the specified SSH user account.
-   **Keep Files:** When this checkbox is **unchecked** (default behavior), the SCP Producer will **delete the local files** from the `to-send` directory after they have been successfully transferred to the remote server. If **checked**, the local copies of the files will be preserved even after the transfer is completed.

<br />

> [!WARNING] **Connectivity Verification**<br />
> The SCP Producer relies on the **SSH protocol** to establish a secure connection with the remote server. Before enabling this producer, it is the **administrator's responsibility** to guarantee that:<br />
> - The remote host is **reachable** from the Viewtinet server.<br />
> - The configured **SSH port** (default `22`) is **open and accessible** through any intermediate firewalls or network policies.<br />
> - The provided **credentials** (username and password) are valid and have **write permissions** on the destination path.<br /><br />
> It is strongly recommended to perform a manual SCP or SSH connection test from the Viewtinet server's command line before activating this producer to confirm that the transfer will succeed.

<br />
