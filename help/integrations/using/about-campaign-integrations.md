---
product: campaign
title: About Campaign integrations
description: Use other Adobe solutions and combine their different capabilities with Campaign.
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
---
# Get started with Adobe Campaign integrations {#about-campaign-integrations}

Adobe Experience Cloud is a comprehensive set of best-in-class, integrated solutions built on a common data platform with a common set of powerful core services.

Learn about functional integrations available between Adobe Campaign and [Adobe Experience Cloud solutions](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html) and [core services](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html). You can then modernize your solution implementations and implement the Experience Cloud so that you can use features like customer attributes and audiences.

   ![](assets/ExCloud-solutions.png)

The full list of Adobe solutions and core services which can be integrated with Adobe Campaign, as well as associated documentation, is available in [this section](#experience-cloud-integrations).

>[!CAUTION]
>
>Most of these integrations require to implement Adobe Identity Management System (IMS), to log in via an Adobe ID. [Learn more in this page](../../integrations/using/about-adobe-id.md).
>

## Linking your solutions {#working-with-experience-cloud-solutions}

Multiple solutions can be linked to Adobe Experience Cloud. The **organization** is the customer entity that enables an administrator to configure groups and users, and to control single sign-on (SSO) in Adobe Experience Cloud. The organization acts like a log-in company that spans all the Experience Cloud products and solutions. Most often, an organization is your company name. However, a company can have many organizations.

Organization management and linking Adobe Experience Cloud accounts are detailed in the [Adobe Experience Cloud help portal](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html).

## Identity and cookie management {#id-and-cookies}

When installing Adobe Campaign or integrating an existing installation with Adobe Experience Cloud, the [Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html) is enabled. This service replaces the permanent cookie used first and foremost by Adobe Campaign for its tracking functionalities.

The Adobe Experience Cloud Identity Service (ID service) provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.

A unique visitor ID will be assigned to recipients generating tracking logs. This ID will be saved in the **[!UICONTROL Requester UUID (@sourceID)]** field of the **[!UICONTROL nms:trackingLogRcp]** table. **The tracking data of recipients who existed before the visitor ID service was implemented will therefore no longer be usable**.

The ID will then be recognized by the other Adobe Experience Cloud solutions with the same CNAME. [Learn more](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/cname.html)

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
   <td> <strong>Adobe Real-time Customer Data Platform (RTCDP)</strong><br /> </td> 
   <td> The integration between Adobe Campaign and Adobe Real-time Customer Data Platform (RTCDP) allows you to share segments data and import audiences to Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Learn more</a> about Campaign - Adobe Real-time Customer Data Platform integration.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
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
   <td> <strong>Adobe Analytics Connector</strong><br /> </td> 
   <td> <strong>Adobe Analytics Connector</strong> allows Adobe Campaign and Adobe Analytics interact through segments concerning user behavior following an email campaign. Conversely, it sends indicators and attributes of email campaigns delivered by Adobe Campaign to Adobe Analytics.<br /> <p><a href="../../platform/using/adobe-analytics-connector.md">Learn more</a> about Campaign - Analytics Connectors integration.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
