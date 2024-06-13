---
product: campaign
title: About Adobe Experience Cloud Triggers
description: Get started with Adobe Experience Cloud Triggers implementation
feature: Triggers
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
---
# Work with Campaign and Experience Cloud Triggers{#about-adobe-experience-triggers}

[!DNL Triggers] is an integration between Adobe Campaign and Adobe Analytics using the pipeline. The pipeline retrieves users' actions or triggers from your website. A cart abandonment is an example of trigger. Triggers are processed in Adobe Campaign to send emails in near real time.

>[!CAUTION]
>
>This capability is not available out of the box as part of the product. For this implementation, work with your Adobe representative / Customer Care. You will then be able to follow the steps detailed in this [page](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] run marketing actions within a short range of time following a user's action. The typical response time is less than one hour.

It allows for more agile integrations since the configuration is minimal and a third party is not involved.
It also supports high volumes of traffic without impacting the performance of marketing activities. As an example, the integration can process a million triggers per hour.

![](assets/do-not-localize/book.png) Discover how to [create an Experience Cloud trigger](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) and identify, define, and monitor critical consumer behaviors.

## [!DNL Triggers] architecture {#triggers-architecture}

The [!DNL pipelined] process is always running on the Adobe Campaign marketing server. It connects to the pipeline, retrieves the events, and processes them immediately.

![](assets/triggers_2.png)

The [!DNL pipelined] process logs in to the Experience Cloud using an authentication service and sends a private key. The authentication service returns a token. The token is used to authenticate when retrieving the events.

## Prerequisites {#adobe-io-prerequisites}

Before starting this implementation, please check you have:

* a valid **Organization identifier**: the Organization ID is the unique identifier within the Adobe Experience Cloud, used for example for the VisitorID service and the IMS Single-Sign On (SSO). [Learn more](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html)
* a **Developer access** to your Organization. The System administrator of the organization needs to follow the **Add developers to a single product profile** procedure detailed [in this page](https://helpx.adobe.com/enterprise/using/manage-developers.html) to provide developer access for the `Analytics - {tenantID}` Product Profile of the Adobe Analytics Product associated with Triggers.

## Implementation steps {#implement}

To implement Campaign and Experience Cloud Triggers, follow the steps below:

1. Create an OAuth project. [Learn more](oauth-technical-account.md#oauth-service)

1. Add your OAuth project credentials in Adobe Campaign. [Learn more](oauth-technical-account.md#add-credentials)

1. Update the authentication type to the Developer console project in the configuration file **config-<&nbsp;instance-name&nbsp;>.xml** as follows:

    ```
    <pipelined ... authType="imsJwtToken"  ... />
    ```

    Then, run a `config -reload` and a restart of the [!DNL pipelined] for the changes to be taken into account.

