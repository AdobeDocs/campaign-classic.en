---
title: About Campaign integrations
description: Learn about functional integrations available between the current version of Adobe Campaign and [Adobe Experience Cloud solutions
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
index: y
internal: n
snippet: y
---

# About Campaign integrations {#about-campaign-integrations}

Adobe Experience Cloud is a comprehensive set of best-in-class, integrated solutions built on a common data platform with a common set of powerful core services.

Learn about functional integrations available between Adobe Campaign and [Adobe Experience Cloud solutions](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) and [core services](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html). You can then modernize your solution implementations and implement the Experience Cloud so that you can use features like customer attributes and audiences.

The full list of Adobe solutions and core services which can be integrated with Adobe Campaign, as well as associated documentation, is available in [this section](#experience-cloud-integrations).

   ![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>Most of these integrations require to log in via an Adobe ID (IMS). For more on this implementation, refer to [this page](../../integrations/using/about-adobe-id.md).
>
>Note that IMS implementation is a complex process, which can be long. It is strictly reserved to the Adobe technical administrators.

## Linking your solutions {#working-with-experience-cloud-solutions}

Depending on your environment, several solutions can be linked to Adobe Experience Cloud. They are linked as Organizations. An **organization** is the entity that enables an administrator to configure groups and users, and to control single sign-on in the Experience Cloud. The organization functions like a log-in company that spans all the Experience Cloud products and solutions. Most often, an organization is your company name. However, a company can have many organizations.

Organization management and linking Adobe Experience Cloud accounts are detailed in the [Adobe Experience Cloud help portal](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html).

>[!CAUTION]
>
>When newly installing Adobe Campaign or integrating an existing installation with Adobe Experience Cloud, the [Experience Cloud ID Service](https://marketing.adobe.com/resources/help/en_US/mcvid/) is enabled. This service replaces the permanent cookie used first and foremost by Adobe Campaign for its tracking functionalities.
>
>A unique visitor ID will then be assigned to recipients generating tracking logs. This ID will be saved in the **[!UICONTROL Requester UUID (@sourceID)]** field of the **[!UICONTROL nms:trackingLogRcp]** table. The tracking data of recipients who existed before the visitor ID service was implemented will therefore no longer be usable.
>
>The ID will then be recognized by the other Adobe Experience Cloud solutions with the same [CNAME](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_cname.html).

## Experience Cloud integrations {#experience-cloud-integrations}

The following table provides access to available Experience Cloud integration documentation.

<table> 
 <thead> 
  <tr> 
   <th> Solution &amp; Core services<br /> </th> 
   <th> Use cases<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform</strong><br /> </td> 
   <td> The integration between Adobe Campaign and Adobe Real-time Customer Data Platform allows you to share segments data and import audiences to Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Learn more</a> about Campaign - Adobe Real-time Customer Data Platform integration.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> Allows you to connect to Adobe Campaign with the same Adobe ID as for the other Adobe Experience Cloud solutions.<br /> An Adobe ID has to be used to log in in order to use certain functionalities linked to the Adobe Experience Cloud integrations, particularly Core Services.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Learn more</a> about implementing Adobe ID with Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Allows you to create email contents or forms mapped to the Adobe Campaign database directly in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Learn more</a> about Adobe Campaign - Adobe Experience Manager integration.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Allows you to insert images that are dynamically computed by <strong>Adobe Target</strong> when the email created and sent by Adobe Campaign is opened.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Learn more</a> about Adobe Campaign - Adobe Target integration.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People core service</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Allows you to share audiences between the Adobe Experience Cloud solutions and core that you use.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Learn more</a> about Adobe Campaign - People core service and Adobe Audience Manager integrations.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets core service</strong><br /> </td> 
   <td> Allows you to insert assets from your Adobe Experience Cloud library into emails and landing pages created in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Learn more</a> about Adobe Campaign - Assets core service integration</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Allows you to insert assets from your <strong>AEM Assets</strong> library into emails and landing pages created in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Learn more</a> about Adobe Campaign - AEM Assets integration.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> Integration between <strong>Triggers core service</strong> and Adobe Campaign allows you to send personalized emails to your customers as a reaction to specific behaviors that are tracked on your website by Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html">Learn more</a> about Adobe Campaign - Experience Cloud triggers integration.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Data Connectors</strong><br /> </td> 
   <td> <strong>Data connectors</strong> (previously known as Adobe Genesis) allows Adobe Campaign and Adobe Analytics interact through segments concerning user behavior following an email campaign. Conversely, it sends indicators and attributes of email campaigns delivered by Adobe Campaign to Adobe Analytics - Data connector.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Learn more</a> about Campaign - Data Connectors integration.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Campaign Standard</strong> (Prime offering)<br /> </td> 
   <td> Allows you to replicate data to <strong>Campaign Standard</strong>, uniting the best of both applications. Campaign Classic v7 has advanced tools to manage the primary marketing database. The data replication from Campaign Classic v7 allows Campaign Standard to leverage the rich data in a user-friendly environment.<br /><p> <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Learn more</a> about Adobe Campaign Classic - Adobe Campaign Standard integration.</p><br /></td> 
  </tr> 
 </tbody> 
</table>

