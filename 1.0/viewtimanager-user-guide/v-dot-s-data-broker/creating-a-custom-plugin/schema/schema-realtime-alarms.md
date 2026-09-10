---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Real-Time Alarms'
id: WTM-6BK-1O0-RY2
slug: schema-realtime-alarms
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 18:48:00'
---
# **<span align="center">Real-Time Alarms</span>**

<br />

In addition to defining the data structure, the **Schema Stage** allows administrators to configure **Real-Time Alarms**. Viewtinet supports both Query-based (scheduled) alarms and Real-Time alarms, but this stage specifically deals with the latter.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarm-intro.png" align="center"></figure>

<br />

---

## **Understanding "Real-Time" Evaluation**

The term "Real-Time" in this context refers strictly to **the exact moment the raw data is being inserted into the database**. 

During the ETL process (Extract, Transform, Load), the metric is captured and simultaneously forwarded to the Alarms Module for immediate evaluation against a threshold. This approach does **not** require a scheduled database query.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarm-etl.png" align="center"></figure>

<br />

> [!WARNING] **Evaluation Timing and Polling Frequency**
> Because the evaluation happens upon database insertion, the actual frequency of the alarm evaluation depends entirely on your extraction polling frequency. For example, if you are using an SNMP plugin that polls data every **5 minutes**, the "real-time" evaluation will occur every 5 minutes when that batch of data is inserted.

<br />

---

## **Configuring a Real-Time Alarm**

To create a new alarm, scroll down to the **Alarms** section within the Schema configuration and follow these steps:

**Step 1:** Click on the **ADD ALARM** button.

**Step 2:** Provide a descriptive **Alarm name**.

**Step 3:** From the **Metrics** dropdown, select the specific metric column that you want to monitor (e.g., `cpu_usage`, `interface-in-octets`).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarm-form.png" align="center"></figure>

<br />

---

### **Defining Alarm Dimensions and Keys**

**Step 4:** You must add the dimensions that will accompany the alarm to provide context. Click the **ADD NEW DIMENSION** button.

**Step 5:** From the added dimensions, you must select at least one dimension to act as the **Key** by checking its corresponding box. 

> [!NOTE] **What is an Alarm Key?**
> As indicated by the system tooltip, if a dimension is marked as a **key**, each unique value of that dimension can raise a distinct, separate alarm. For example, if `host` is the key, the system tracks the metric separately for each individual IP address or host name, raising independent alarms for each one that breaches the threshold.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarm-key.png" align="center"></figure>

<br />

---

### **Applying Filters**

By default, every added dimension has its **Filter** set to `Full`. This means the alarm will be evaluated against the entire dataset arriving at the database for that metric.

However, you can restrict the alarm to only evaluate specific segments of your network:

**Step 6:** Change the Filter dropdown from `Full` to `Partial`.

**Step 7:** A **Filter Type** dropdown will appear. Select the evaluation criteria you wish to use (e.g., `IPs`, `IP range`, `Subnets`, `Identifiers`, `starts-with`, `contains`, `regex`).

**Step 8:** In the **Value** field on the right, enter the specific string, IP, or regex pattern against which the data should be evaluated.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarm-filter.png" align="center"></figure>

<br />

Once the alarm structure is defined here in the Schema stage, the actual rules (Severity, Condition Thresholds, and Actions like Email or Telegram) are configured later from the **Viewtisight** interface.