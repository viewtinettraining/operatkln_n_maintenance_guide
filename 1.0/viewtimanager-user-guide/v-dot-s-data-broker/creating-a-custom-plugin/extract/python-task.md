---
reusableId: 146
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Python Task'
id: G0B-9DU5-VOF-55K
slug: python-task
isVisible: true
lastUpdated: '2025-09-03 10:30:56'
---
# **<span align="center">Python Task Connector</span>**

The **Python Task Connector** allows users to integrate custom Python programs into the Visual Smart Data Broker (VSDB). Through this connector, it is possible to collect metrics, logs, or any other type of data from sources accessible via Python code.

This provides a flexible way to extend Viewtinet integrations when no standard connector is available. The Python Task executes user-developed scripts and transforms their output into records compatible with Viewtinet’s time-series database.

---

## **Creating Your Python Program**

To use the Python Task Connector, you must create a Python program in the following directory of the Viewtilog server:

```bash
/opt/vn/dhyana/bin
```

Your script must follow a predefined template to be compatible with the Python Loader.

```python
import sys
sys.path.append('/app/python-modules/')
from bin.data_wrapper import DataWrapper
import os
import warnings
warnings.filterwarnings('ignore')

_config: dict = None

def init(config: dict):
    global _config
    _config = config
    # Example: endpoint = _config.get("endpoint")

def read() -> DataWrapper:
    global _config
    # Implement your logic here
    data = DataWrapper.wrap(YOUR_DICT)
    return data
```

<br />

### **Example: Collecting CPU Usage from Linux** `/proc/stat`

<br />

The following script reads CPU usage from the `/proc/stat` file, calculates the CPU utilization percentage, and returns it with a timestamp. This script can be saved in `/opt/vn/dhyana/bin/cpu_monitor.py`.

<br />

```python
import sys
sys.path.append('/app/python-modules/')
from bin.data_wrapper import DataWrapper
import os
import warnings
import time

warnings.filterwarnings('ignore')

_config: dict = None

def init(config: dict):
    global _config
    _config = config

def read() -> DataWrapper:
    # Get the current timestamp in milliseconds
    timestamp = int(time.time()  1000000)

    # Read CPU statistics from /proc/stat
    with open("/proc/stat", "r") as f:
        line = f.readline()
    parts = line.split()

    # Extract user, nice, system, idle times
    user, nice, system, idle = map(int, parts[1:5])

    # Calculate total and usage percentage
    total = user + nice + system + idle
    busy = total - idle
    cpu_usage_percent = (busy / total)  100 if total > 0 else 0

    # Prepare dictionary output
    result = [
        {
            "timestamp": timestamp,
            "cpu_usage": round(cpu_usage_percent, 2)
        }
    ]

    # Wrap the dictionary into DataWrapper
    return DataWrapper.wrap(result)
```

<br />

### **Example Output**

If executed at runtime, the connector may produce records like:

```json
[
  {
    "timestamp": 1756894500328,
    "cpu_usage": 6.79
    
  }
]
```

-   `timestamp`: Mandatory field in milliseconds.
-   `cpu_usage`: The measured CPU utilization percentage.

<br />

### **Workflow Summary**

1.  Save your script under `/opt/vn/dhyana/bin`.
2.  Ensure it follows the Python Loader template (`init` + `read` functions).
3.  Implement your logic inside the `read()` method.
4.  Return data as a list of dictionaries with at least a **timestamp** field.

<div data-start="3573" data-end="3752"><p><br></p><div class="sd-callout" data-callout-type="alert"><strong>Important</strong><br>The Python program must always return data with a <strong>timestamp</strong> field (in microseconds 16 digits). Without it, the records cannot be stored in Viewtinet’s time-series database.</div></div>

<br />

Once you have developed and saved your Python script under `/opt/vn/dhyana/bin`, the next step is to configure the **Extract Stage** of your pipeline. This stage links the Python code you created with the Viewtinet ETL process.

<br />

## **Step 2: Configure the Extract Stage**

Follow these steps to set up the Python Task Connector:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/7Vf0zAE1kKRxoz8feGg4.png" align="center" data-drop-shadow="disabled"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/qFQTZidQxXU9zroD8VWH.png" align="center"></figure>

<br />

1.  **Select the Connector Type**<br />
    From the dropdown menu, choose **Python Task Connector**.
2.  **Name of the Pipeline**<br />
    Enter a unique pipeline name. Example: `my_python_task`.
3.  **Execution Configuration**
    
    -   Choose the **Frequency Type**: `Scheduled` or `Periodic`.
    -   Define the **Cron Expression** if using scheduled execution (e.g., every minute).
    -   Set the **Number of Executions**:
        
        -   `-1` means infinite execution.
        -   Any positive integer limits the number of runs.
4.  **Program Path**<br />
    Specify the directory where your Python script is stored, usually:<br />
    `/opt/vn/dhyana/bin/`
5.  **Module Name**<br />
    Enter the name of your Python file (without the `.py` extension).<br />
    Example: for `cpu_monitor.py`, write `cpu_monitor`.
6.  **Main Function**<br />
    Set the function to be executed inside the script. By convention, it must be `read`.
7.  **Arguments (Optional)**<br />
    If your Python script requires parameters, you can define them here by specifying a **name** and **value** pair. These will be passed to your script at runtime.
8.  **Define the Output Fields**
    
    -   Add the fields that your Python script will return.
    -   **Mandatory field:** `timestamp` → type must be `ulong`.
    -   Define additional fields as needed (e.g., `cpu_usage`, `memory_usage`, etc.).
    -   These fields must match the keys in the dictionary returned by your Python script.

✅ Example configuration:

-   **Field Name:** `timestamp` → **Field Type:** `ulong`
-   **Field Name:** `cpu_usage` → **Field Type:** `ulong`

<br />

<br />