---
product: campaign
title: Troubleshooting
description: Troubleshooting
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
TQID: 'https://experienceleague.adobe.com/4de9cxyepP-REa2OTWniBFWInphApeUM79sZuFGcynI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Experience Manager integration
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Experience Platform integration
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Target integration
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences
  - id: a8512b64-d668-4084-b4f0-34baa899e306
    internal-label: People Core Service integration
  - id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875f
    internal-label: Troubleshooting
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Troubleshooting{#troubleshooting}

 

In case of error, make sure that the following elements are correctly configured:

* **External accounts**

  In **[!UICONTROL Administration > Platform > External accounts]**, make sure that the following external SFTP accounts are correctly configured. The mentioned SFTP servers should have been configured in Adobe Experience Cloud by your consultant.

    * **[!UICONTROL importSharedAudience]** : SFTP account dedicated to importing audiences.
    * **[!UICONTROL exportSharedAudience]** : SFTP account dedicated to exporting audiences.

* **AMC Data source**

  In **[!UICONTROL Administration > Platform > AMC Data sources]**, check that the AMC Data source is set properly.

It can occur that some data are missing when sharing an audience via Experience Cloud Audience or when importing an audience. Only records of which the ID ('Visitor ID' or 'Declared ID') was able to be reconciled with the profile dimension are transferred. IDs from the segments that are not recognized by Adobe Campaign are not imported.
