---
product: campaign
title: Work with Adobe Campaign and Adobe Analytics
description: Work with Adobe Campaign and Adobe Analytics
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
TQID: https://experienceleague.adobe.com/YuvP0m31wL-WlocUXU3rWovOiwLiA5XrEsnBLlW3nY8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Adobe Analytics integration (Campaign)
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Adobe Experience Manager integration (Campaign)
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Adobe Experience Platform integration (Campaign)
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Adobe Target integration (Campaign)
---
# Work with Adobe Campaign and Adobe Analytics {#adobe-analytics-connector-gs}

Adobe Analytics Connector allows Adobe Campaign and Adobe Analytics interact through the **[!UICONTROL Web Analytics connectors]** package. It forwards data to Adobe Campaign in the form of segments concerning user behavior following a campaign. Conversely, it sends indicators and attributes of campaigns delivered by Adobe Campaign to Adobe Analytics.

## Guardrails and prerequisites {#adobe-analytics-connector-guardrails}

Before starting working with the Adobe Campaign-Adobe Analytics connector, consider the following guardrails and prerequisites.

* For this integration, connecting to Campaign with Adobe Identity Management System (IMS) is required. [Learn more](../../integrations/using/about-adobe-id.md).

* Adobe Analytics Connector is not compatible with Transactional messaging (Message Center).

* The Web Analytics connector add-on must be installed on your environment, through the dedicated package.

    * For Hybrid and On-premise implementations, make sure to follow the provisioning steps detailed in this [page](adobe-analytics-provisioning.md).
    * As a Hoster or Managed Cloud Services user, contact Adobe to connect Campaign with Adobe Experience Cloud services and solutions. 


## Configuration and usage {#adobe-analytics-connector-usage}

To enable this integration, you must create your Adobe technical account as detailed in [this page](oauth-technical-account.md).

Learn how to work with Adobe Campaign and Adobe Analytics in [Adobe Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.
