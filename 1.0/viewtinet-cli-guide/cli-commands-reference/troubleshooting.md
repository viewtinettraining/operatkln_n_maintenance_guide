---
reusableId: 52
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Troubleshooting
id: XRV-WRYD-2NW-IYL
slug: troubleshooting
isVisible: true
lastUpdated: '2025-10-15 16:09:54'
---
# **<span align="center">Troubleshooting Script</span>**

The `troubleshooting.sh` script is a comprehensive diagnostic tool designed for Viewtinet deployments running on Ubuntu servers. Its main purpose is to automate the health verification of core system resources and the Viewtinet microservice modules. It checks for container availability, logs, disk and memory usage, configuration files, database health, and more.

This script is especially useful for scheduled checks via cron jobs, providing alarm generation and log saving capabilities for long-term tracking and alerting.

It supports the following modules:

-   **System**: general health of CPU, memory, partitions, interfaces.
-   **Viewtimanager**: frontend, backend, database, and network checks.
-   **Viewticore**: internal components and storage usage.
-   **Viewtisight**: service and endpoint availability.
-   **Viewtiauth**: container and network validations.
-   **Bypasser**: device state and plugin integrity.
-   **Viewtimon**: log, config, and pipeline verifications.
-   **Sniffer**: pcap partition and live capture services.
-   **Dhyana**: connector processing, data freshness, and pipelines.
-   **HA**: PostgreSQL replication and cluster consistency checks.

<br />

## **Usage**

### **Basic Usage**

```bash
$ sudo  /opt/vn/viewtinet-builder/scripts/troubleshooting.sh
```

This will run all checks and output a global health summary.

### Optional Flags

```bash
  -h | --help                         Show help message
  -l | --logging <directory>          Enable logging to given directory
  -a | --alarms <directory>           Enable alarm output as CSV (for Self Monitoring plugin ingestion)
  -d | --dhyana-csv-dir <directory>   Enable Dhyana pipeline stats to CSV (used by dashboard plugin)
  -t | --time-inteval <mins>          Set time interval in minutes for log checks
  -p | --parallel-jobs <num>          Max parallel jobs (default: 5)
  --dhyana-logs                       Enable pipeline log checking (can be slow with many pipelines)
  --dhyana-files                      Check data folder in /opt/vn/dhyana/var/data/ (verbose, optional)
```

<br />

## **Module Selection**

You can specify individual modules to check:

```bash
sudo  /opt/vn/viewtinet-builder/scripts/troubleshooting.sh dhyana
```

To check only system health:

```bash
sudo  /opt/vn/viewtinet-builder/scripts/troubleshooting.sh system
```

<br />

## **Alarm and Dhyana Export Features**

### Alarm Generation (`-a`)

When executed with the `-a` option, the script will activate alarm generation and output a CSV file compatible with Viewtinet's **Self Monitoring plugin**. This allows automatic ingestion of system and module statuses as structured alarms.

The output CSV includes:

-   Timestamp
-   Alarm name
-   Severity (clear, minor, major, critical)
-   Description

This enables seamless integration with alarm dashboards and alerting rules.

<br />

## **Dhyana Pipeline Statistics (**`-d`**)**

The `-d` option enables an advanced export of **Dhyana pipeline status metrics** to a CSV file in the specified directory. This file is designed for ingestion by the **Dhyana Dashboard plugin** and is typically used to generate graphs and reports about pipeline health.

The data includes:

-   Pipeline name and PID
-   Execution status
-   Error count in logs (if `--dhyana-logs` is enabled)

> ⚠️ This is useful for performance analytics, but enabling `--dhyana-logs` may slow down execution in environments with many pipelines.

<br />

## **Optional Deep Checks**

-   `--dhyana-logs`: Deep scan of Dhyana container logs to extract pipeline-related errors. It enhances precision but increases runtime, especially in environments with many concurrent pipelines.
-   `--dhyana-files`: Enables verification of every subdirectory in `/opt/vn/dhyana/var/data/` to detect stale or oversized files. This check is verbose and should be used selectively.

<br />