---
reusableId: 56
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Updating Bundle'
id: XY9-HS55-0VV-2F9
slug: updating-bundle
isVisible: true
lastUpdated: '2025-10-15 16:20:46'
---
# **<span align="center">Updating All Modules at Once</span>**

This section walks you through applying a full-platform update bundle (`artifacts.zip`) to all Viewtinet modules in one operation via the CLI.

> **Note:** Both the bundle file name and the version numbers shown here are examples; your actual filenames and versions will vary. The update bundles are provided directly by Viewtinet engineers (no public repository is available at this time).

---

## **1\. Upload the Update Bundle**

Use your preferred SCP/SFTP client to copy the ZIP bundle to the server. For example, with OpenSSH’s `scp`:

```bash

scp artifacts.zip viewtinet@your-server:/home/viewtinet/

```

Or with PuTTY PSCP:

```bash
pscp artifacts.zip viewtinet@your-server:/home/viewtinet/
```

## **2\. SSH into the Server**

Connect to the server using an SSH client (Linux/macOS ssh, Windows PuTTY, etc.):

```bash
ssh viewtinet@your-server
```

## **3\. Unzip the Bundle**

Navigate to the directory where you uploaded artifacts.zip and unzip it:

```bash
cd /home/viewtinet
unzip artifacts.zip
```

You should see output similar to:

```bash
Archive:  artifacts.zip
  creating: bundle/
 inflating: bundle/deploy
 inflating: bundle/deploy.sh
 inflating: bundle/public_key.pem
 inflating: bundle/signature
 inflating: bundle/software-bundle-6.3.5-r3243.tgz.bin
```

## **4\. Deploy the New Software**

Run the deploy script to unpack and install everything under /opt/vn/software:

```bash
./bundle/deploy.sh
```

Example output (truncated):

```bash
Uncompressing and deploying software... This may take a while.
Uncompressing software bundle /home/viewtinet/bundle/software-bundle-6.3.5-r3243.tgz
Deploying software
Backing up prior version to folder /opt/vn/software_bk_1745401625. Remove it manually if there is no need to keep it.
Backing up dhyana to /opt/vn/software_bk_1745401625/dhyana
...
Moving module viewtimon to /opt/vn/software/viewtimon
Installing deb file
(Reading database ... 112870 files and directories currently installed.)
Preparing to unpack .../viewtinet-builder_6.3.3243_all.deb ...
Unpacking viewtinet-builder (6.3.3243) over (6.3.3243) ...
Setting up viewtinet-builder (6.3.3243) ...
 Please wait
Deployment complete.
```

**Warning:** The numeric suffixes (e.g., 6.3.5-r3243, 1745401625) will differ based on the bundle version and timestamp.

## **5\. Load Docker Images**

Finally, update and load all container images for the newly deployed software:

```bash
/opt/vn/viewtinet-builder/install-packages.sh --software-directory /opt/vn/software
```

This step pulls and loads Docker images for every module. Depending on your server’s CPU, memory, and network bandwidth, this may take several minutes.

> **Note:** After loading new software images, the system automatically triggers a restart **only** for the `viewtimanager` module.

There are two ways to load updated module versions:

---

#### 1\. Full solution restart

```bash
/opt/vn/viewtinet-builder/scripts/stop-all.sh
# wait for all modules to stop
/opt/vn/viewtinet-builder/scripts/start-all.sh
```

> ⚠️ This approach takes the longest and will cause a complete outage of data collection, ingestion, and visualization across the platform.

2.  **Module-by-module restart** (recommended for shorter downtime)<br />
    Use the individual module scripts described in the chapter _[Operating Viewtinet Containers via Scripts](http:#?target=20U-C19U-8N7-KWB)_. Although this still incurs brief unavailability per module, total impact is much lower than a full restart.

<br />