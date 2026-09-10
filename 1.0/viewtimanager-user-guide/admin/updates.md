---
reusableId: 106
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Updates
id: QSU-GUJD-JHM-QCI
slug: updates
isVisible: true
isSearchable: true
lastUpdated: '2026-06-12 15:53:47'
---
# **<span align="center">Updating the Platform and Modules</span>**

<br />

## **📘 Introduction**

Viewtinet provides a built-in update mechanism that allows administrators to upgrade the entire platform — including all its modules — to the latest available version provided by Viewtinet.<br />

> ⚠️ **Important**: This update process **applies to the whole platform**. It is **not possible to update individual modules selectively** using this method.

In addition to the GUI-based procedure described in this section, updates can also be performed via the command line. For CLI-based update instructions, refer to the **"Updating Viewtinet"** section in the chapter **"Viewtinet CLI Guide"**.

---

## **📦 Prerequisites**

Before starting the update process, make sure the following requirements are met:

-   ✅ You have obtained the **official update bundle** (`.tgz` file) from Viewtinet.
-   ✅ The bundle must be the latest supported version, and the download link will be provided by the Viewtinet Support team.
-   ✅ You must also obtain the **Passphrase file** provided by the Viewtinet Support team, which is required to authenticate the update.

### **🔐 Transferring the Bundle**

1.  Use an SCP-capable tool such as **WinSCP**, **FileZilla**, or a terminal with `scp` support to connect to the Viewtinet appliance (server or virtual machine).
2.  Log in using a system user with write permissions (typically `admin` or a privileged user).
3.  Upload the `.tgz` update bundle to the following directory: `/var/viewtimanager/updates`
    
    <br />
    

### **📂 Extracting the Bundle**

Once the file is successfully uploaded, you must extract its contents:

1.  Connect to the Viewtinet appliance via SSH using the `admin` user.
2.  Navigate to the updates directory:
    
    ```bash
    cd /var/viewtimanager/updates
    ```
    
3.  Decompress the bundle by running the following command (replace `&lt;version&gt;` with your specific file name):
    
    ```bash
    tar xvzf bundle-&lt;version&gt;.tgz
    ```
    
4.  After decompressing the file, you will obtain the extracted files as shown below:
    
    <br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-bundle-extracted.png" align="center"></figure>
    
    <br />
    

---

## **Open the Update Manager**

1.  In the left-hand menu, click **Admin**.<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/lIi7e7MEFosaR3xCKoUm.png" align="center"></figure>
    
2.  Select the **Updates** tab at the top.<br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-tab-new.png" align="center"></figure>
    
    <br />
    

## **Select the Bundle and Update**

1.  Click the dropdown arrow on **Bundles Available** and select your bundle.
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-dropdown-new.png" align="center"></figure>
    
    <br />
    
2.  In the next step, you must enter the passphrase. After typing it, initiate the update by clicking **UPDATE**.
    
    <br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-passphrase.png" align="center"></figure>
    
    <br />
    
3.  Finally, confirm the process when prompted.
    
    <br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-confirm.png" align="center"></figure>
    

    <br />

4.  During the installation process, live logs will be displayed as shown below:
    
    <br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-progress.png" align="center"></figure>
    
    <br />

5.  Once the process completes, the output will indicate that the installation is finished. Click the **FINISH INSTALLATION** button to conclude the process.
    
    <br />

    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-finished.png" align="center"></figure>

---

## **Restart Each Module**

> **Important:** After updating, each module must be restarted to apply the new version.

1.  In the left menu, go to **Viewtisight** and restart the module.
2.  Proceed with each active module (e.g., **Viewtilog**, **Viewtimon**, **Viewtify QoS**), depending on your licensed modules.
3.  To restart a module, click **RESTART** in the top-right corner and confirm.

    <br />

    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-restart.png" align="center"></figure>

Repeat this process for every active module until all of them are running the latest version.
