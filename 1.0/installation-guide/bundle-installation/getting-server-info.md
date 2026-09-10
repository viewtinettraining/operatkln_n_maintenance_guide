---
reusableId: 73
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Getting server info'
id: I7G-VSW8-J9P-8HE
slug: getting-server-info
isVisible: true
lastUpdated: '2025-10-15 09:34:18'
---
# **<span align="center">Getting the Server INFO</span>**

To issue a valid license, Viewtinet requires a unique hardware identifier specific to your machine. This unique footprint ensures that your Viewtinet installation is securely tied to your designated environment (whether it is a physical appliance, virtual machine, or COTS server). 

This identifier is automatically generated during the previous steps and is stored in the following file path on your server:
`/opt/vn/viewtimanager/var/server-info.txt`

### **How to Obtain Your License**

1. **Download the Identifier File:** Use any SCP client (such as WinSCP for Windows, or the native `scp` command on Linux/macOS) to connect to your server and download the `server-info.txt` file to your local computer.
2. **Send it to Viewtinet:** Attach the downloaded file in an email and send it to your assigned Viewtinet representative or support engineer.
3. **Receive Your License:** After processing your unique identifier, the Viewtinet team will reply with your official license file (in `.key` format), which you will use in the upcoming steps.

<br />

<br />

<br />