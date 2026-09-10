---
reusableId: 138
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Column Constant Adder'
id: 3AE-OBTK-EV6-YSP
slug: column-constant-adder
isVisible: true
lastUpdated: '2026-05-20 15:30:00'
---
# **<span align="center">Column Constant Adder</span>**

<br />

The **Column Constant Adder** grid handler is a transformation component that allows you to apply a static, constant value to all fields of a specified column in the **Grid** during the ETL (Extract, Transform, Load) pipeline.

This operation is highly useful for populating default values, setting standard constants, or appending static labels across entire columns in your dataset.

<br />

---

### **Configuration & Examples**

Configuring the **Column Constant Adder** requires specifying two main fields:

- **Column**: Type or select the name of the column you want to operate on.
- **Constant**: Specify the static value that will be added to the column.

This handler supports both numeric values and string text, applying the changes while maintaining the original column name.

<br />

#### **Example 1: Adding a Numeric Constant**
When operating on numeric columns, you can add a fixed number to all rows (for example, adding `2500` to the `bytes_out` column):

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/column-constant-adder-1.png" align="center"></figure>

<br />

#### **Example 2: Adding a String Constant**
This handler can also be used to append text to a string or text-based column (for example, setting the value `"MyVendor"` for all rows in the `vendor` column):

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/column-constant-adder-2.png" align="center"></figure>

<br />

<div class="sd-callout" data-callout-type="tip"><strong>Best Practice:</strong> Use the Column Constant Adder when you need to define default metadata (such as vendor name, static status codes, or baseline threshold numbers) across all rows before loading the final dataset into the database.</div>

<br />