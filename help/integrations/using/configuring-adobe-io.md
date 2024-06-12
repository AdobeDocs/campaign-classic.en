---
product: campaign
title: Configuring Developer Console for Adobe Experience Cloud Triggers
description: Learn how to configure Developer Console Adobe Experience Cloud Triggers
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
---
# Configuring Developer Console for Adobe Experience Cloud Triggers {#configuring-adobe-io}

<!--
>[!CAUTION]
>
>If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O as described below**. 
>Note that during this move to [!DNL Adobe I/O], some incoming triggers may be lost.
>
>Legacy oAuth authentication mode with Campaign has been retired on **October 20, 2021**. Hosted environments benefit from an extension until **May 25, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to **May 2022**. You must [provide the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
-->

## Prerequisites {#adobe-io-prerequisites}

<!--
This integration only applies starting **Campaign Classic 20.2.4 and above, 19.1.8 and Gold Standard 11 releases**.
-->

Before starting this implementation, please check you have:

* a valid **Organization identifier**: the Organization ID is the unique identifier within the Adobe Experience Cloud, used for example for the VisitorID service and the IMS Single-Sign On (SSO). [Learn more](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html)
* a **Developer access** to your Organization. The System administrator of the organization needs to follow the **Add developers to a single product profile** procedure detailed [in this page](https://helpx.adobe.com/enterprise/using/manage-developers.html) to provide developer access for the `Analytics - {tenantID}` Product Profile of the Adobe Analytics Product associated with Triggers.

## Step 1: Create/update Oauth project {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> The Service Account (JWT) credential is being deprecated by Adobe, Campaign integrations with Adobe solutions and apps must now rely on OAuth Server-to-Server credential. </br>
>
> * If you have implemented inbound integrations with Campaign, you must migrate your Technical Account as detailed in [this documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Existing Service Account (JWT) credentials will continue to work until January 27, 2025.</br>
>
> * If you have implemented outbound integrations, such as Campaign-Analytics integration or Experience Cloud Triggers integration, they will continue to work until until January 27, 2025. However, before that date, you must upgrade your Campaign environment to v7.4.1 and migrate your Technical Account to oAuth. 

To proceed with configuring your Adobe Analytics connector, access the Adobe Developer console and create your OAuth Server-to-Server project.

Refer to [this page](oauth-technical-account.md#oauth-service) for the detailed documentation.

## Step 2: Add the project credentials in Adobe Campaign {#add-credentials-campaign}

Follow the steps detailed in [this page](oauth-technical-account.md#add-credentials) to add your OAuth project credentials in Adobe Campaign.

## Step 3: Update pipelined tag {#update-pipelined-tag}

To update [!DNL pipelined] tag, you need to update the authentication type to the Developer console project in the configuration file **config-<&nbsp;instance-name&nbsp;>.xml** as follows:

```
<pipelined ... authType="imsJwtToken"  ... />
```

Then, run a `config -reload` and a restart of the [!DNL pipelined] for the changes to be taken into account.
