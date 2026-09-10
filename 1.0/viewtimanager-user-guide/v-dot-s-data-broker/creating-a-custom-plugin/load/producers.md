---
reusableId: 139
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Producers '
id: DWK-9MRZ-IG3-0YN
slug: producers
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 11:33:02'
---
# **<span align="center">Producers</span>**

<br />

Once the data has passed through the **Extract** and **Transform** stages of the ETL cycle, the **Load stage** defines where the processed records will be stored or exported.<br />
In Viewtinet, these destinations are managed through components called **Producers**.

A **Producer** is responsible for delivering the transformed data to a specific output, whether it is local storage, a database, a file, or an external system. By configuring a Producer, administrators decide the final destination of the data and how it will be made available for dashboards, reports, or external integrations.

The available Producers include:

-   **Aggregator**
-   **CSV Writer**
-   **Rotational CSV Writer**
-   **Syslog Producer**
-   **SCP Producer**
-   **ViewtinetDB Producer**
-   **Kafka Producer**

Each of these Producers offers different options for storing or exporting data, depending on the integration and operational requirements.

---

## **How to Add a New Producer**

Regardless of the destination type, the initial step to configure **any** of the available producers is always the same.

1.  Navigate to the **Load** stage of your V.S. Data Broker plugin configuration.
2.  Click on the **\+ ADD NEW PRODUCER** button.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/add-producer-step1.png" align="center"></figure>

<br />

3.  A new empty Producer box will appear indicating that selecting a Producer Type is a mandatory field.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/add-producer-step2.png" align="center"></figure>

<br />

4.  Open the **Producer Type** dropdown menu and select the specific producer you wish to configure.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/add-producer-step3.png" align="center"></figure>

<br />

> \[!NOTE\] The specific configuration parameters, use cases, and integration examples for each individual producer type are explained in detail in the following sections.

<br />