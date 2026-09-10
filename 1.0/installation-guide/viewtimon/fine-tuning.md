---
reusableId: 103
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Fine Tuning'
id: JB9-WUEB-9W1-SFX
slug: fine-tuning
isVisible: true
lastUpdated: '2025-10-15 10:28:49'
---
# **<span align="center">Fine-Tuning for Viewtimon Performance</span>**

To maximize throughput, minimize latency, and ensure reliable operation, apply the following kernel and system-level tunings on every Viewtimon host.

<br />

## **High Precision Event Timer (HPET)**

HPET provides high-resolution timestamps for packet capture and scheduling:

1.  **Check support**
    
    ```bash
    cat /sys/devices/system/clocksource/clocksource0/available_clocksource
    # e.g.: tsc hpet acpi_pm
    ```
    
2.  **If** `hpet` appears, enable it in GRUB:
    
    -   Edit `/etc/default/grub`
    -   Append `clocksource=hpet` to `GRUB_CMDLINE_LINUX_DEFAULT`:
        
        ```diff
        --- /etc/default/grub
        + GRUB_CMDLINE_LINUX_DEFAULT="… clocksource=hpet"
        ```
        
3.  **Update GRUB** and reboot:
    
    ```bash
    sudo update-grub
    sudo reboot
    ```
    

---

## **Hugepages**

Allocating large pages reduces TLB overhead and boosts memory performance.

<br />

### **A. 1 GB Hugepages (Recommended)**

1.  **Verify support**
    
    ```bash
    cat /proc/cpuinfo | egrep -o pdpe1gb | head -n1
    # returns pdpe1gb if supported
    ```
    
2.  **Determine count** based on NUMA nodes and RAM:
    
    <table><tbody><tr><th><p>NUMA nodes</p></th><th><p>RAM</p></th><th><p>Hugepages</p></th></tr><tr><td><p>1</p></td><td><p>128 GB</p></td><td><p>32</p></td></tr><tr><td><p>1</p></td><td><p>96 GB</p></td><td><p>24</p></td></tr><tr><td><p>1</p></td><td><p>64 GB</p></td><td><p>16</p></td></tr><tr><td><p>1</p></td><td><p>32 GB</p></td><td><p>8</p></td></tr><tr><td><p>2</p></td><td><p>128 GB</p></td><td><p>32</p></td></tr><tr><td><p>2</p></td><td><p>96 GB</p></td><td><p>32</p></td></tr><tr><td><p>2</p></td><td><p>64 GB</p></td><td><p>24</p></td></tr><tr><td><p>2</p></td><td><p>32 GB</p></td><td><p>16</p></td></tr></tbody></table>
    
3.  **Enable in GRUB** (example: 1 NUMA, 128 GB → 48 pages):
    
    ```diff
    --- /etc/default/grub
    + GRUB_CMDLINE_LINUX_DEFAULT="… default_hugepagesz=1G hugepagesz=1G hugepages=48"
    ```
    
4.  **Update GRUB**:
    
    ```bash
    sudo update-grub
    ```
    
5.  **Mount hugepage filesystem**:
    
    ```bash
    echo "nodev /mnt/huge_1GB hugetlbfs pagesize=1GB 0 0" | sudo tee -a /etc/fstab
    sudo mkdir -p /mnt/huge_1GB
    sudo mount -a
    ```
    

> **Notes:**
> 
> -   A single-NUMA node server is highly recommended.
> -   On dual-NUMA servers, the OS will free half of node 2’s pages at runtime if unused.

<br />

### **B. 2 MB Hugepages (Fallback)**

<br />

1.  **Verify support**
    
    ```bash
    cat /proc/cpuinfo | egrep -o pse | head -n1
    # returns pse if supported
    ```
    
2.  **Mount and configure**:
    
    ```bash
    echo "nodev /mnt/huge hugetlbfs defaults 0 0" | sudo tee -a /etc/fstab
    sudo mkdir -p /mnt/huge
    echo "vm.nr_hugepages = X" | sudo tee -a /etc/sysctl.conf
    sudo mount -a
    sudo sysctl -p
    ```
    
    Replace `X` with the desired number of 2 MB pages.
    

---

## **Viewtimon High-Performance Configuration**

### **CPU Isolation**

Prevent other processes from contending with Viewtimon:

1.  **Compute CPUs to isolate**:
    
    ```bash
    STAGES=$(grep -c '^stage' /opt/vn/config/viewtimon/etc/pipeline.cfg)
    ANALYZE=$(grep -A1 '^stage' /opt/vn/config/viewtimon/etc/pipeline.cfg               | grep -c '= analyze')
    CPUS=$((STAGES + ANALYZE + 2))   # +1 master +1 bypasser
    echo "Isolate $CPUS CPUs"
    ```
    
    Or run the helper script:
    
    ```bash
    sudo /opt/vn/viewtinet-builder/scripts/compute-isolated-cpus.sh
    ```
    
2.  **Edit GRUB** (example: isolate CPUs 3–6):
    
    ```diff
    --- /etc/default/grub
    + GRUB_CMDLINE_LINUX_DEFAULT="… isolcpus=3-6 nohz_full=3-6 rcu_nocbs=3-6 nohz=on"
    ```
    
3.  **(AMD only)** add:
    
    ```diff
    + iommu=pt amd_iommu=on
    ```
    
4.  **Apply changes**:
    
    ```bash
    sudo update-grub
    ```
    

### **CPU Performance Setup**

Disable Spectre/Meltdown mitigations in trusted environments:

```diff
--- /etc/default/grub
+ GRUB_CMDLINE_LINUX_DEFAULT="… mitigations=off"
```

```bash
sudo update-grub
```

---

> **Final Step:**<br />
> Reboot the server to apply all kernel parameters and mounts:
> 
> ```bash
> sudo reboot
> ```

<br />