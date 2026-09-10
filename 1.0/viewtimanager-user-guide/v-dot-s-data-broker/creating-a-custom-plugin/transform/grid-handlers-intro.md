---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grid handlers intro'
id: DGL-CW6-BNR-HIL
slug: grid-handlers-intro
isVisible: true
isSearchable: true
lastUpdated: '2026-05-20 17:30:00'
---
# **<span align="center">Grid Handlers</span>**

<br />

## Grid Concept

During the Extraction phase, all the obtained information is stored in an in-memory structure called a **Grid**. To simplify the understanding process, think of it as a matrix or table with rows and columns.

The Grid, as a structure, is sent to the **Transformation process** to perform actions such as adding, removing, modifying, or creating new fields based on the data obtained in the Extraction stage.

<br />

## What are Grid Handlers?

**Grid Handlers** are the individual components or operations used within the Transform Stage to manipulate the Grid. By applying different handlers, the data obtained in the previous stage can be heavily transformed and refined before it moves to the next phase of the pipeline.

These handlers are incredibly versatile and are able to:

-   Filter records based on the information extracted.
-   Apply both simple and complex mathematical operations (especially useful for numerical fields) to calculate new fields.
-   Apply regular expressions (regexes) to filter information or extract specific fields.
-   Apply AI techniques to generate new information based on both historical and current data.
-   Add information from external sources (such as CSV files) to dynamically enrich statically-configured data.

<br />

---

### How to Add a New Grid Handler

To add a new Grid Handler to your Transform stage, follow these steps:

**Step 1:** Click the **"+ ADD NEW GRID HANDLER"** button located at the bottom of the Transform stage configuration panel.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-handler-add-button.png" align="center"></figure>

<br />

**Step 2:** A new **Grid Handler** card will appear. Click on the **"Grid Handler Type"** dropdown field to reveal the list of all available handlers.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-handler-type-selector.png" align="center"></figure>

<br />

**Step 3:** Select the desired handler from the dropdown list. The available Grid Handler types are:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-handler-dropdown.png" align="center"></figure>

<br />

<div class="sd-callout" data-callout-type="info"><strong>Note:</strong> This procedure applies to <strong>all</strong> Grid Handlers described in the following sections. Each handler type has its own specific configuration fields that will appear once selected from the dropdown.</div>

<br />
