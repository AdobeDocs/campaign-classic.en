---
title: About Adobe Experience Manager
seo-title: About Adobe Experience Manager
description: About Adobe Experience Manager
seo-description: 
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
---

# About Adobe Experience Cloud Triggers{#about-adobe-experience-triggers}

[!DNL Triggers] is an integration between Adobe Campaign and Adobe Analytics using the pipeline. The pipeline retrieves users' actions or triggers from your website. A cart abandonment is an example of trigger. Triggers are processed in Adobe Campaign to send emails in near real time.

[!DNL Triggers] run marketing actions within a short range of time following a user’s action. The typical response time is less than one hour.

It allows for more agile integrations since the configuration is minimal and a third party is not involved.
It also supports high volumes of traffic without impacting the performance of marketing activities. As an example, the integration can process a million triggers per hour.

## [!DNL Triggers] architecture {#triggers-architecture}

The [!DNL pipelined] process is always running on the Adobe Campaign marketing server. It connects to the pipeline, retrieves the events, and processes them immediately.

![](assets/triggers_2.png)

The [!DNL pipelined] process logs in to the Experience Cloud using an authentication service and sends a private key. The authentication service returns a token. The token is used to authenticate when retrieving the events.

For more information on authentication, refer to this [page](../../integrations/using/configuring-adobe-io.md).

>[!NOTE]
>
>Further processing of events is done as part of the ACX Package provided outside the default implementation. Received event is processed immediately using JavaScript code. It is saved into a database table with no further processing in real time. The triggers are used for targeting by a campaign workflow which sends emails. The campaign is set up so the customer that has triggered the event will receive an email.
