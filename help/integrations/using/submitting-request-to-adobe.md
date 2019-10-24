---
title: Submitting request to Adobe
seo-title: Submitting request to Adobe
description: Submitting request to Adobe
seo-description: 
page-status-flag: never-activated
uuid: 8caa1dd6-864d-4101-8b72-c9bd28b8173f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 6d19a5a6-98e5-4b1a-a56a-67cfead152bd
index: y
internal: n
snippet: y
---

# Submitting request to Adobe{#submitting-request-to-adobe}

>[!NOTE]
>
>To be able to proceed further, make sure that IMS is enabled on your system. Consult the section about [IMS](../../integrations/using/about-adobe-id.md).

Once IMS is enabled, you can request provisioning of the People core service/Audience Manager integration with Campaign. To do that, send an email to [Digital-Request@adobe.com](mailto:Digital-Request@adobe.com) with the following information:

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Request Type:</strong><br /> </td> 
   <td> Configure AAM/People core service-Campaign Integration </td> 
  </tr> 
  <tr> 
   <td> <strong>Organization Name:</strong><br /> </td> 
   <td> Your organization name </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS Org ID</strong><br /> </td> 
   <td> Your IMS Org ID* </td> 
  </tr> 
  <tr> 
   <td> <strong>Environment:</strong><br /> </td> 
   <td> Example: Production </td> 
  </tr> 
  <tr> 
   <td> <strong>AAM or People Service</strong><br /> </td> 
   <td> Example: Adobe Audience Manager </td> 
  </tr> 
  <tr> 
   <td> <strong>Declared ID* or Visitor ID</strong><br /> </td> 
   <td> Example: Declared ID </td> 
  </tr> 
  <tr> 
   <td> <strong>Additional Information</strong><br /> </td> 
   <td> Any useful information or comment that you may have </td> 
  </tr> 
 </tbody> 
</table>

&#42; **[!UICONTROL Declared ID]** works for every shared audiences integration. Note that if you are using People core Service, the use of **[!UICONTROL Declared ID]** can change depending on the solution:

* If audiences are shared from Adobe Campaign to Adobe Target via People core service, **[!UICONTROL Declared ID]** can be provisioned.
* If audiences are shared from Adobe Campaign to Ad Cloud via People core Service, you will not be able to use **[!UICONTROL Declared ID]** provisioning for historical backfill of audiences. Some latency is also to be expected when building audiences.
* If audiences are being shared from Adobe Analytics to Adobe Campaign via People Core Service, segments will not be populated in Adobe Campaign with **[!UICONTROL Declared ID]**.

If you are using Adobe Audience Manager instead of People Core Service, **[!UICONTROL Declared ID]** will work in all scenarios.

Please raise request for **[!UICONTROL Declared ID]** provisioning to the following address: [Digital-Request@adobe.com](mailto:Digital-Request@adobe.com).