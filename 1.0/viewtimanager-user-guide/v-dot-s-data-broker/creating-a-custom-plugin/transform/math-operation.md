---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Math Operation'
id: Y8I-WJZ-GMD-5X6
slug: math-operation
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 12:00:00'
---
# **<span align="center">Math Operation</span>**

<br />

The **Math Operation** grid handler allows you to perform mathematical operations using selected numerical fields from your data flow. The calculated result of the operation is then stored in a completely new field added to the grid.

This is particularly useful for dynamically calculating percentages, ratios, deltas, or converting units (like bytes to gigabytes) on the fly during the ETL process.

---

## **Configuration Steps**

Configuring the **Math Operation** grid handler involves following these sequential steps:

1. **Add the Grid-Handler**: Click on the "ADD NEW GRID-HANDLER" button.
2. **Select the Grid Handler Type**: Choose **Math Operation** from the `Grid Handler Type` dropdown menu.

<br />

3. **Select the Fields**: From the `Fields` dropdown, select the numerical fields that you want to include in your mathematical operation.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/math-operation-step2.png" align="center"></figure>

<br />

4. **Define the Expression**: In the `Expression` input box, insert the desired mathematical formula. You can use standard mathematical operators, conditionals (like `if`), and reference the exact field names you selected in the previous step.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/math-operation-step3.png" align="center"></figure>

<br />

5. **Set the Column Name**: In the `Column Name` option, type the name of the new field where the result of the mathematical operation will be stored. Keep in mind that this is a completely new field that will be added to the database schema.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/math-operation-step4.png" align="center"></figure>

<br />