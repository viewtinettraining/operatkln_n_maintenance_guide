---
reusableId: 63
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'GUI Logging for AD Users'
id: 9CB-AQAQ-DQS-CXU
slug: gui-logging-for-ad-users
isVisible: true
lastUpdated: '2025-10-15 15:40:05'
---
# **<span align="center">GUI logging for AD Users</span>**

<br />

Once the Active Directory integration is complete, along with the creation and mapping of roles, you can perform the respective logging test. Users must be created in Active Directory and belong to their corresponding group. The steps are as follows:

<br />

1.  <span align="justify">Please visit the Viewtinet management IP address in your browser, using port 4200 (insecure) or 4201 (secure).</span>
2.  Enter the username and password
3.  <span align="justify">If the configuration is correct, Viewtinet will authenticate the user and display the options according to the user's role</span>

<br />

<span align="justify">For the purposes of this guide, three users have been created and assigned to each of the groups</span>

<br />

<table><tbody><tr><td><p><strong><span align="center">User</span></strong></p></td><td><p><strong><span align="center">Active Directory Group</span></strong></p></td><td><p><strong><span align="center">Viewtinet Role</span></strong></p></td><td><p><strong><span align="center">Behavior</span></strong></p></td></tr><tr><td><p><span align="center">user_admin_viewtinet</span></p></td><td><p><span align="center">Admins_Viewtinet</span></p></td><td><p><span align="center">Admin_Viewtinet</span></p></td><td><p><span align="center">Full Acess to Viewtimanager &amp; Viewtisight</span></p></td></tr><tr><td><p><span align="center">user_vs_viewtinet</span></p></td><td><p><span align="center">Viewtisight_Viewtinet</span></p></td><td><p><span align="center">Viewtisight_Viewtinet</span></p></td><td><p>Full Access to Viewtisight &amp; Denied Access to Viewtimanager</p></td></tr><tr><td><p><span align="center">user_ro_viewtinet</span></p></td><td><p>ReadOnly_Viewtinet</p></td><td><p>ReadOnly_Viewtinet</p></td><td><p>Restricted Access to Viewtisight (No dashboard Composer) &amp; Denied Access to Viewtimanager</p></td></tr></tbody></table>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/I17r1lREoUQtRawS8SHK.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/jcK2QHiZKSXbgj9UVl66.png" align="center"></figure>

From the 'Profile' option in the 'Help' button in Viewtisight, you will be able to see the user

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/KShGBk8obnYJohe30mOW.png" align="center"></figure>

<br />

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/67xdZpSTXnATYX4X4b8L.png" align="center"></figure>

Full Access to Viewtisight & Viewtimanager

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/0h3kPAa5wjIMY584gWQ3.png"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/paqDUPSynt2tfKwzAR31.png"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/fmvXkOo9YHfidivgnuit.png" align="center"></figure>

<br />

Full Access to Viewtisight:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/Hzq276bMwR9CXZWaTN7l.png" align="center"></figure>

Viewtimanager Access Denied:

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/an7TolCCCey15voheahi.png"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/lpRmvZfdbKBvOz6MqnOJ.png" align="center"></figure>

<br />

Restricted access to Viewtisight without options for creating dashboards, metrics, etc.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/knXaRhkhYqh66S4j5vz3.png" align="center"></figure>

Viewtimanager Access Denied:

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/tkdKpHUg05hny8QACXsg.png"></figure>

<br />