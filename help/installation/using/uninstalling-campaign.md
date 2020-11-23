---
solution: Campaign Classic
product: campaign
title: Uninstalling Campaign
description: Learn how to uninstall Campaign
audience: installation
content-type: reference
topic-tags: appendices
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
