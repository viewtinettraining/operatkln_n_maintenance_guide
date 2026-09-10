---
reusableId: 100
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Prerequisites
id: K8S-P9GS-SJQ-339
slug: prerequisites
isVisible: true
lastUpdated: '2025-10-15 14:58:01'
---
# **<span align="center">Prerequisites</span>**

<span align="justify">Before you can effectively use the Configuration Manager feature in Viewtinet, it is essential to prepare your inventory and access credentials. This chapter outlines the necessary prerequisites and the steps to verify them within the Inventory module.</span>

## **1\. Devices Added to Inventory**

<span align="justify">Ensure that all devices to be managed are added to the Inventory. Devices can be imported via CSV files, autodiscovery, or added manually.</span>

<span align="justify">The detailed process for provisioning devices into the inventory is explained in the Inventory chapter.</span>

<span align="justify">In the Inventory overview tab, you will see a list of devices along with key details such as IP address, device name, OID groups, operating system, software version, device type, and vendor</span>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/7JRNcefCYxntnLB9GEUl.png" align="center"></figure>

<br />

## **2\. Device Filtering**

<span align="justify">To use the Configuration Manager feature, it is necessary to have a filter created that selects the devices to be included. This filter defines the subset of devices on which configuration tasks will operate.</span>

<span align="justify">The creation and management of filters is explained in detail in the Inventory chapter. Filters allow you to target devices based on attributes such as vendor, operating system, IP address, or other metadata.</span>

<span align="justify">Filters can also be combined with logical operators (AND, OR, NOT) to precisely refine the device selection.</span>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/CglaXww1LUAHyUeKk61W.png"></figure>

## **<span class="text-large"><br></span>3\. Access Credentials Configuration**

<span align="justify">Credentials can be added by using the Viewtinet provisioning template or by importing your own CSV file.</span>

<span align="justify">If these credentials have not been imported using the methods mentioned above, it is necessary to create the credentials manually within the Inventory module.</span>

<span align="justify">In the Credentials tab of Inventory, verify that you have defined the necessary credentials, including:</span>

-   <span align="justify">SSH access credentials (port, username, authentication type, password or key)</span>
-   <span align="justify">Telnet access credentials if applicable</span>

To create a new credential, click the \*\*"ADD New Credential"\*\* button and configure the connection parameters for the devices you want to include in the Configuration Manager feature.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/KoHQmqrgo6kiFPG0xxH6.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/TjGu5czRScCowR8e813J.png" align="center"></figure>

<br />

<figure align="center" style="width:21%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/NqihyBDVhoNO9q2M083d.png" width="21%" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/k15mESrCcY2Xh7Xx5xQR.png" align="center"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/gWSh77BV9Og7ynvzpMaB.png"></figure>

<br />

## **4\. Device-Credential Relations**

<span align="justify">Finally, assign credentials to devices by creating relations in the Relations tab. This mapping is necessary so Configuration Manager knows which credentials to use to access each device.</span>

<span align="justify">In the Relations tab, filter devices and credentials to assign them accordingly.</span>

<br />

Once these prerequisites are met — devices added, filtered, credentials configured, and relations assigned — you will have the necessary setup to create and run configuration tasks in the Configuration Manager feature.

---

This preparation ensures secure, targeted, and efficient management of device configurations within your network.