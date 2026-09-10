---
reusableId: 81
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'IPMI IP Address Configuration'
id: GTF-VP32-JNO-C00
slug: ipmi-ip-address-configuration
isVisible: true
lastUpdated: '2025-10-15 10:36:15'
---
# **<span align="center">IPMI IP Address Configuration</span>**

<span align="justify">The Intelligent Platform Management Interface (IPMI) provides remote access to multiple users at different locations for networking. It also allows a system admin­istrator to monitor system health and manage computer events remotely. IPMI operates independently from the operating system. Provides remote access to multiple users from different locations for system maintenance and management.</span>

This section describes the steps to configure the IP address of the IPMI interface. To complete these steps, you will need to connect a keyboard and monitor to your appliance (list of ports in the previous chapter, link), power on the appliance, and when the SuperMicro message appears, as shown in the image below, you must press the DEL key

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/dBYEmjKmvVdmmBMRcFD6.png"></figure>

In the next screen, you will need to press the &lt;DEL&gt; key again.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/zXcW0E7FveIE23iUXAr5.png"></figure>

The above will allow you to enter the appliance's Setup Utility. To access the IPMI configuration, use the right arrow key '-&gt;' to navigate to the IPMI menu, as shown in the images

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/eMrsZet3rgH8KXhUqSEI.png"></figure>

<br />

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/a8YHwpY94NBJwUmyRqpv.png"></figure>

Using the down arrow key on the keyboard, select the 'Update IPMI LAN Configuration' menu and press the &lt;Enter&gt; key to change the configuration.

From the pop-up menu, select 'Yes'

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/xgnecpAv56dTAspkzmT6.png"></figure>

Use the down arrow key to select each configuration parameter (Station IP Address, Subnet Mask, Gateway IP Address) to configure it according to your network settings

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/ZHCKdxWiIQjNd7lVFkkO.png"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/gAUHg17U5pzXvR52BJPN.png"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/FIqKuIBzsQj6bLgXpZs1.png"></figure>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/AGCp1sU4oGJbaxNYKF7o.png"></figure>

After configuring the network parameters, to confirm the changes, you will need to press the &lt;F4&gt; key

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/Rk34fGvJ6LICCghb7wT6.png"></figure>

To finalize, select the 'Yes' option from the pop-up menu

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/6HHddNJPpu8amwjAb2Ev.png"></figure>

Now the appliance will go through a reboot process, and you will be able to access the IPMI tool via the web. Please remember to physically connect the IPMI port to your network in order to access the web-based IP tool (see the following [link](http:#?target=2PL-6EPV-GGQ-5D7#standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) )

<br />

<br />