---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Changing the Management IP Address'
id: 2ZB-E2LQ-CYQ-MH7
slug: changing-the-management-ip-address
isVisible: true
lastUpdated: '2026-02-04 08:22:26'
---
# **<span align="center">Changing the Management IP Address</span>**

<br />

There are several scenarios where it may be necessary to change the **management IP address** of a Viewtinet appliance or any system running the Viewtinet solution.<br />
For example, when an appliance is first acquired, it is delivered with a **default management IP address** that must be updated to match the network segment where the appliance will be installed.<br />
In addition, due to **operational requirements** or network topology changes, administrators may also need to modify the existing management IP to ensure proper communication and integration with other components.

However, due to the **software architecture implemented by Viewtinet**, changing the IP address only at the **operating system level** is not sufficient.<br />
Multiple internal services, configuration files, and containers depend on the management IP for communication and synchronization.<br />
Therefore, it is necessary to execute the dedicated script described below, which automatically updates all internal references and restarts the affected services.

This procedure can be performed either:

-   Through an **SSH session** using the `viewtinet` user, or
-   Directly from the appliance using a **keyboard and monitor** connected to the console.

<br />

<div class="sd-callout" data-callout-type="warning"><p>Please note that the IP address mentioned in this section is the management IP of Viewtinet and is different from the IP of IPMI</p></div>

## **Command Execution**

Run the following command from the appliance console or through SSH as the `viewtinet` user:

```
/opt/vn/viewtinet-builder/scripts/change-management-ip.sh
```

To modify the **management IP address** of a Viewtinet appliance or any Viewtinet-based deployment, a dedicated script is provided.<br />
This script updates the network configuration, environment variables of all components, and restarts the required services.

Once executed, the system will display a warning message similar to:

```
You are about to change management ip address. If process fails, access to this server could be lost.
To continue, it is necessary to have IPMI access, please confirm IPMI access is enabled (yes/no):
```

<div class="sd-callout" data-callout-type="warning"><p>It is important to confirm that <strong>IPMI access is enabled</strong> to ensure remote recovery in case of a network misconfiguration.</p></div>

Type:

```
yes
```

and press **Enter** to continue.

---

## **Configuration Prompts**

The script will then request the current and new management IP details:

```
Please insert the current management address: 10.30.23.205
Please insert the current mask in CIDR format (e.g., 24 for 255.255.255.0): 24
Please insert the new management address: 10.30.23.5
Please insert the mask in CIDR format (e.g., 24 for 255.255.255.0): 24
Please insert the current gateway: 10.30.23.1
```

The script uses this information to automatically update the corresponding **Netplan** configuration file and all internal `.env` files for the different Viewtinet modules:

```
Netplan configuration updated.
...
/opt/vn/viewtinet-builder/scripts/viewtimanager/.env file updated.
...
MongoDB configuration updated.
Restarting the Viewtimanager service...
```

---

## **Automatic Restart**

The script performs a controlled restart of the main services:

```
Stopping viewtimanager_viewtinet-viewtimanager-dhyana_1 ... done
Stopping viewtimanager_viewtinet-viewtimanager-mongo_1 ... done
Stopping viewtimanager_viewtinet-viewtimanager-webssh2_1 ... done
Stopping viewtimanager_viewtinet-viewtimanager-backend_1 ... done
Stopping viewtimanager_viewtinet-viewtimanager-frontend_1 ... done
Removing containers ... done
Creating containers ... done
```

When the process finishes successfully, you will see a confirmation message:

```
Network configuration, .env update, MongoDB changes, and service restart completed successfully.
Please execute 'sudo netplan apply' to apply the Netplan changes.
Note: You will now need to use the new management address for SSH and GUI connections.
```

---

## **Final Step**

To finalize the process, apply the new network configuration:

```
sudo netplan apply
```

After this step, access to the system must be done using the **new management IP address** both for:

-   SSH connections
-   Web interface (Viewtimanager GUI)

<br />

If you are configuring your appliance for the first time, you will need to proceed to the admin user activation step (see the following [link](http:#?target=757-J2LF-2VB-34B#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation))

<br />

<br />