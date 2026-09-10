---
reusableId: 70
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Installation step1 '
id: SM3-711J-KFE-QS7
slug: installation-step1
isVisible: true
isSearchable: true
lastUpdated: '2026-03-10 15:51:34'
---
# <span align="center">Installation Step 1</span>

<br />

<div class="sd-callout" data-callout-type="alert">Internet access is mandatory during the installation process, as all the libraries and tools needed for the execution of Viewtinet will be installed</div>

<div class="sd-callout" data-callout-type="info">The installation is carried out in 3 steps: deployment, installation of dependencies, loading of images, and configuration</div>

The first step is to execute the deployment script:

```bash
./deploy.sh
```

Upon execution, you will see the following prompts and progress:

```bash
viewtinet@dante:~$ ./deploy.sh
Uncompressing and deploying software... This may take a while. Please wait.
Please write the bundle passphrase:
```

<div class="sd-callout" data-callout-type="info">At this point, enter the <strong>passphrase</strong> that was sent along with your bundle.</div>

After entering the passphrase, the system will proceed with the deployment. At the end of the process, you will see an output similar to the one shown below:

```bash
Deploying current software
Moving deb file /home/viewtinet/_build/viewtinet-builder_6.3.5.5767_all.deb to /opt/vn/software/viewtinet-builder_6.3.5.5767_all.deb
Moving module dependencies to /opt/vn/software/dependencies
Moving module dhyana to /opt/vn/software/dhyana
Moving module license-checker to /opt/vn/software/license-checker
Moving module release-notes to /opt/vn/software/release-notes
Moving module third-party to /opt/vn/software/third-party
Moving module viewtiauth to /opt/vn/software/viewtiauth
Moving module viewticore to /opt/vn/software/viewticore
Moving module viewtimanager to /opt/vn/software/viewtimanager
Moving module viewtimon to /opt/vn/software/viewtimon
Moving module viewtisight to /opt/vn/software/viewtisight
Installing deb file
Selecting previously unselected package viewtinet-builder.
(Reading database ... 94807 files and directories currently installed.)
Preparing to unpack .../viewtinet-builder_6.3.5.5767_all.deb ...
Unpacking viewtinet-builder (6.3.5.5767) ...
Setting up viewtinet-builder (6.3.5.5767) ...
INFO: Generating application-level RSA key pair... writing RSA key
viewtinet@dante:~$
```

<br />