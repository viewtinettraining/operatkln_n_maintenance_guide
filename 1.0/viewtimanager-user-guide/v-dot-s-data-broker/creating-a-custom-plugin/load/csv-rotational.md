---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Rotational CSV Writer'
id: 97X-FXC-MZ1-UAZ
slug: csv-rotational
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 13:43:08'
---
# **<span align="center">Rotational CSV Writer</span>**

<br />

The **Rotational CSV Writer** producer functions similarly to the standard CSV Writer by dumping the transformed grid data into the local Operating System as a flat file.

However, its key difference lies in its **rotation mechanism**: instead of appending indefinitely to a single file, it writes data continuously until a specified **rotation time** is met. Once the time limit is reached, it closes the current file and creates a new one. This is extremely useful for handling continuous, high-volume data streams and breaking them into manageable, time-based chunks.

---

## **Configuration Parameters**

When you select `Rotational CSV Writer`, the producer auto-fills the variables based on the plugin name. All fields remain fully customizable.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-rotational-step2.png" align="center"></figure>

<br />

-   **Output Path**: The directory where the rotated files will be stored. By default, it uses the `%%%PLUGIN_NAME%%%` macro to create an isolated folder.
    
    -   _Reminder:_ As with the standard CSV writer, this path **must** reside under the `/opt/vn/dhyana/var/data/` root directory to avoid OS permission issues.
-   **Rotation Period**: The exact time interval after which the file will be rotated.
-   **CSV Prefix**: The base string used for the filename before appending the rotation timestamps.

> \[!WARNING\] **Microseconds Unit for Rotation Period**<br />
> It is extremely important to note that the unit for the **Rotation Period** is **microseconds (µs)**. By default, the UI auto-fills `60`, which equals just 60 microseconds. You **must** modify this value to match your desired timeframe in microseconds. For example, if you want the file to rotate every 60 seconds (1 minute), you should enter `60000000`.

<br />

Here is an example of a custom configuration pointing to a specific syslog folder and rotating the file every 1 minute (60,000,000 microseconds):

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-rotational-step1.png" align="center"></figure>

<br />