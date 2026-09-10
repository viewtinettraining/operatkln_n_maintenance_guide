---
reusableId: 151
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: WMI
id: BAR-U0M4-7C6-7OF
slug: wmi
isVisible: true
lastUpdated: '2025-09-03 16:37:21'
---
# **<span align="center">WMI Connector</span>**

<br />

The **WMI (Windows Management Instrumentation) Connector** was designed to extract performance metrics, logs, and configuration data directly from Windows servers through the WMI interface.

This connector operates as a **scheduled pipeline**, running queries periodically to gather information such as CPU usage, memory, disk statistics, and other system counters.

---

### ⚠️ Important Disclaimer

Due to a **security update released by Microsoft in March 2013**, the use of WMI for remote queries has been restricted.<br />
As a result, the **WMI Connector cannot be used with Windows servers that have this patch installed**.

For environments with modern and updated Windows systems, this connector is not functional and alternative methods (such as **WinRM over HTTPS**) must be used instead.

---

### Recommendation

If you need to collect metrics or logs from Windows servers:

-   Verify if the Windows version predates the March 2013 patch (not recommended for production).
-   Otherwise, configure the environment to use **WinRM connectors**, which are supported and secure alternatives.

<br />