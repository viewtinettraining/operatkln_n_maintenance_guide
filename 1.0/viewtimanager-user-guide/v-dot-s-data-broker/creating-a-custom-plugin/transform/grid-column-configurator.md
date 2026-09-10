---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grid Column Configurator'
id: O3Y-V9O-SQJ-APX
slug: grid-column-configurator
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 11:17:41'
---
# **<span align="center">Grid Column Configurator</span>**

<br />

The **Grid Column Configurator** handler is designed to let you define the strict order and presence of columns within your data grid.

By explicitly specifying the output fields, you ensure that the payload maintains a consistent, standardized schema before it is inserted into the database. This is especially useful for organizing large datasets or normalizing structures from varying log sources.

---

## **Configuration Parameters**

To use this handler, select `Grid Column Configurator` from the dropdown menu. The interface will display a read-only preview string of your current **Output fields**.

To define or modify the exact order of the columns, click on the **Edit Output Fields** pencil icon () located on the right side of the handler.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-column-configurator-step1.png" align="center"></figure>

<br />

### **Editing the Schema**

Clicking the pencil icon opens the **Editing Output Fields** modal window.

In this window, you can freely manage your columns:

-   **Adding Fields**: Type the exact name of the column you want to include and separate it using a comma (`,`) or a semicolon (`;`). The system will automatically convert it into an interactive tag.
-   **Removing Fields**: Click the `X` icon next to any tag to remove it from the grid's output completely.
-   **Ordering Fields**: The order in which the tags appear here dictates the strict left-to-right sequence of the columns in the final grid structure.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-column-configurator-step2.png" align="center"></figure>

<br />

> \[!TIP\] Use this handler as one of the last steps in your transformation pipeline to guarantee that your final payload structure is clean and correctly formatted for ingestion.

<br />