---
solution: Campaign Classic
product: campaign
title: Temporary files
description: Temporary files
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
---
# Temporary files{#temporary-files}

Error messages such as the following may display (particularly in delivery logs) when the system is put into production:

*Unable to rename file '/tmp/tmp0000.tmp' to /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)*

The cause is as follows:

Adobe Campaign generates temporary files under **/tmp**, and then renames them to move them to **/usr/local/neolane/nl6/var**. This error occurs when both folders (**/tmp** and **/usr/local/neolane/nl6/var**, which is in fact a symbolic link to **/var/nl6**) correspond to different devices. The **df** command is used for verification.

To correct this problem, the temporary files must be generated in the same device as the destination.

For example, execute the following:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

Then add:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
