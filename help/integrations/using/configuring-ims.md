---
product: campaign
title: Configuring IMS
description: Learn how to connect via an Adobe ID
feature: Configuration
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
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
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Experience Manager integration
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Experience Platform integration
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Target integration
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
---
# Configuring IMS{#configuring-ims}

>[!IMPORTANT]
>
>As a Campaign hosted or managed services user, your Adobe IMS implementation is owned by Adobe. Steps decribed below only apply to on-premise and hybrid customers.
> Adobe IMS implementation must only be performed by Adobe technical administrators. Contact your Adobe representative to start the implementation process.

## Prerequisites {#prerequisites}

* You must have an Adobe Experience Cloud Organization name and ID. To find your Organization ID, refer to [this page](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html){_blank}.
* You have to add users in the Experience Cloud. For more on this, refer to [this page](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>Make sure that your users are linked to the Adobe Experience Cloud groups that will be synced with Adobe Campaign. [Learn more](#configuring-the-external-account).

## Updating the console {#updating-the-console}

To use this functionality, it is imperative that you install the latest version of the Client console.

## Installing the package {#installing-the-package}

You must install the built-in **[!UICONTROL Integration with the Adobe Experience Cloud]** package. Installing an integration package is the same as installing a standard package, which is detailed in [this page](../../installation/using/installing-campaign-standard-packages.md). 

![](assets/ims_6.png)

## Configuring the external account {#configuring-the-external-account}

Configure the **Adobe Experience Cloud** external account in **[!UICONTROL Administration > Platform > External accounts]**.

![](assets/ims_5.png)

Enter the following information:

* Connection information for the IMS server used (ID and secret). This information is provided by Adobe Customer Care team. For more information, refer to the [FAQ for Adobe Experience Cloud Administrators](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

  The **[!UICONTROL Callback server]** address must be specified in **https**. This field corresponds to the access URL of your Adobe Campaign instance.

* Organization ID: to find your organization ID, refer to [this page](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html){_blank}.

* Association mask: this field allows you to define the syntax which will allow configuration names in Enterprise Dashboard to be synced with the groups in Adobe Campaign. If you use the syntax "Campaign - tenant_id - (.&#42;)", the security group created in Adobe Campaign will be linked to the configuration name "Campaign - tenant_id - internal_name" in Enterprise Dashboard.

* Adobe Experience Cloud connection information, which is the name of the Adobe Experience Cloud Tenant.
