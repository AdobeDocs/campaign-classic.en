---
title: Troubleshooting
seo-title: Troubleshooting
description: Troubleshooting
seo-description: 
page-status-flag: never-activated
uuid: 86187401-565c-4960-b752-37dedbc3d2b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 89f6348e-b695-4960-9d8a-9c1857e29617
index: y
internal: n
snippet: y
---

# Troubleshooting{#troubleshooting}

In case of error, make sure that the following elements are correctly configured:

* **External accounts**

  In **Administration > Platform > External accounts**, make sure that the following external SFTP accounts are correctly configured. The mentioned SFTP servers should have been configured in Adobe Experience Cloud by your consultant.

    * **importSharedAudience**: SFTP account dedicated to importing audiences.
    * **exportSharedAudience**: SFTP account dedicated to exporting audiences.

* **AMC Data source**

  In **Administration > Platform > AMC Data sources**, check that the AMC Data source is set properly.

It can occur that some data are missing when sharing an audience via People core service or when importing an audience. Only records of which the ID ('Visitor ID' or 'Declared ID') was able to be reconciled with the profile dimension are transferred. IDs from the People core service segments that are not recognized by Adobe Campaign are not imported.
