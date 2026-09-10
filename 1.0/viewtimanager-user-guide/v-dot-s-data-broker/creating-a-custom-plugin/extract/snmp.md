---
reusableId: 134
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: SNMP
id: GE5-DPO8-5AX-W06
slug: snmp
isVisible: true
lastUpdated: '2025-09-02 09:43:03'
---
# **<span align="center">SNMP Connector</span>**

<span align="justify">This subsection explains how to configure the Extract stage of a plugin using the SNMP Connector. The SNMP Connector is one of the most common connectors available in the Visual Smart Data Broker (VSDB), allowing the acquisition of data from network devices, servers, and any system supporting the SNMP protocol.</span>

<br />
**Accessing the Extract Stage**

1.  From the **Plugin Creator**, select the **Extract** stage.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/R1CROHlmnYMpjiXd0AYc.png" align="center"></figure>
    
2.  Click on the **connector selection icon** to open the list of available connectors.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/JIdUrJEU8uxjjZo4faRf.png" align="center"></figure>
    
3.  From the list, choose **SNMP Connector**
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/UtNiKc0mpDeOn0hSiTUr.png" align="center"></figure>
    
    <br />
    

Once selected, the SNMP Connector configuration window is displayed.

<br />

**Connector Configuration Parameters**

-   **Frequency Type**<br />
    Defines how often the pipeline will run:
    
    -   **Periodic**:<br />
        The pipeline is executed for the first time after the number of seconds defined in _Refresh Time (secs)_ from the moment the plugin is installed.<br />
        After each execution, the pipeline waits the same interval before running again.
    -   **Scheduled**:<br />
        The pipeline execution is configured using a **cron expression**, similar to a crontab. This allows precise scheduling by minutes, hours, days, weeks, or months.
-   **Refresh Time (secs)** _(Periodic only)_<br />
    Interval, in seconds, between each execution of the pipeline.
-   **Number of Executions**
    
    -   `-1`: The pipeline will run indefinitely.
    -   Any positive number: The pipeline will run exactly that number of times.
-   **Session**<br />
    A mandatory parameter used internally by the module to manage execution.<br />
    It must be a **string value** and uniquely identify the session.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/t5FcSc6KWYd8IxgYYNUl.png"></figure>

<br />

-   **hostPartitionSize** _(default 0)_<br />
    Defines the maximum number of hosts to be grouped and polled in each batch.
-   **partitionDelay (secs)** _(default 30)_<br />
    Defines the number of seconds to wait between each batch execution.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/4BG6bduRzTbAq96dfPRy.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/iSV5XZ1rRAuRtGnkSwXz.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/Z8iIEKxtBX6hVKCNMVbl.png" align="center"></figure>

**How Host Partitioning Works**

When polling a large number of hosts, **hostPartitionSize** and **partitionDelay** allow the workload to be divided into manageable batches.

For example:

-   If `hostPartitionSize = 20` and `partitionDelay = 10`, and the pipeline has 100 devices:
    
    -   The system will divide the 100 hosts into 5 groups of 20.
    -   Each group of 20 will be polled sequentially, waiting 10 seconds between groups.

Execution timeline example:

-   Poll 20 hosts → 00:00:00 – 00:00:05
-   Wait 10 seconds
-   Poll next 20 hosts → 00:00:15 – 00:00:20
-   Wait 10 seconds
-   Poll next 20 hosts → 00:00:30 – 00:00:35
-   Wait 10 seconds
-   Poll next 20 hosts → 00:00:45 – 00:00:50
-   Wait 10 seconds
-   Poll last 20 hosts → 00:01:05

At the end of the cycle, the pipeline waits until the next scheduled execution.

⚠️ **Important Note:** If the total polling time (including delays) exceeds the interval defined in the cron expression or refresh time, executions may **overlap**. This can cause inaccurate timestamps in the collected data. Always validate that partition sizes and delays are properly aligned with the pipeline schedule.

<br />

**Default Credentials**

The SNMP Connector also requires **default credentials**:

-   **SNMP Version** (e.g., 2c, 3).
-   **Community** (for SNMP v1/v2c).
-   **Authentication and privacy fields** (for SNMP v3).

These credentials are applied to all hosts by default, but can be overridden individually when adding hosts to the connector.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/DYTdXdo5eEivi7p3oheO.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/VTjDadscYiuwjKBqdoYS.png" align="center"></figure>

<div class="sd-callout" data-callout-type="info">The <strong>Hosts section</strong> is normally provisioned through the <strong>Inventory module</strong>, which enables massive and organized provisioning of devices. This method is recommended when managing a large number of hosts, as it ensures consistency and efficiency.</div>

<div class="sd-callout" data-callout-type="info">However, it is also possible to manually add hosts one by one using the <strong>Add Host</strong> button, specifying the corresponding <strong>OID Group</strong> for each device.</div>

<br />

**Summary**

The SNMP Connector in the Extract stage allows flexible and scalable polling of network devices:

-   **Periodic** or **Scheduled** execution modes.
-   Continuous execution with `-1` or limited runs with a fixed number.
-   Session parameter is mandatory.
-   Partitioning (hostPartitionSize, partitionDelay) prevents overloads and improves efficiency.
-   Requires at least one host and valid SNMP credentials.

Correct configuration ensures reliable and optimized data extraction for the subsequent transformation and loading stages.

<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />