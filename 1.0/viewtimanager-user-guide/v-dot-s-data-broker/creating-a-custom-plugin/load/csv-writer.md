---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'CSV Writer'
id: GXO-SEQ-ARK-SFV
slug: csv-writer
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 13:24:47'
---
# **<span align="center">CSV Writer</span>**

<br />

The **CSV Writer** producer is used to dump the final transformed grid directly into a specific file location within the Operating System. It formats the output into a comma-separated values (CSV) file, making it ideal for creating flat file backups, exporting logs for third-party analysis tools, or generating static periodic reports.

---

## **Configuration Parameters**

When you select `CSV Writer` from the producer dropdown, the system will automatically pre-configure the necessary variables using the plugin's name. However, all these fields are entirely customizable.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-writer-step2.png" align="center"></figure>

<br />

-   **CSV Filename**: The name of the resulting file. By default, it takes the `%%%PLUGIN_NAME%%%` macro, but you can explicitly specify the filename (e.g., `icmp`).
-   **CSV Destination Path**: The directory where the file will be saved. By default, it auto-configures a subfolder based on the plugin name.
-   **CSV Separator**: The character used to delimit the columns in the output file. Defaults to a comma (`,`).
-   **Use Timestamp in filenames**: A checkbox that, when enabled, automatically appends the current execution timestamp to the filename. This is highly recommended to prevent files from being overwritten on subsequent executions.

> \[!WARNING\] **Important Path Restriction**<br />
> The root directory for writing these files **must** be `/opt/vn/dhyana/var/data/`. If you attempt to configure a destination path outside of this root directory, the process might fail to write the files due to strict Operating System permission restrictions.

<br />

Here is an example of a custom configuration pointing to a specific `icmp/collected` subfolder:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-writer-step1.png" align="center"></figure>

<br />