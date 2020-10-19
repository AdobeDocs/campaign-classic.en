---
title: Temporary files
seo-title: Temporary files
description: Temporary files
seo-description: 
page-status-flag: never-activated
uuid: ae7ec619-e93f-41fb-ba7c-fcbcf4cba84f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f18237b0-ef54-46a6-9c14-34b038f9de18
---

# Temporary files{#temporary-files}

If error messages such as the following appear (particularly in delivery logs) when the system is put into production:

**Unable to rename file '/tmp/tmp0000.tmp' to /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)**

The cause is as follows:

Adobe Campaign generates temporary files under **/tmp**, and then renames them to move them to **/usr/local/neolane/nl6/var**. This error occurs when both folders (**/tmp** and **/usr/local/neolane/nl6/var**, which is in fact a symbolic link to **/var/nl6**) correspond to different devices. The **df** command is used for verification.

To correct this problem, the temporary files must be generated in the same device as the destination. For example, by executing:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

and then adding:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

