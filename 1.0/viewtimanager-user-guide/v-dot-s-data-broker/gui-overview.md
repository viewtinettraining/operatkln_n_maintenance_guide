---
reusableId: 121
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'GUI Overview'
id: FJO-8GB2-32F-P4J
slug: gui-overview
isVisible: true
lastUpdated: '2025-10-15 15:13:30'
---
# **<span align="center">Visual Smart Data Broker in the GUI</span>**

<br />

## **Location in the Interface**

<span align="justify">The Visual Smart Data Broker (VSDB) is accessible through the Viewtimanager interface.<br>In the left navigation panel, the module appears as V.S. Data Broker, grouped together with other core components of the platform. By selecting this option, the central panel displays the workspace where all VSDB operations are managed.</span>

<br />

## **Main Components of the GUI**

The VSDB interface is divided into several functional areas:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/ZnBZQMLaCiS4PU2Kgxc5.png" align="center"></figure>

<br />

-   **Category Panel (left)**<br />
    Allows filtering of plugins by category (e.g., Network, Windows, SNMP). This helps administrators quickly locate the type of integration or data set they want to manage.
    
    <br />
    
-   **Search Bar (top)**<br />
    Provides a powerful filter to search plugins by name, IP, OID, decorator, model, dashboard, report, or even using regex expressions.
    
    <br />
    
-   **Central Panel (main workspace)**<br />
    Displays the list of available **plugins**. Each plugin appears as a card showing:
    
    -   Its name and version.
    -   The pipelines included.
    -   Real-time alarms associated with the pipelines.
    -   Dashboards that are linked to the plugin.
    -   Installation status and timestamps.
        
        <br />
        
-   **Action Buttons (bottom left)**
    
    -   **Create New Plugin**: Launches the wizard to define a new plugin container.
    -   **Import Plugin**: Allows importing a plugin previously exported or provided by Viewtinet.
        
        <br />
        

## **Role of Plugins**

The **plugin** is the **mandatory container element** inside the Visual Smart Data Broker.

-   A plugin acts as a logical grouping of pipelines.
-   Each **pipeline** defines a sequence of ETL operations (Extract, Transform, Load).
-   It is **not possible to create or use a pipeline without associating it to a plugin**. This ensures that all ETL logic is properly organized, managed, and linked to dashboards, alarms, and reports.

In other words, the **plugin is the entry point and organizational unit** for all ETL activities in VSDB. While pipelines are the ones that execute the data workflows, the plugin provides the framework where they are defined, documented, and connected to the rest of the platform.

---

<br />