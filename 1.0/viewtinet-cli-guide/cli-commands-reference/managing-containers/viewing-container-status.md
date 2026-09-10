---
reusableId: 48
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewing Container Status'
id: 1GM-1PE0-3E1-IFM
slug: viewing-container-status
isVisible: true
lastUpdated: '2025-10-15 15:59:03'
---
# **<span align="center">Viewing Container Status</span>**

<br />

To list all running containers, Viewtinet provides a convenient alias in the CLI called `dps`, which maps to the following command:

```bash
sudo docker ps
```

You can simply execute:

```bash
$ dps
```

When you run the `dps` command (an alias for `sudo docker ps`), the CLI returns a table showing the current state of all active Docker containers in the Viewtinet environment. Each row corresponds to a container and includes useful details such as:

-   **CONTAINER ID**: The unique identifier for the container.
-   **IMAGE**: The Docker image used to create the container, including the version (e.g., `viewtinet/viewtimanager/backend:6.3.5`).
-   **COMMAND**: The entrypoint or command used to start the container.
-   **CREATED**: How long ago the container was started.
-   **STATUS**: Indicates whether the container is running, how long it has been up, and whether it is healthy.
-   **PORTS**: Lists the ports being used and exposed by the container (e.g., `0.0.0.0:4500-&gt;4000/tcp`).
-   **NAMES**: The assigned name for the container, which typically includes the module and container role (e.g., `viewtimanager_viewtinet-viewtimanager-backend_1`).

This output is extremely useful for diagnosing issues, verifying that all expected services are running, and identifying containers that might be misconfigured or failing. It also helps track which version of each component (e.g., `:6.3.5`) is currently deployed.

Below is a sample output from a fully deployed Viewtinet system:

```
CONTAINER ID   IMAGE                                     COMMAND                  CREATED        STATUS                  PORTS                                                                                          NAMES
3f1d3d216126   viewtinet/kafka:6.3.5                     "/opt/bitnami/script…"   2 hours ago    Up 2 hours              0.0.0.0:9092->9092/tcp, :::9092->9092/tcp                                                      dhyana_kafka_1
d4ba21773245   viewtinet/viewtinet-dhyana/dhyana:6.3.5   "/app/dhyana -p /con…"   2 hours ago    Up 2 hours                                                                                                             dhyana_viewtinet-dhyana-kafka_1
7b0bf85cebb4   viewtinet/zookeeper:6.3.5                 "/opt/bitnami/script…"   2 hours ago    Up 2 hours              2181/tcp, 2888/tcp, 3888/tcp, 8080/tcp                                                         dhyana_zookeeper_1
b48a20cd0840   viewtinet/viewtinet-dhyana/dhyana:6.3.5   "nice -n -20 /app/dh…"   2 hours ago    Up 2 hours                                                                                                             dhyana_viewtinet-dhyana_1
62bdcff67243   viewtinet/viewtinet-haproxy:6.3.5         "docker-entrypoint.s…"   23 hours ago   Up 23 hours                                                                                                            haproxy_viewtinet-haproxy_1
ae188f58470c   viewtinet/mongodb:6.3.5                   "docker-entrypoint.s…"   23 hours ago   Up 23 hours             27017/tcp                                                                                      license-checker_viewtinet-license-checker-mongodb_1
0f1b8bde4d6b   viewtinet/license-checker:6.3.5           "/app/license-checke…"   23 hours ago   Up 23 hours             0.0.0.0:9974->9974/tcp, :::9974->9974/tcp                                                      viewtinet-license-checker
...
```

> **Note**: This is a real example based on a running Viewtinet system. The actual output will depend on the modules deployed and their current state.

<br />