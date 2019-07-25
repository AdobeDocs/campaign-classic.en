---
title: Uninstalling Campaign
seo-title: Uninstalling Campaign
description: Uninstalling Campaign
seo-description: 
page-status-flag: never-activated
uuid: fe36ba48-9008-44af-9a93-c55a09e7d476
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: d9e19b99-445a-476b-ba87-ee662f4c822d
index: y
internal: n
snippet: y
---

# Uninstalling Campaign{#uninstalling-campaign}

>[!CAUTION]
>
>These procedures will uninstall permanently Adobe Campaign. All data will be lost.

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows:**

Refer to this [page](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Don't forget to remove the Campaign installation folder.
