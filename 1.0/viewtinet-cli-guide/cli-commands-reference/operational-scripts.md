---
reusableId: 53
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Operational Scripts'
id: 86R-WT9P-MP0-NDE
slug: operational-scripts
isVisible: true
lastUpdated: '2025-10-15 16:11:57'
---
# **<span align="center">Operational CLI Scripts</span>**

Viewtinet includes a set of general-purpose CLI scripts that allow administrators to perform routine operations and maintenance tasks efficiently. These scripts are located in:

```
/opt/vn/viewtinet-builder/scripts/
```

They are executable directly by the `viewtinet` user and cover a wide range of operations, including starting and stopping the full platform, exporting/importing backups, performing log cleanup, and running diagnostics.

---

## **Key Operational Scripts**

#### `start-all.sh`

Starts all modules in the correct order.

```bash
/opt/vn/viewtinet-builder/scripts/start-all.sh
```

#### `stop-all.sh`

Stops all modules in a safe and orderly manner.

```bash
/opt/vn/viewtinet-builder/scripts/stop-all.sh
```

#### `start-gui.sh`

Starts only the GUI modules.

```bash
/opt/vn/viewtinet-builder/scripts/start-gui.sh
```

#### `stop-gui.sh`

Stops only the GUI modules.

```bash
/opt/vn/viewtinet-builder/scripts/stop-gui.sh
```

---

## **Additional Utility Scripts**

<table><tbody><tr><th><p><span align="center">Script</span></p></th><th><p><span align="center">Description</span></p></th></tr><tr><td><p><code>get_logs.sh</code></p></td><td><p>Collects logs from active containers</p></td></tr><tr><td><p><code>get_node_ip.sh</code></p></td><td><p>Retrieves the IP address of the current node</p></td></tr><tr><td><p><code>check_ip.sh</code>, <code>check_vrrp.sh</code></p></td><td><p>Verifies IP assignments and VRRP configuration</p></td></tr><tr><td><p><code>init.sh</code></p></td><td><p>Initializes required folders and permissions</p></td></tr><tr><td><p><code>update-repo.sh</code></p></td><td><p>Updates the repository metadata</p></td></tr><tr><td><p><code>uncompress-file.sh</code></p></td><td><p>Extracts <code>.tar.gz</code> or <code>.tgz</code> files</p></td></tr><tr><td><p><code>exec_job.sh</code></p></td><td><p>Executes a predefined scheduled job</p></td></tr></tbody></table>

---

## **Execution and Permissions**

All scripts in this directory are preconfigured to be executed by the `viewtinet` user and do not require `sudo`.

```bash
cd /opt/vn/viewtinet-builder/scripts/
./start-all.sh
```

---

## **Operational Scripts by Task Category**

<table><tbody><tr><th><p><strong><span align="center">Category</span></strong></p></th><th><p><strong><span align="center">Script</span></strong></p></th><th><p><strong><span align="center">Description</span></strong></p></th></tr><tr><td><p><strong>Startup / Shutdown</strong></p></td><td><p><code>start-all.sh</code>, <code>stop-all.sh</code></p></td><td><p>Starts or stops all modules</p></td></tr><tr><td><p><br></p></td><td><p><code>start-gui.sh</code>, <code>stop-gui.sh</code></p></td><td><p>Starts or stops GUI modules only</p></td></tr><tr><td><p><strong>Backup &amp; Restore</strong></p></td><td><p><code>export-backup.sh</code>, <code>import-backup.sh</code></p></td><td><p>Export and restore configuration and MongoDB backups</p></td></tr><tr><td><p><strong>Diagnostics</strong></p></td><td><p><code>troubleshooting.sh</code>, <code>get_logs.sh</code></p></td><td><p>System checks and log collection</p></td></tr><tr><td><p><strong>Disk Maintenance</strong></p></td><td><p><code>docker-images-housekeeping.sh</code></p></td><td><p>Cleans unused Docker images</p></td></tr><tr><td><p><br></p></td><td><p><code>housekeeping_viewtinet_logger_folder.sh</code></p></td><td><p>Cleans local log folders</p></td></tr><tr><td><p><strong>System Info</strong></p></td><td><p><code>get_node_ip.sh</code>, <code>check_ip.sh</code>, <code>check_vrrp.sh</code></p></td><td><p>Retrieves IP/VRRP info</p></td></tr><tr><td><p><strong>Utilities</strong></p></td><td><p><code>init.sh</code>, <code>exec_job.sh</code>, <code>uncompress-file.sh</code>, <code>update-repo.sh</code></p></td><td><p>Various helper tools</p></td></tr></tbody></table>

---

## **Backup and Restore Scripts: Detailed Usage**

Viewtinet includes two key scripts to manage backup and restore operations:

-   `export-backup.sh`: Creates a backup of essential configuration and data components.
-   `import-backup.sh`: Restores a previously generated backup.

These scripts are designed to help administrators quickly preserve and recover system state, especially during migrations, upgrades, or incident recovery.

<br />

## **Creating a Backup (**`export-backup.sh`**)**

**Location:**<br />
`/opt/vn/viewtinet-builder/scripts/export-backup.sh`

**Usage:**

```bash
/opt/vn/viewtinet-builder/scripts/export-backup.sh /path/to/backup-dir/
```

This script performs the following actions:

1.  Validates that a backup directory path has been provided.
2.  Creates a timestamped folder in the specified location.
3.  Archives the contents of:
    
    -   `/opt/vn/viewtinet-builder` → platform scripts and binaries
    -   `/opt/vn/config` → full system and module configuration
4.  Uses `docker exec` and `mongodump` to dump the contents of the MongoDB database running inside the `viewtiauth` container.
5.  Compresses all generated folders (`viewtinet-builder`, `config`, and MongoDB dump) into `.tgz` archive files.

**Example Output in the Backup Directory:**

```
config_viewtinet_bk_1681234567.tgz
viewtinet_builder_viewtinet_bk_1681234567.tgz
viewtiauth_viewtinet_bk_1681234567.tgz
```

---

## **Restoring a Backup (**`import-backup.sh`**)**

**Location:**<br />
`/opt/vn/viewtinet-builder/scripts/import-backup.sh`

**Usage:**

```bash
/opt/vn/viewtinet-builder/scripts/import-backup.sh /path/to/backup-dir/
```

This script restores only the **MongoDB database** used by the `viewtiauth` module. It performs the following steps:

1.  Validates the existence of the MongoDB `.tgz` archive in the specified directory.
2.  Extracts the archive and copies the MongoDB dump into the `viewtiauth_viewtinet-viewtiauth-mongo_1` container using `docker cp`.
3.  Executes `mongorestore` inside the container to reimport the data.
4.  Cleans up temporary files after completion.

> ⚠️ **Caution:** This process **overwrites** the current database for `viewtiauth`. It should only be performed when the module is stopped and during controlled recovery operations.

---

#### 🧠 Notes and Recommendations

-   These scripts must be run as the `viewtinet` user — no `sudo` is required.
-   Always ensure the platform or affected module (e.g., `viewtiauth`) is stopped before performing a restore.
-   For a full snapshot of the platform, combine this with a `stop-all.sh` operation.
-   Store backup folders securely and verify integrity before restoring.
-   Use consistent naming and archiving practices for backup directories.

> 💡 Include a copy of the generated `.tgz` files when contacting support for recovery assistance.

---

## **Backup Script Summary Table**

<table><tbody><tr><th><p>Script</p></th><th><p>Description</p></th><th><p>Includes</p></th></tr><tr><td><p><code>export-backup.sh</code></p></td><td><p>Creates a backup of configs and MongoDB for <code>viewtiauth</code></p></td><td><p><code>/opt/vn/viewtinet-builder</code>, <code>/opt/vn/config</code>, <code>mongodump</code></p></td></tr><tr><td><p><code>import-backup.sh</code></p></td><td><p>Restores <code>viewtiauth</code> MongoDB data from backup</p></td><td><p>Extracts, copies, and restores with <code>mongorestore</code></p></td></tr></tbody></table>

> ✅ Recommended: run `export-backup.sh` regularly and before any upgrade or major change.

<br />