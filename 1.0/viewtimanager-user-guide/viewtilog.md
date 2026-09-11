---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Viewtilog
id: J5H-53DD-UC3-YS6
slug: viewtilog
isVisible: true
isSearchable: true
lastUpdated: '2026-09-10 19:55:21'
---
# **<span align="center">Viewtilog</span>**

<span align="justify">The Viewtilog module ingests, parses and stores logs from your network and security devices. It runs on one or more Dhyana collector appliances and feeds log data into the Viewtinet platform for analysis, visualization and alerting.</span>

> **Prerequisite**<br />
> Make sure you have installed and configured your Dhyana collector(s) according to the **Viewtilog** chapter of the Installation Guide before adding them here.

---

## **Status**

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/N9dvqudCh7Kzg0Sm12uC.png" align="center"></figure>

-   **Version**: e.g. `6.3.5.3966 (Revision aaf37d89)`
-   **Uptime**: Time since the ViewtILog service started.
-   **Controls**:
    
    -   **Stop**: Gracefully shuts down the connectors.
    -   **Restart**: Restarts the service without changing configuration.
    -   **Start**: (Disabled when running) Starts the service if stopped.

---

## **Configuration**

> **Note**: All settings on this tab are applied **automatically** during module installation.
> 
> <br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/oqmHfYqHNcLFKPj7YzpL.png" align="center"></figure>

<br />

-   **Main directory**: Path where the Dhyana collector stores incoming log files (e.g. `/opt/vn/dhyana/`).
-   **Watchdog time (secs)**: Interval for internal health checks (default `60`).

---

## **Hosts List**

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/lxgxyxBtwxuO9Ig5GhvI.png" align="center"></figure>

Defines which Dhyana appliances feed logs into Viewtilog.

1.  **Cluster for Connectors**
    
    -   **High availability mode**
        
        -   **No HA** if only one host is defined.
        -   **HA** applies when two or more hosts are present with virtual addresses.
2.  **Cluster Virtual Addresses** (optional)<br />
    Click **\+ Add New Virtual Address** to define a floating IP for HA.
3.  **Cluster Host List**
    
    -   **\+ Add New Host**: Bring up a blank row.
    -   Enter each collector’s:
        
        -   **Hostname or IP Address** (management plane)
        -   **LAN Hostname or IP Address** (data plane)
        -   **Password** and **Password confirm** (SSH credentials for `viewtinet` user)
    -   Click **Save Changes** to apply.

> **Note**: Collector installation and tuning is covered in the **[Viewtilog's Cluster Installation](http:#?target=ND7-Z3HP-QAV-NIZ)** chapter of the Installation Guide.

---

## **Issues**

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/g2jfllBnhjXkYQ356sL9.png" align="center"></figure>

All operational warnings and errors from the ViewtILog connectors:

-   **Timestamp**: When the event was logged.
-   **Level**: `warning`, `error`, etc.
-   **Message**: Detailed description (e.g. host key additions, connection failures).

Controls:

-   **Show archived**: Toggle to include archived entries.
-   **Archive Page**: Manually archive the current list.

---

> **Restart After Changes**<br />
> If you update hosts or virtual addresses, use the **Restart** button on the **Status** tab to apply changes without waiting for the next automated restart.

<br />