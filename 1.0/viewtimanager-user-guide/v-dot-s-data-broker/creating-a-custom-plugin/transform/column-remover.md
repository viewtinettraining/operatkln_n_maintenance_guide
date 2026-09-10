---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Column Remover'
id: RVF-1N2E-SDZ-KI3
slug: column-remover
isVisible: true
isSearchable: true
lastUpdated: '2026-05-20 15:20:00'
---
# **<span align="center">Column Remover</span>**

<br />

The **Column Remover** grid handler is a transformation component that allows you to arbitrarily remove any field (column) from the **Grid** during the ETL (Extract, Transform, Load) pipeline.

This operation is particularly useful in two main scenarios:
- **Database Optimization & Security**: Preventing sensitive, redundant, or unnecessary fields from being written to the database, thereby saving storage space and adhering to data privacy policies.
- **Cleanup of Intermediate Data**: Removing temporary columns that were only created for intermediate calculations by other upstream grid handlers (such as `math-operation` or custom scripts), ensuring that the final loaded dataset remains clean and concise.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/column-remover.png" align="center"></figure>

<br />

---

### **Configuration**

Configuring the **Column Remover** requires specifying only one field:

- **Column**: A dropdown menu containing all the available columns in the current Grid structure. Select the specific column you wish to discard (for example, `memory_used` as shown in the screenshot above).

Once this handler is executed, the selected column is completely purged from the active Grid and will not be available in subsequent transformation steps or in the final load stage.

<br />

---

### **Execution Order & Validation**

Due to the destructive nature of removing a column from the pipeline, the **Column Remover** has a strict ordering constraint:

- **Positioning Requirement**: The Column Remover **must** be positioned at the very end of the list of all configured grid handlers within the ETL stage.
- **Validation Rule**: If a Column Remover is placed before any other grid handler in the sequence, the system will prevent saving the configuration and will display a red validation error message under the handler selection field:  
  `This grid must be at the end of this stage` (as illustrated below).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/column-remover-error.png" align="center"></figure>

<br />

<div class="sd-callout" data-callout-type="warning"><strong>Warning:</strong> Always ensure that all other transformation steps (such as <em>math-operation</em>, filters, or formatting handlers) that rely on a specific column are executed <strong>before</strong> the Column Remover purges it.</div>

<br />

<div class="sd-callout" data-callout-type="tip"><strong>Best Practice:</strong> It is highly recommended to use the Column Remover to clean up any temporary variables or mathematical intermediates immediately after they have fulfilled their purpose in downstream handlers like <em>math-operation</em>. This keeps the data schema neat and optimal.</div>

<br />
