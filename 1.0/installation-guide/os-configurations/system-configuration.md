---
reusableId: 68
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'System Configuration'
id: GG6-I8VJ-HKN-FYJ
slug: system-configuration
isVisible: true
lastUpdated: '2025-10-14 09:45:50'
---
# **<span align="center">System Initialization</span>**

<br />
This chapter describes the essential steps required to configure the system profile, SSH service, and time synchronization services. These configurations must be completed before proceeding with the installation of Viewtinet.<br />
User Profile Setup

All Viewtinet modules, containers, and services run under the `viewtinet` user. This user must be created during the operating system installation process.

### Profile Setup During Installation

On the **Profile setup** screen, enter the following details:

-   **Your name:** `viewtinet`
-   **Your server’s name:** Any hostname of your choice (e.g., `my_viewtilog`)
-   **Pick a username:** `viewtinet`
-   **Choose a password:** Set a secure password
-   **Confirm your password:** Re-enter the same password

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/qRQJX723KTkRI4WS2odl.png"></figure>

Click `[Done]` to continue.

> ⚠️ Do not change the username. It must be `viewtinet` for the system to function correctly.

---

## **SSH Setup**

To enable secure remote management, it is mandatory to install and enable the **OpenSSH Server**.

On the **SSH Setup** screen:

-   Check the option: `[X] Install OpenSSH server`
-   Leave the import identity option as `No`
-   Ensure: `[X] Allow password authentication over SSH` is checked

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/Ud68BjEZe1OzSldgxJeA.png"></figure>

Click `[Done]` to proceed.

Optional Packages

If the installer presents a screen for selecting additional packages (e.g., "Featured Server Snaps"):

-   **Do not select any packages**.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/V0OGHxgoBgQn5JAxh0Xl.png"></figure>

<br />

-   Simply click `[Done]` to continue the installation process.

> ❗Installing additional packages at this point is not recommended and may cause conflicts with Viewtinet modules.

---

## **NTP Configuration**

Correct time synchronization is essential. Configure the system to use an NTP server as follows:

### **Install NTP Service**

```bash
sudo apt-get install ntp
```

### **Edit NTP Configuration File**

```bash
sudo vi /etc/ntp.conf
```

If the customer provides NTP servers, add them below the section:

```bash
# Specify one or more NTP servers
```

Otherwise, use public NTP servers closest to your location: [https://support.ntp.org/bin/view/Servers/NTPPoolServers](https://support.ntp.org/bin/view/Servers/NTPPoolServers)

<br />

### **Restart NTP Service**

```bash
sudo service ntp restart
```

### **Verify NTP Status**

```bash
sudo service ntp status
```

### **Verify Status and Synchronization**

```bash
sudo systemctl status systemd-timesyncd
timedatectl
```

Expected output:

```bash
System clock synchronized: yes
NTP service: active
```

Once all steps in this chapter are completed, the operating system is correctly configured to proceed with the Viewtinet installation. Continue with the steps outlined in the Bundle Installation documentation.

<br />