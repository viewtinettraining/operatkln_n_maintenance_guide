---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Key Value'
id: ZIX-2MR-SWE-6VG
slug: key-value
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 12:00:00'
---
# **<span align="center">Key Value</span>**

<br />

The **Key Value** grid handler is designed to parse and extract values from a string or record that contains data in a delimited key-value format (e.g., `key1=value1,key2=value2,key3=value3,key_n=value-n`). 

By using this handler, the system automatically creates new database columns corresponding to the keys found in the record, and populates them with their associated values.

---

## **Context and Use Case**

A very common use case for this grid handler involves integrations with network devices and security appliances (such as firewalls or intrusion detection systems) that export event logs via Syslog. These logs frequently use the **CEF (Common Event Format)**, which encapsulates multiple data fields inside a single message payload as key-value pairs. 

For more information about CEF format, you can refer to the official [Micro Focus ArcSight CEF documentation](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors-8.3/cef-implementation-standard/) or similar industry standards.

Using the **Key Value** grid handler on a `syslog_record` column allows the ETL process to explode the CEF payload and properly index each property into its own column.

<br />

---

## **Configuration Steps**

Configuring the **Key Value** grid handler involves following these sequential steps:

1. **Add the Grid-Handler**: Click on the "ADD NEW GRID-HANDLER" button and select **Key Value** from the `Grid Handler Type` dropdown menu.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/key-value-overview.png" align="center"></figure>

<br />

2. **Select the Message Column**: From the `Message Column` dropdown, select the field that contains the raw key-value string. Normally, for Syslog events, this column is `syslog_record`.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/key-value-step3.png" align="center"></figure>

<br />

3. **Define Output Fields**: Click on the pencil icon (<i class="fa fa-pencil"></i>) to edit the Output Fields. This will open a text editor popup where you can define which keys will be extracted into new columns.
   
   > [!TIP]
   > The easiest way to configure this is to prepare the list of fields separated by commas in a simple text editor, paste the entire string into the input box, press Enter, and then click **SAVE**.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/key-value-step4.png" align="center"></figure>

<br />

4. **Enable CEF Header (Optional)**: If the incoming logs follow the Common Event Format, be sure to check the **"Has CEF Header"** checkbox. This instructs the parser to handle the standard CEF prefix before extracting the key-value pairs.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/key-value-step5.png" align="center"></figure>

<br />