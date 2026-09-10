---
reusableId: 51
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Analyzing Logs'
id: ABY-3TLV-XA4-MNN
slug: analyzing-logs
isVisible: true
lastUpdated: '2025-10-15 16:06:47'
---
# **<span align="center">Analyzing Logs in Viewtinet</span>**

Log analysis is a fundamental part of operating and troubleshooting the Viewtinet platform. There are two main ways to access logs in a Viewtinet environment:

1.  **Accessing historical log files stored on disk**
2.  **Inspecting logs directly from running containers using** `docker logs`

Each method serves different use cases and has its advantages and limitations. This chapter describes both approaches in detail and shows how to use them effectively.

---

## **Method 1:**

### Viewing Logs from `/var/log/viewtinet`

<br />

Viewtinet modules write their logs to files under the directory:

```
/var/log/viewtinet/
```

Each module has its own log file. Some examples of the files you may find include:

```
viewtinet-active-probe.log
viewtinet-haproxy.log
viewtinet-timescaledb.log
viewtinet-viewtimanager.log
viewtinet-bypasser.log
viewtinet-kafka.log
viewtinet-viewtiauth.log
viewtinet-viewtimon.log
viewtinet-dhyana.log
viewtinet-license-cheker.log
viewtinet-viewticore.log
viewtinet-viewtisight.log
```

These files store logs **persistently and historically**, even after container restarts or system reboots.

<br />

#### 🔍 Example command:

```bash
less /var/log/viewtinet/viewtinet-viewticore.log
```

You can also use tools like `grep` to filter messages:

```bash
grep ERROR /var/log/viewtinet/viewtinet-viewtimanager.log
```

#### ✅ Advantages:

-   Long-term historical data is available.
-   Logs from all containers of a module are consolidated.
-   Easier for forensic analysis or root-cause investigations.

#### ⚠️ Disadvantages:

-   Logs can be extensive and harder to search without filters.
-   Not ideal for quick, container-specific checks.

---

## **Method 2:**

### Using `docker logs &lt;container&gt;`

<br />

You can also inspect logs directly from a specific running container using the `docker logs` command. This provides **real-time** or recent logs from the target container only.

<br />

#### 🔍 Example command:

```bash
docker logs viewtimanager_viewtinet-viewtimanager-backend_1
```

To follow logs live:

```bash
docker logs -f viewtiauth_viewtinet-viewtiauth-backend_1
```

This method is ideal for monitoring immediate behavior after restarting a service or when debugging a container that is not working properly.

<br />

#### ✅ Advantages:

-   Logs are shown in real time.
-   Focused on a single container — more precise.
-   Helpful for active debugging.

#### ⚠️ Disadvantages:

-   In high-traffic environments, logs may only include the **last few minutes**.
-   Not persistent — logs are lost if the container is removed.

---

## **Choosing the Right Method**

<br />

<table><tbody><tr><th><p>Use Case</p></th><th><p>Recommended Method</p></th></tr><tr><td><p>Historical analysis</p></td><td><p><code>/var/log/viewtinet</code></p></td></tr><tr><td><p>Real-time debugging</p></td><td><p><code>docker logs</code></p></td></tr><tr><td><p>Filtering errors across all logs</p></td><td><p><code>/var/log/viewtinet + grep</code></p></td></tr><tr><td><p>Container-specific issues</p></td><td><p><code>docker logs &lt;container&gt;</code></p></td></tr><tr><td><p>Checking after restart</p></td><td><p><code>docker logs -f</code></p></td></tr></tbody></table>

> **Tip:** You can combine both methods for a complete view — start with `docker logs` for recent activity, and fall back to the file-based logs for deeper context.

<br />