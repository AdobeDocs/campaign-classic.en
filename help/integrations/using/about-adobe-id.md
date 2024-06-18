---
product: campaign
title: Use your Adobe ID to connect to Adobe Campaign
description: Learn more about Adobe IMS implementation in Adobe Campaign
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
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
