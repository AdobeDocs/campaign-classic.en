---
product: campaign
title: Inbox rendering in Campaign
description: Learn how to capture email renderings and make them available in a dedicated report
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
role: User
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
TQID: 'https://experienceleague.adobe.com/d0fFXi4Ma-PwY8vsSBOmvbhRD4631kUoagNXlf4Rmek'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: 2317b1ea-6db4-58c7-851f-717a69c0f5c0
    internal-label: Inbox Rendering
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
  - id: aef0b685-fc31-54d4-b831-a87fdb9d69de
    internal-label: Email Rendering
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Inbox rendering{#inbox-rendering}

Adobe Campaign leverages the [Litmus](https://litmus.com/email-testing) web-based email testing solution to capture email renderings and make them available in a dedicated report.

>[!NOTE]
>
>As part of the transition from Campaign v7 to v8, the Campaign Classic documentation set has been streamlined and reorganized. Common features are now available exclusively in the Campaign v8 documentation set. To learn more about inbox rendering, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}.
>
>[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}

## Activating Inbox rendering {#activating-inbox-rendering}

[!BADGE On-premise & Hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"}

For hosted and hybrid clients, Inbox rendering is configured on your instance by Adobe technical support and consultants. For more information, contact your Adobe Account executive.

For on-premise installations, follow the steps below to configure Inbox rendering.

1. Install the **[!UICONTROL Inbox rendering (IR)]** package via the **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. For more on this, see [Installing Campaign Classic standard packages](../../installation/using/installing-campaign-standard-packages.md).
1. Configure an external account of the HTTP type via the **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** node. For more on this, see [Creating an external account](../../installation/using/external-accounts.md#creating-an-external-account).
1. Set the external account parameters as follows:
    * **[!UICONTROL Label]**: Deliverability server info
    * **[!UICONTROL Internal name]**: deliverabilityInstance
    * **[!UICONTROL Type]**: HTTP
    * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
    * **[!UICONTROL Encryption]**: None
    * Check the **[!UICONTROL Enabled]** option.
    
    ![](assets/s_tn_inbox_rendering_external-account.png)
 
1. Go to the **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** node. Search for the **[!UICONTROL DmRendering_cuid]** option and contact support to get your delivery reports identifier that needs to be copied to the **[!UICONTROL Value (text)]** field.
1. Edit the **serverConf.xml** file to allow a call to the Litmus server. Add the following line to the `<urlPermission>` section:

    ```
    <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
    ```

1. Reload the configuration using the following command:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>You may have to log out from the console and log back in to be able to use Inbox rendering.
