---
reusableId: 44
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Microservices Approach'
id: OWE-SBWL-ZGV-PXH
slug: microservices-approach
isVisible: true
lastUpdated: '2025-10-15 15:56:46'
---
# **<span align="center">Microservices Architecture</span>**

<span align="justify">Viewtinet is built on a microservices-based architecture, where each module is composed of multiple Docker containers that perform specific, isolated functions. This design enhances scalability, flexibility, and performance, while allowing for modular deployment, simplified troubleshooting, and efficient resource usage.</span>

## **Key Benefits of the Microservices Approach**

-   **Scalability**: Containers can be scaled independently based on load.
-   **Flexibility**: Modules can be updated or restarted without affecting the entire system.
-   **Fault Isolation**: Errors in one container do not bring down the full platform.
-   **Resource Optimization**: Services consume only what they need.
-   **Independent Deployment**: Each component can be deployed, updated, or rolled back independently​

## **Modular Composition**

Each Viewtinet product—**Viewtilog**, **Viewtimon**, and **Viewtify QoS**—is made up of several modules, including:

-   **Viewtimanager**: Manages configuration, plugin handling, and module orchestration.
-   **Viewtisight**: Provides dashboards, reports, and data visualization.
-   **Viewtiauth**: Manages authentication and access control.
-   **Dhyana**: Implements ETL pipelines for data collection and transformation.
-   **Viewticore**: Functions as the data warehouse and time-series engine.
-   **HA\_Proxy**: Manages load balancing and proxy services.
-   **License Checker**: Handles licensing validation and enforcement​

## **GUI Modules and Their Containers**

Each GUI module (e.g., Viewtimanager, Viewtiauth, Viewtisight) typically includes:

-   **Frontend container**: Presents the user interface and handles interactions.
-   **Backend container**: Processes business logic, authentication, or configuration tasks.
-   **MongoDB container**: Stores persistent state, configuration, or user preferences.

This separation allows for cleaner architecture and easier debugging or maintenance of each role within the platform​

<br />

## **Data Processing Layers in Viewtilog (Dhyana)**

The backend module **Dhyana** follows a classic **ETL (Extract, Transform, Load)** microservice pattern:

-   **Extraction Layer**: Collects data from protocols like SNMP, NetFlow, Syslog, ICMP, etc.
-   **Transformation Layer**: Applies filters, conversions, regex processing, and mathematical calculations.
-   **Loading Layer**: Exports data to target systems in formats like XDR, UDP, TCP, or custom databases​

This pipeline-based processing is defined via XML files and is highly customizable based on network and observability needs.

<br />

## **Viewticore: The Core Data Engine**

**Viewticore** is the time-series data warehouse that supports:

-   Multi-node scalability and parallel query execution
-   Data retention policies
-   SQL functions (GROUP BY, JOIN, ORDER BY, etc.)
-   Aggregation, alarm management, and document export (PDF)
-   Query cancellation and optimization capabilities​

---

The microservices architecture in Viewtinet not only supports complex observability and analytics workflows but also makes the platform highly adaptable and easy to manage through CLI-driven operations.