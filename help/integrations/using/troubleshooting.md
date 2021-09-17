---
product: campaign
title: Troubleshooting
description: Troubleshooting
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
---
# Troubleshooting{#troubleshooting}

![](../../assets/common.svg)

In case of error, make sure that the following elements are correctly configured:

* **External accounts**

  In **[!UICONTROL Administration > Platform > External accounts]**, make sure that the following external SFTP accounts are correctly configured. The mentioned SFTP servers should have been configured in Adobe Experience Cloud by your consultant.

    * **[!UICONTROL importSharedAudience]** : SFTP account dedicated to importing audiences.
    * **[!UICONTROL exportSharedAudience]** : SFTP account dedicated to exporting audiences.

* **AMC Data source**

  In **[!UICONTROL Administration > Platform > AMC Data sources]**, check that the AMC Data source is set properly.

It can occur that some data are missing when sharing an audience via People core service or when importing an audience. Only records of which the ID ('Visitor ID' or 'Declared ID') was able to be reconciled with the profile dimension are transferred. IDs from the People core service segments that are not recognized by Adobe Campaign are not imported.
