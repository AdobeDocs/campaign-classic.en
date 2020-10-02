---
title: Creating message content
seo-title: Creating message content
description: Creating message content
seo-description: 
page-status-flag: never-activated
uuid: 4ee013fc-fba2-4120-b796-dd4008000ea9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 1f420652-c9af-4a49-8d5c-a640e960aced
index: y
internal: n
snippet: y
---

# Creating message content{#creating-message-content}

The definition of the transactional message content is the same as for regular deliveries in Adobe Campaign. For instance, for an email delivery, you can create content in HTML or text format, add attachments or personalize the delivery object. For more on this, refer to the chapter on [Email delivery](../../delivery/using/about-email-channel.md).

>[!IMPORTANT]
>
>Images included in the message must be publicly accessible. Adobe Campaign does not provide any image upload mechanism for transactional messages.  
>Unlike in JSSP or webApp, `<%=` doesn’t have any default escaping.
>
>In this case, you have to escape each data coming from the event properly. This escaping depends on how this field is used. For example, within a URL, please use encodeURIComponent. To be displayed in the HTML, you can use escapeXMLString.

Once you have defined your message content, you can integrate event information into the message body and personalize it. Event information is inserted into the body of the text thanks to personalization tags.

![](assets/messagecenter_create_content_001.png)

* All the personalization fields are coming from the payload.
* It is possible to reference one or several personalization blocks in a transactional message. The block content will be added to the delivery content during the publication to the execution instance.

To insert personalization tags into the body of an email message, apply the following steps:

1. In the message template, click the tab that matches the email format (HTML or text).
1. Enter the body of the message.
1. In the body of the text, insert the tag using the **[!UICONTROL Real time events>Event XML]** menus.

   ![](assets/messagecenter_create_custo_002.png)

1. Fill in the tag using the following syntax: **element name**.@**attribute name** as shown below.

   ![](assets/messagecenter_create_custo_003.png)

