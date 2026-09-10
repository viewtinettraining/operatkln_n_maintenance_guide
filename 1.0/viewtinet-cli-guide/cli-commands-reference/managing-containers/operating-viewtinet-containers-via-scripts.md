---
reusableId: 50
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Operating Viewtinet Containers via Scripts'
id: 20U-C19U-8N7-KWB
slug: operating-viewtinet-containers-via-scripts
isVisible: true
lastUpdated: '2025-10-15 16:05:16'
---
# **<span align="center">Operating Viewtinet Containers via Scripts</span>**

<br />

This chapter covers the use of CLI scripts to manage the lifecycle of Viewtinet containers. These scripts provide a consistent and safe way to start, stop, or restart all containers that belong to a specific Viewtinet module.

The scripts are located in the following path:

```
/opt/vn/viewtinet-builder/scripts/<module>/action-module.sh
```

Where `&lt;module&gt;` corresponds to one of the platform components, such as:

-   `viewtiauth`
-   `viewtisight`
-   `viewtimanager`
-   `viewticore`
-   `dhyana`
-   `viewtimon`

Each script accepts one of the following parameters:

-   `start`: Starts all containers of the selected module.
-   `stop`: Stops all containers of the selected module.
-   `restart`: Stops and then starts all containers of the selected module.

These scripts ensure that actions are applied to the entire module in a controlled manner, respecting container dependencies and the required start/stop order. They are especially useful during:

-   Maintenance or troubleshooting operations
-   Controlled shutdowns prior to system updates
-   Partial restarts when only one module requires attention

---

<br />

## **Starting a Module**

To start all containers associated with a specific Viewtinet module, use the `start` parameter with the module's `action-module.sh` script.

**Example:**

```bash
/opt/vn/viewtinet-builder/scripts/viewticore/action-module.sh start
```

> **Tip:** Wait a few seconds after running the script, then verify the container status using `dps`.

## **Stopping a Module**

To stop all containers associated with a specific module, use the `stop` parameter. This is useful before applying upgrades, backing up volumes, or performing diagnostics.

**Example:**

```bash
/opt/vn/viewtinet-builder/scripts/viewtisight/action-module.sh stop
```

> **Caution:** Do not use this during peak production hours unless necessary.

<br />

## **Restarting a Module**

The `restart` parameter combines a stop followed by a start operation for the selected module. This is commonly used to recover from container-level issues, configuration changes, or memory leaks.

<br />

**Example:**

```bash
/opt/vn/viewtinet-builder/scripts/viewtiauth/action-module.sh restart
```

> **Note:** A restart may temporarily interrupt services. Always verify the platform health afterward using `dps` and the web interface.

---

## **Additional Scripts for the** `viewticore` **Module**

Unlike other modules in Viewtinet, the `viewticore` module includes two additional scripts to manage internal components separately:

1.  `action-timescaledb.sh`
2.  `action-viewticore-internal.sh`

These scripts provide more granular control over critical infrastructure components related to data storage and internal platform logic.

<br />

## **Restarting the Time-Series Database (**`action-timescaledb.sh`**)**

This script controls the TimescaleDB container, which serves as the time-series database where all collected data is stored.

**Script path:**

```
/opt/vn/viewtinet-builder/scripts/viewticore/action-timescaledb.sh
```

**Usage:**

```bash
/opt/vn/viewtinet-builder/scripts/viewticore/action-timescaledb.sh restart
```

This script also accepts the `start` and `stop` parameters:

```bash
/opt/vn/viewtinet-builder/scripts/viewticore/action-timescaledb.sh stop
/opt/vn/viewtinet-builder/scripts/viewticore/action-timescaledb.sh start
```

> **Note:** Stopping the database will interrupt access to all metrics and historical data. Use with caution and only during planned maintenance windows.

<br />

## **Managing Internal Containers (**`action-viewticore-internal.sh`**)**

This script handles auxiliary containers that perform background processing inside the `viewticore` module, such as arbiter processes or MongoDB used for internal coordination.

<br />

**Script path:**

```
/opt/vn/viewtinet-builder/scripts/viewticore/action-viewticore-internal.sh
```

**Usage:**

```bash
/opt/vn/viewtinet-builder/scripts/viewticore/action-viewticore-internal.sh restart
```

> **Tip:** Use this script when troubleshooting internal alarms, replication issues, or if instructed by the support team.

---

> ⚠️ **Warning:** These scripts are intended for advanced operational scenarios. Avoid using them unless you understand their impact or have been instructed by Viewtinet support. In most cases, restarting the full `viewticore` module using `action-module.sh` is sufficient.

---

<br />

## **Module Script Reference Table**

The following table summarizes all supported modules and the location of their control script:

<table><tbody><tr><th><p><span align="center">Module</span></p></th><th><p><span align="center">Script Path</span></p></th><th><p><span align="center">Description</span></p></th></tr><tr><td><p><code>viewtiauth</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewtiauth/action-module.sh</code></p></td><td><p>Authentication and user access containers</p></td></tr><tr><td><p><code>viewtisight</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewtisight/action-module.sh</code></p></td><td><p>BI dashboards and reporting engine</p></td></tr><tr><td><p><code>viewtimanager</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewtimanager/action-module.sh</code></p></td><td><p>Web interface and plugin orchestration</p></td></tr><tr><td><p><code>viewticore</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewticore/action-module.sh</code></p></td><td><p>Core processing and data storage</p></td></tr><tr><td><p><code>viewticore-db</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewticore/action-timescaledb.sh</code></p></td><td><p>Time-series database (TimescaleDB) control</p></td></tr><tr><td><p><code>viewticore-int</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewticore/action-viewticore-internal.sh</code></p></td><td><p>Internal services of the viewticore module</p></td></tr><tr><td><p><code>dhyana</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/dhyana/action-module.sh</code></p></td><td><p>ETL pipelines and data collection logic</p></td></tr><tr><td><p><code>viewtimon</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewtimon/action-module.sh</code></p></td><td><p>QoS and network visibility containers</p></td></tr></tbody></table>

Use this table as a quick reference to locate and execute the correct control script for each module in your Viewtinet environment.