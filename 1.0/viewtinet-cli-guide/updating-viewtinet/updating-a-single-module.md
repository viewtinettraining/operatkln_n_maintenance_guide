---
reusableId: 57
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Updating a single module'
id: D9M-IWLN-96U-LDX
slug: updating-a-single-module
isVisible: true
lastUpdated: '2025-10-15 16:21:31'
---
# **<span align="center">Updating a Single Module via CLI</span>**

This section describes how to update just one Viewtinet module (for example, `dhyana`) using the CLI. The update bundle contains only the Docker image archives for that module.

> **Note:** As with the full-platform bundle, module update ZIPs are provided by Viewtinet engineers; there is no public repository at this time.

---

## **1\. Upload the Module Bundle**

Copy the module ZIP bundle to your server via SCP/SFTP. For example:

```bash
scp dhyana-artifacts.zip viewtinet@your-server:/home/viewtinet/
```

## **2\. SSH Into the Server**

```bash
ssh viewtinet@your-server
```

## **3\. Unzip into a Module-Specific Directory**

Create a staging directory named software/ by unzipping:

```bash
cd /home/viewtinet
unzip dhyana-artifacts.zip
```

Example output:

```bash
Archive:  artifacts.zip
  creating: software/dhyana/
 inflating: software/dhyana/images.txt
 inflating: software/dhyana/viewtinet-kafka-6.3.5.tar.gz
 inflating: software/dhyana/viewtinet-viewtinet-dhyana-config-6.3.5.tar.gz
 inflating: software/dhyana/viewtinet-viewtinet-dhyana-dhyana-6.3.5.tar.gz
 inflating: software/dhyana/viewtinet-zookeeper-6.3.5.tar.gz
```

Resulting tree:

```bash
└── software
    └── dhyana
        ├── images.txt
        ├── viewtinet-kafka-6.3.5.tar.gz
        ├── viewtinet-viewtinet-dhyana-config-6.3.5.tar.gz
        ├── viewtinet-viewtinet-dhyana-dhyana-6.3.5.tar.gz
        └── viewtinet-zookeeper-6.3.5.tar.gz
```

## **4\. Backup the Existing Module**

Move the current module folder out of the way:

```bash
mv /opt/vn/software/dhyana/ /opt/vn/software/dhyana_backup
```

**Tip**: You can name your backup directory with a timestamp or version suffix to identify it, e.g. /opt/vn/software/dhyana\_backup\_$(date +%Y%m%d)}

<br />

## **5\. Deploy the New Module Files:**

Copy the new module directory into place. The -r flag is required for directories; -v (verbose) is optional:

```bash
cp -rv ./software/dhyana/ /opt/vn/software/
```

Example output:

```bash
'./software/dhyana/images.txt' -> '/opt/vn/software/dhyana/images.txt'
'./software/dhyana/viewtinet-kafka-6.3.5.tar.gz' -> '/opt/vn/software/dhyana/viewtinet-kafka-6.3.5.tar.gz'
'./software/dhyana/viewtinet-viewtinet-dhyana-config-6.3.5.tar.gz' -> '/opt/vn/software/dhyana/viewtinet-viewtinet-dhyana-config-6.3.5.tar.gz'
'./software/dhyana/viewtinet-viewtinet-dhyana-dhyana-6.3.5.tar.gz' -> '/opt/vn/software/dhyana/viewtinet-viewtinet-dhyana-dhyana-6.3.5.tar.gz'
'./software/dhyana/viewtinet-zookeeper-6.3.5.tar.gz' -> '/opt/vn/software/dhyana/viewtinet-zookeeper-6.3.5.tar.gz'
```

<br />

## **6\. Load the Module Docker Images**

Use the install-packages.sh script with the --software-directory and --module flags to load and install the new container images for the module. Replace with the module name:

```bash
/opt/vn/viewtinet-builder/install-packages.sh ---software-directory /opt/vn/software --module dhyana
```

This command pulls and loads the Docker image archives for the dhyana module. Execution time will vary based on CPU, memory, and network bandwidth.

⚠️ After loading the images, remember to restart the module using the scripts described in [Operating Viewtinet Containers](http:#?target=20U-C19U-8N7-KWB) via Scripts to apply the update.<br />