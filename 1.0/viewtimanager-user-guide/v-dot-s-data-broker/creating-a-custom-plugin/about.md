---
reusableId: 126
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: About
id: AE9-UUBF-A0O-RX1
slug: about
isVisible: true
lastUpdated: '2025-08-28 08:15:30'
---
# **<span align="center">Creating a Custom Plugin</span>**

<br />

<span align="justify">In this subsection, we will explain how to create a custom plugin from scratch. The process will guide you through defining each component of the plugin while exploring all the stages of the ETL cycle Extract, Transform, and Load. By the end of this section, you will understand how to configure connectors, design transformation workflows using grid handlers, and decide how and where the processed data will be loaded, ensuring the plugin fully meets the requirements of your environment.</span>

<br />

**Outline of the Creation Process**

<br />

1.  **Define the Plugin Container**
    
    -   Assign a name, description, and category.
    -   Establish the plugin as the mandatory container for one or more pipelines.
2.  **Configure the Extract Stage**
    
    -   Select and configure protocol connectors (e.g., SNMP, ICMP, Syslog, NetFlow, APIs).
    -   Associate connectors with the data sources to be integrated.
3.  **Design the Transform Stage**
    
    -   Add grid handlers to parse, normalize, and enrich incoming data.
    -   Apply mathematical operations or data mapping rules as needed.
4.  **Configure the Load Stage**
    
    -   Decide where the processed data will be stored or exported.
    -   Options include the Viewtinet TSDB (default), syslog, SCP, or CSV.
5.  **Integrate Dashboards and Reports**
    
    -   Link the plugin to existing dashboards, or create new visualizations.
    -   Ensure the outputs of the ETL pipeline are available for monitoring and analysis.
6.  **Save and Validate the Plugin**
    
    -   Deploy the plugin within the Visual Smart Data Broker.
    -   Verify that data sources are being processed correctly through the defined pipelines.

<br />