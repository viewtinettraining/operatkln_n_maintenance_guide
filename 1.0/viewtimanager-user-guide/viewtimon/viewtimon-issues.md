---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtimon Issues'
id: DCE-8CF-PFV-V6J
slug: viewtimon-issues
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 10:34:57'
---
# **<span align="center">Viewtimon Issues</span>**

<br />

The **ISSUES** tab acts as the internal system log and alert center specifically dedicated to the Viewtimon DPI engine. It tracks background status checks and any operational anomalies that occur while the probe is running.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-issues.png" align="center"></figure>

<br />

---

## **Understanding the Issues Log**

Whenever the Viewtimon engine detects a problem, it logs an entry in this section. If there are unread or active issues, a red badge containing the number of alerts will appear over the "ISSUES" tab icon, proactively notifying administrators that attention is required.

The table provides a clear breakdown of each event:

-   **Timestamp:** The exact date and time the issue was detected and logged.
-   **Level:** The severity of the alert (e.g., `error`, `warning`, `info`). This helps prioritize troubleshooting efforts.
-   **Message:** A detailed description of the problem. For instance, it may report internal background status warnings or state changes in hardware bypass mechanisms (e.g., `BYPASS_DISCONNECTED`), which are crucial for ensuring high availability.

---

## **Managing Issues**

To maintain a clean and manageable log over time, you can archive issues that have already been resolved or acknowledged.

-   **ARCHIVE PAGE:** Clicking this button will archive all the currently visible alerts on the active page, removing them from the default view.
-   **Show archived:** Checking this box allows you to view historical alerts that were previously archived, which is useful for post-incident analysis or auditing recurring problems.

<br />