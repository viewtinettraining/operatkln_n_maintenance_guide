---
reusableId: 118
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Tasks
id: QLK-CBX1-ANW-UDR
slug: tasks
isVisible: true
lastUpdated: '2025-10-15 14:54:13'
---
# **<span align="center">Tasks</span>**

<span align="justify">The Tasks tab in the Network Configuration Manager lets you orchestrate recurring or one‑off jobs against groups of devices. A Task is a named schedule + device filter, and a Subtask is a single command invocation within that job. Use Tasks to automate backups, compliance checks, or batch configuration pushes on a timetable you define.</span>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/Szq3m40HWbuIqJjUmGs3.png" align="center"></figure>

1.  **View existing tasks**
    
    -   **Name**: Your task identifier.
    -   **Devices Filter**: A previously defined filter (by group, tag, IP‑range).
    -   **Cron** / **Date**: Shows the schedule expression or next run timestamp.
    -   **Scheduled**: Enable/disable the cron job.
    -   **Allow Individual Failure**: Continue other devices if one fails.
    -   **Edit**, **Run**, **Results**, **Delete** icons for quick actions.
2.  **Create a new Task**<br />
    Click **Add a New Task** at the bottom of the list.<br />
    
3.  **Define Task properties**
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/1OZnFoP7XS98lwWcd9n0.png" align="center"></figure>
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/SiyUs5lpBf5rpXSND2YJ.png" align="center"></figure>
    
4.  **Define Task properties**<br />
    In the **View Task** dialog:
    
    -   **Name**: Give your task a clear, descriptive title.
    -   **Filter Devices**: Pick one of your pre‑built device filters.
    -   **Allow individual failure**: When checked, one device failure won’t halt the rest of the run.
    -   **Schedule Enabled**: Toggle on to open the scheduling controls.
        
        <br />
        
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/skHcNTghWAfXpePGLvAM.png" align="center"></figure>
    
    <br />
    
5.  **Set execution schedule**
    
    -   **Next Execution Date** (one‑off): Toggle on and pick a date/time.
    -   **Cron Editor**: When **Next Execution Date** is off and **Schedule Enabled** is on, configure a recurring schedule in **Minutes | Hourly | Daily | Weekly | Monthly** tabs.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/Af0kd0e7DQalTBXON92s.png" align="center"></figure>
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/MO9iqvKav1nREqCmzp3o.png" align="center"></figure>
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/AVdE7o1WBza1fJLhnwKT.png" align="center"></figure>
    
    <br />
    
6.  **Build your Task Flow**<br />
    Once saved, you’re taken to the flow editor. Your Task node appears in purple.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/R4aw8tNfNB8pvylkLX8m.png" align="center"></figure>
    
    <br />
    
    -   **Add a Subtask**: Hover over the bottom handle and click to spawn a new node.
    -   **Connect** the Task node to the Subtask node by dragging the connector dot.
        
        <br />
        
        <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/7gWj8TcWawKgL6B5rtLf.png" align="center"></figure>
        
        <br />
        
7.  **Configure each Subtask**
    
    -   Click **EDIT** on the Subtask node.
    -   In the **View Subtask** dialog, enter:
        
        -   **Name**: A descriptive subtask label (e.g. “Get Startup Configs”).
        -   **Devices**: Inherit from the parent Task filter or override with a comma‑separated list.
        -   **Command**: Select one of your predefined Commands.
            
            <br />
            
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/8Qa9bqLbMdoeXyRYjvPN.png" align="center"></figure>
    
    <br />
    
8.  **Save and Activate**
    
    -   After configuring all subtasks, click **SAVE** in the flow editor.
    -   Your Task will now run on its schedule, executing each Subtask in sequence.
        
        <br />
        
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/xlFsjpWa6vVYi5Ws3wXa.png" align="center"></figure>
    
    <br />
    
9.  **Persist the new Task**<br />
    After saving your flow, return to the **Tasks** list. You’ll see your new task row populated with its name, device filter, and Cron expression. Click **Save Changes** at the bottom right to commit it.<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/kEpm3l7JJ2BEdmpw3Idh.png" align="center"></figure>
    
    <br />
    
10.  **Confirm the schedule**<br />
    Once saved, verify that the **Cron** column shows the correct expression (e.g. `0 0/5 * ?`) and that **Scheduled** is checked. Your task is now active and will run according to the defined timetable.
    
    ```text
    Name           | Devices Filter           | Cron            | Scheduled
    -----------------------------------------------------------------------
    My Task Name   | Cisco Training Devices   | 0 0/5   * ?   | ✓
    ```
    
11.  **Run, Edit, or Delete on‑demand**
    
    -   **Edit (✏️)** – Modify the task’s name, filter or schedule.
    -   **Run (▶️)** – Trigger the task immediately against its device set.
    -   **Delete (🗑️)** – Remove the task entirely.
        
        <br />
        
        <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/HDumqVMP31YZirWf94MJ.png" align="center"></figure>
        
        <br />
        
12.  **View Task Results**<br />
    Click **Results (📋)** to inspect the history of runs. You’ll see for each execution:
    
    -   **Start / Finish** timestamps
    -   **Hosts Success / Failure** counts
    -   **Commands Run / Success / Failure** counts
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/2KrDvj6S0vFToz7QUIDM.png" align="center"></figure>
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/7APhMdiDceOCXQc8a4D2.png"></figure>
    
    <br />
    
    Expand any run to drill into host‑level details, then expand a host to see **Subtask Results** and click the **👁️** in **Command Output** to view the raw device output (e.g. running‑config).
    
    <br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/uUihXNE4tHptDMkNbKFp.png"></figure>
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/K0WkdPEebkwTMb8MVHLW.png"></figure>
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/lFloitXerrYPHdrx4ZbI.png" align="center"></figure>
    
    <br />
    

> **Note:** This section covers only the viewing of command outputs. File storage and archive management of collected configurations will be explained in the **“Configurations”** chapter.

<br />