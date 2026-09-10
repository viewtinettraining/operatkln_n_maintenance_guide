---
reusableId: 54
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Readme First Updating '
id: DDC-YZMU-EHR-VBH
slug: readme-first-updating
isVisible: true
lastUpdated: '2025-10-15 16:13:05'
---
# **<span align="center">Updating Viewtinet</span>**

<span align="justify">In this chapter we’ll cover how to update your entire Viewtinet platform—or individual modules—using only the command-line interface (CLI). Updates are distributed as ZIP bundles and must be uploaded to your Ubuntu Server instances (physical appliances or VMs) before applying them.</span>

### Prerequisites

Before you begin, ensure you have:

-   **SSH access** to the target server(s), with firewall rules permitting TCP port **22** from your workstation.
-   A CLI-capable terminal on your local machine (Linux/macOS Terminal, Windows PowerShell, etc.).
-   One of the following SCP/SFTP clients installed for bundle upload:
    
    -   **WinSCP**
    -   **FileZilla**
    -   **PuTTY PSCP**
    -   **OpenSSH’s** `scp` (native on Linux/macOS; available in Windows 10+)

> **Note:** Both the full-platform update bundle and the module-specific ZIP archives are provided directly by Viewtinet engineers. At the time of writing, there is no public repository for these bundles.

Subsequent sections will walk through the CLI commands to apply these bundles, verify versions, and confirm a successful update.