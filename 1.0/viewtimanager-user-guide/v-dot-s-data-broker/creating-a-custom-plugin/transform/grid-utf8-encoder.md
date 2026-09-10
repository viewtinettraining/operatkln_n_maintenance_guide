---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grid UTF8 Encoder'
id: H4M-8GO-4NZ-VGW
slug: grid-utf8-encoder
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 09:21:08'
---
# **<span align="center">Grid UTF8 Encoder</span>**

<br />

The **Grid UTF8 Encoder** grid handler is designed to explicitly encode the entire content of the grid into UTF-8 format during the transformation stage.

This is crucial when dealing with data sources that export logs or records in legacy or alternative character encodings (such as `iso-8859-1`), ensuring that special characters and symbols are correctly ingested and displayed in the time-series database without corruption.

---

## **Configuration Parameters**

To configure this grid handler, you only need to define its original encoding format:

-   **Grid Handler Type**: Select `Grid UTF8 Encoder`.
-   **Current Encoding**: From the dropdown menu, select the original encoding format that the incoming data is currently using (e.g., `iso-8859-1`). The handler will automatically translate this into standard `UTF-8`.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-utf8-encoder-step1.png" align="center"></figure>

<br />

---

## **Best Practices & Recommendations**

> \[!IMPORTANT\] **Execution Order:** If you need to use the Grid UTF8 Encoder, it is highly recommended that you place it as the **very first** handler in your Grid Handlers list.
> 
> You can reorder your handlers by clicking the blue **Move Up** () arrow button, as shown in the image above. Encoding the payload at the very beginning ensures that any subsequent handlers (like Split, Regex, or Math Operations) process the data with the correct UTF-8 character mapping, preventing parsing errors on special characters.

<br />