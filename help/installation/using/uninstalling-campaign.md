---
title: Uninstalling Campaign
seo-title: Uninstalling Campaign
description: Uninstalling Campaign
seo-description: 
page-status-flag: never-activated
uuid: 2abcac4e-db12-467d-aac3-849c65ecf0c4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 01e5dfaa-5049-4b07-8766-c390d8c7cef3
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
