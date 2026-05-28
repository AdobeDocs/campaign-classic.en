---
product: campaign
title: Use your Adobe ID to connect to Adobe Campaign
description: Learn more about Adobe IMS implementation in Adobe Campaign
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
TQID: https://experienceleague.adobe.com/i9Ncu86b4PZaAY6yROb-6kUdOgjbYNV1nE0Rj-Jb-OY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Adobe Analytics integration
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Adobe Experience Manager integration
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Adobe Experience Platform integration
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Adobe Target integration
---
# About Adobe ID {#about-adobe-id}

Adobe Identity Management System (IMS) helps admins create and manage user's access to applications and services. For more information on the different types of Adobe IDs, refer to [this page](https://helpx.adobe.com/enterprise/using/identity.html).

Campaign users can connect to the Adobe Campaign console using their Adobe ID, instead of the [native user/password authentication](../../platform/using/access-management-operators.md). This implementation provides the following advantages:

* The same ID can be used for all Experience Cloud solutions.
* The connection is kept when using Adobe Campaign with different integrations.
* Securer password management policy than native login/password.
* Use of Federated ID accounts (external ID provider).

>[!IMPORTANT]
>
> Note that in Campaign v8, connecting with user/password (aka native authentication) is not allowed. **Adobe recommends to perform this migration starting Campaign v7.3.5 to be able to migrate smoothly to Campaign v8.** 
>
>Learn how to migrate to Adobe IMS in [this section](../../technotes/using/ac-ims.md).
>


<!--
>[!IMPORTANT]
>
>If you are connecting to Campaign through Adobe Identity Service (IMS), you need to upgrade to the latest build to be able to connect to Campaign after **June 30, 2021**. This upgrade is mandatory for both Campaign server and client console. 
>
>Depending on your current version, you must upgrade to one of the following releases: 
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[Learn more about IMS updates](../../technotes/using/ims-updates.md)
-->

## More resources

| Useful pages | Additional resources |
|---|---|
| [Configuring IMS](../../integrations/using/configuring-ims.md) | [Experience Cloud FAQ](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html) |
| [Implementing IMS](../../integrations/using/implementing-ims.md) | [Access management](../../platform/using/access-management.md) |
| [IMS Troubleshooting](../../integrations/using/ims-troubleshooting.md) |  [Installing Campaign packages](../../installation/using/installing-campaign-standard-packages.md) |
