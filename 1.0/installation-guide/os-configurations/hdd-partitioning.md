---
reusableId: 66
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'HDD partitioning'
id: BGW-74PL-76T-ZMH
slug: hdd-partitioning
isVisible: true
lastUpdated: '2025-10-15 10:54:43'
---
# **<span align="center">HDD Partitioning</span>**

<br />

## **Recommended Partitioning Scheme**

Viewtinet strongly recommends installations to utilize **two separate groups of disks** for optimal performance and redundancy:

-   **First Disk Group (Operating System):** Use a RAID 1 configuration with at least **2 physical disks** to protect the operating system data.
-   **Second Disk Group (Data Warehouse):** Use at least **2 additional physical disks**. Depending on the number of disks available, it is suggested to implement either RAID 10 (preferred) or RAID 5.

For servers equipped with physical RAID controllers, configure the RAID arrays directly on the controller.

<br />

### **Recommended Partitions for Operating System (Disk Group 1 - RAID 1):**

<table><tbody><tr><th><p>Mount Point</p></th><th><p>Recommended Size</p></th><th><p>Partition Type</p></th><th><p>Filesystem</p></th></tr><tr><td><p><code>/boot</code></p></td><td><p>1 GB</p></td><td><p>Primary</p></td><td><p>XFS</p></td></tr><tr><td><p><code>swap</code></p></td><td><p>96 GB (or same value as RAM)</p></td><td><p>Primary</p></td><td><p>swap</p></td></tr><tr><td><p><code>/</code></p></td><td><p>35 GB</p></td><td><p>Logical</p></td><td><p>XFS</p></td></tr><tr><td><p><code>/home</code></p></td><td><p>50 GB</p></td><td><p>Logical</p></td><td><p>XFS</p></td></tr><tr><td><p><code>/tmp</code></p></td><td><p>10 GB</p></td><td><p>Logical</p></td><td><p>XFS</p></td></tr><tr><td><p><code>/var</code></p></td><td><p>100 GB</p></td><td><p>Logical</p></td><td><p>XFS</p></td></tr></tbody></table>

<br />

### **Recommended Partitions for Data Warehouse (Disk Group 2 - RAID 10 preferred or RAID 5):**

<table><tbody><tr><th><p>Mount Point</p></th><th><p>Recommended Size</p></th><th><p>Partition Type</p></th><th><p>Filesystem</p></th><th><p>Comments</p></th></tr><tr><td><p><code>/opt/vn</code></p></td><td><p>200 GB</p></td><td><p>Logical</p></td><td><p>ext4</p></td><td><p><br></p></td></tr><tr><td><p><code>/opt/vn/viewticore/</code></p></td><td><p>1.2 TB</p></td><td><p>Logical</p></td><td><p>ext4</p></td><td><p><br></p></td></tr><tr><td><p><code>/opt/vn/dhyana/var/data/</code></p></td><td><p>400 GB</p></td><td><p>Logical</p></td><td><p>ext4</p></td><td><p>Or increase if more space is available</p></td></tr><tr><td><p><code>/opt/vn/probe/var/</code><br>(if viewtimon is to be deployed)</p></td><td><p>600 GB</p></td><td><p>Logical</p></td><td><p>ext4</p></td><td><p>Or increase if more space is available</p></td></tr></tbody></table>

-   **Note:** Adjust partition sizes proportionally according to your specific needs and available disk capacity.

---

## **NVMe Disk Recommendations**

For servers equipped with NVMe disks that lack a physical RAID controller, configure partitions using Linux's software RAID (mdadm) utility:

-   Use RAID 1 for Operating System partitions.
-   Use RAID 10 (preferred) or RAID 5 for Data Warehouse partitions.

---

## **Virtual Machine Recommendations**

In virtualized environments, Viewtinet recommends maintaining the same logical separation:

-   Use **two separate virtual storages**:
    
    -   One virtual disk dedicated to the operating system partitions.
    -   One or more virtual disks for Data Warehouse storage.

This configuration maintains separation and ensures optimal performance and manageability.

---

## **Customizing Partitioning During Installation**

During the Ubuntu Server installation, select **Custom storage layout** to manually define partitions according to the guidelines provided above. Ensure correct filesystems and RAID configurations are applied based on your environment (physical RAID controller, NVMe disks, or virtualized environment).

---

**Important:**

-   Partitioning setup should be completed **before** proceeding with Viewtinet installation steps described later in this manual.
-   Detailed instructions for disk partitioning beyond these guidelines are outside the scope of this document.

<br />

<br />

<br />