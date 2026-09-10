---
reusableId: 69
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Preparing the Installation Bundle'
id: LQB-DJ6N-7GW-42C
slug: preparing-the-installation-bundle
isVisible: true
isSearchable: true
lastUpdated: '2026-03-10 15:37:45'
---
# **<span align="center">Preparing the Installation Bundle</span>**

<br />
This chapter describes the steps required to download, upload, and extract the Viewtinet installation bundle onto the designated server (appliance, VM, or COTS hardware).

<br />

## **Downloading the Bundle**

The Viewtinet installation package is delivered as a compressed `.tgz` file. A Viewtinet sales representative or support engineer will provide a download link to retrieve the bundle.

Additionally, you must receive the following from your Viewtinet contact:

-   The official **.tgz** bundle file.
-   A **passphrase**, which is mandatory for the installation process.

The bundle naming convention follows this structure: `bundle-6.3.5-ubuntu24.04-rXXXX-YYYYMMDDHHMMSS.tgz`.

-   The prefix `bundle-6.3.5-ubuntu24.04` remains constant for this version.
-   The subsequent characters represent the specific build revision and the generation timestamp.

Ensure the file is downloaded and stored locally on your machine before proceeding to the next step.

---

## **Uploading the Bundle**

Once the bundle has been downloaded, it must be uploaded to the server where Viewtinet will be installed. It is recommended to upload the file to the `/home/viewtinet` directory.

<br />

### **Using SCP from Linux Terminal**

If you are using a Linux-based system, open a terminal and execute (replacing the filename with your specific build):

```bash
scp bundle-6.3.5-ubuntu24.04-r5767-20260302080607.tgz viewtinet@<SERVER_IP>:/home/viewtinet
```

> **Note:** Replace `&lt;SERVER_IP&gt;` with the actual IP address of your server in all examples.

<br />

### **Using WinSCP (Windows)**

For Windows environments, use a GUI SCP client such as **WinSCP**:

1.  Open **WinSCP**.
2.  Enter the following connection details:
    
    -   **Host name:** IP address of your server
    -   **User name:** `viewtinet`
    -   **Password:** Password configured during system setup
3.  Navigate on your local machine to the folder where the `.tgz` file is located.
4.  Upload the file to the `/home/viewtinet` directory on the server.

---

## **SSH Connection**

If you are not working directly on the appliance, virtual machine, or COTS server, you must connect remotely via SSH.

Depending on your operating system, you can connect using the built-in terminal or a third-party application:

### Using the Command Line (Windows 10+, macOS, Linux)

Most modern operating systems come with a built-in SSH client. You can easily connect using your system's terminal (Command Prompt, PowerShell, or standard Linux/macOS Terminal):

1.  Open your terminal.
2.  Execute the following command, replacing `<SERVER_IP>` with the actual IP address of your server:
    
    ```bash
    ssh viewtinet@<SERVER_IP>
    ```

3.  When prompted, enter the password for the `viewtinet` user.

### Using GUI Clients

If you prefer a graphical interface or are using an older version of Windows, you can use a dedicated SSH client such as **PuTTY** or **MobaXterm**:

1.  Open your preferred SSH client.
2.  In the **Host Name** field, enter the IP address of your server.
3.  Initiate the connection and log in using the `viewtinet` user credentials.

Once logged in successfully, you will have access to the server's command-line interface to continue with the installation steps.

---

## **Extracting the Bundle**

The Viewtinet bundle must be extracted before installation.

### **Navigating and Extracting**

Navigate to the directory where the installation bundle was uploaded. By default, this is:

```bash
cd /home/viewtinet
```

Then, run the following command to extract the contents of the `.tgz` file (replace with your specific filename):

```bash
tar -xvf bundle-6.3.5-ubuntu24.04-r5767-20260302080607.tgz
```

After extraction, a new directory named `bundle` will be created. All subsequent installation steps will be carried out from within this directory.

After uncompressing the bundle, you will see an output with the following files and scripts:

```bash
decrypt.sh
deploy.sh
software-bundle-6.3.5-r5767.tgz.gpg
viewtinet-pub.asc
```

<div class="sd-callout" data-callout-type="info">Keep the <strong>passphrase</strong> provided by Viewtinet at hand, as it will be required during the execution of the installation scripts in the following steps.</div>

<br />