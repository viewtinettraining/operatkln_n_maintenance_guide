---
reusableId: 43
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'About CLI Guide'
id: 486-TZTP-0YW-J40
slug: about-cli-guide
isVisible: true
lastUpdated: '2025-10-15 15:56:20'
---
# **<span align="center">Introduction</span>**

<span align="justify">Viewtinet is a modular observability platform designed to run on Ubuntu Server (20.04 and 24.04), leveraging a microservices architecture orchestrated with Docker. Its container-based approach ensures scalability, efficient resource management, and simplified maintenance.</span>

<span align="justify">This guide is intended for system administrators, network engineers, and support personnel who interact with Viewtinet through the command-line interface (CLI). It provides a practical reference for performing essential operational tasks, including:</span>

-   Monitoring the status of services and containers
-   Accessing and analyzing system logs
-   Running scripts for backups, data imports, and system checks
-   Troubleshooting and resolving common issues
-   Updating the entire platform or individual modules using CLI tools

The objective of this guide is to streamline CLI-based management of Viewtinet environments and provide clear, actionable instructions to support day-to-day operations.

This guide applies to Viewtinet versions **6.3** and **6.3.5**, and is relevant for all product lines: **Viewtilog**, **Viewtimon**, and **Viewtify QoS**.

---

### Conventions Used

-   `$` denotes commands to be run in a shell session
-   `&lt;argument&gt;` indicates a placeholder to be replaced by user-specific values
-   Scripts may require elevated permissions (e.g., `sudo`), as noted — though most are designed to be executed directly by the `viewtinet` user

By following this guide, you'll be able to efficiently operate and maintain your Viewtinet deployment using the CLI—whether you're performing routine checks, module operations, or full-system maintenance tasks such as upgrades.