---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Saving and Installing the Plugin'
id: CUS-PLG-FIN-001
slug: saving-and-installing
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 19:00:00'
---
# **<span align="center">Saving and Installing the Plugin</span>**

<br />

Once you have finished configuring the **Extract**, **Transform**, **Load**, and **Schema** stages, you must properly confirm, save, and install the plugin for the changes to take effect in the system.

<br />

---

## **1. Confirming Stage Changes**

Every time you modify a stage (like the Schema configuration), you will be working inside a popup or a specific configuration window. To ensure those changes are temporarily retained by the editor, you must click the **CONFIRM** button (usually located at the bottom right).

> [!WARNING] **Closing without Confirming**
> If you close the configuration window without clicking **CONFIRM**, all modifications made within that specific stage will be lost.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/plugin-confirm.png" align="center"></figure>

<br />

---

## **2. Saving Changes to the Database**

After confirming the changes within the individual stages, you will return to the main Plugin Editor interface showing the ETL flowchart. 

At this point, the changes are only in the editor's memory. To commit these configurations to the database, you must scroll to the bottom of the page and click the **SAVE CHANGES** button. 

You can also provide a brief description of what was changed before saving, which helps keep a history of modifications.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/plugin-save.png" align="center"></figure>

<br />

---

## **3. Installing the Plugin**

Saving the changes to the database ensures your work is stored, but **it does not automatically apply them to the running system**. 

To generate and deploy the actual pipelines, models, dashboards, and alarms to the host, you must **install** the plugin.

To do this:
1. Go back to the Plugin Details page (outside the editor).
2. Click the **INSTALL** button.

The system will then compile your configurations and deploy them. If the plugin already exists, the items will be seamlessly updated.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/plugin-install.png" align="center"></figure>

<br />
