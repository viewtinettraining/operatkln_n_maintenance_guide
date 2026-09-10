---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grid Replace'
id: ZDE-USR-M4L-84X
slug: grid-replace
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 09:35:11'
---
# **<span align="center">Grid Replace</span>**

<br />

The **Grid Replace** handler allows you to search for specific characters, substrings, or patterns within a column and substitute them with a new value. You can write the resulting modified text into the same column (to overwrite the original data) or into a completely new target column.

This is extremely useful for sanitizing data, standardizing formats (e.g., changing commas to dots in numerical values), or removing unwanted characters from log messages.

---

## **Configuration Parameters**

To set up the **Grid Replace** handler, configure the following fields:

-   **Grid Handler Type**: Select `Grid Replace`.
-   **Mode**: Defines the specific behavior and scope of the replacement operation (explained in detail below).
-   **Column**: The source column containing the original text you want to modify (e.g., `LOC_LATITUD`).
-   **Target Column**: The destination column where the modified string will be saved. If you select the same name as the source column, the original data will be overwritten.
-   **To Replace**: The exact character, string, or regular expression pattern you want to find and substitute.
-   **Replacement**: The new text that will take the place of the matched string.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-replace-step1.png" align="center"></figure>

<br />

---

## **Execution Modes**

The power of this handler lies in its different execution modes, which allow you to control exactly which occurrences of the string are replaced.

When you click the `Mode` dropdown, you will see the following options:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-replace-step2.png" align="center"></figure>

<br />

-   `all`: Replaces _every single occurrence_ of the "To Replace" string found in the text. This is the most common mode used for global sanitization.
-   `first`: Replaces _only the very first_ occurrence of the string, leaving any subsequent matches intact.
-   `last`: Replaces _only the final_ occurrence of the string found at the end of the text.
-   `nth`: Replaces a specific occurrence based on its numerical index (e.g., replacing only the 3rd instance of a comma). Selecting this mode will typically prompt for the index value.
-   `regex`: Treats the "To Replace" field as a **Regular Expression** rather than a literal string. This allows for advanced, dynamic replacements based on complex patterns.

<br />