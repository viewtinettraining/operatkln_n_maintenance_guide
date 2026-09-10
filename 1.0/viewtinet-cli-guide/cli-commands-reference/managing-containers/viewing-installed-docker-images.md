---
reusableId: 49
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewing Installed Docker Images'
id: R1C-WGZV-8OK-AI9
slug: viewing-installed-docker-images
isVisible: true
lastUpdated: '2025-10-15 16:02:19'
---
# **<span align="center">Viewing Installed Docker Images</span>**

<br />

Viewtinet provides another helpful CLI alias: `di`, which is shorthand for:

```bash
sudo docker image ls
```

This command lists all Docker images currently installed on the system. It's particularly useful for:

-   Verifying the **exact version** of each Viewtinet component installed (e.g., `viewtinet/viewtisight:6.3.5`)
-   Checking the **creation date** of the image, which helps determine how recently it was updated or rebuilt
-   Comparing images across environments for consistency
-   **Reporting** image versions to the Viewtinet support team when opening a support ticket

To use it, simply run:

```bash
$ di
```

You will see output similar to the following:

```
REPOSITORY                        TAG       IMAGE ID       CREATED         SIZE
viewtinet/viewtisight-frontend   6.3.5     a1b2c3d4e5f6   23 hours ago    400MB
viewtinet/viewtiauth-backend     6.3.5     b2c3d4e5f6g7   23 hours ago    350MB
viewtinet/viewticore             6.3.5     c3d4e5f6g7h8   23 hours ago    780MB
```

> **Tip**: Always include the output of `di` when submitting a support request. It allows the support team to confirm you are running the correct and most recent versions of the components involved.

This command complements `dps` by offering a version-level view of the deployed modules, helping you keep track of the platform’s health and update history.

<br />

## **Checking the Installed Viewtinet Version**

In addition to monitoring containers and images, it is often necessary to check the installed version of the Viewtinet platform itself. This can be done using the following command:

```bash
dpkg --list | grep viewtinet
```

This command queries the Debian package manager to list any installed packages that include `viewtinet` in their name. A typical output looks like this:

<br />

```
ii  viewtinet-builder     6.3.3200     all     viewtinet-builder
```

This output indicates that the system is running version `6.3.3200` of the `viewtinet-builder` package.

#### Why this is useful

-   It allows administrators to **confirm the exact installed version** of the platform, independent of the Docker image tags.
-   It is **essential for support purposes**, as the Viewtinet support team may request this information to troubleshoot issues or verify compatibility.
-   It helps identify if the environment is running a **stable or outdated build**, especially before performing upgrades or patches.

> **Tip**: Include the result of this command in any support request to ensure faster diagnosis and resolution.

<br />