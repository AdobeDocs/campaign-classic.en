---
title: Creating message content
seo-title: Creating message content
description: Creating message content
seo-description: 
page-status-flag: never-activated
uuid: a7877bae-c76f-46f4-8973-7ebe8fab083d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: eb51c4ad-7b3e-41f5-8acb-f1856d08e007
index: y
internal: n
snippet: y
---

# Creating message content{#creating-message-content}

The definition of the transactional message content is the same as for regular deliveries in Adobe Campaign. For instance, for an email delivery, you can create content in HTML or text format, add attachments or personalize the delivery object. For more on this, refer to the chapter on [Email delivery](../../delivery/using/about-email-channel.md).

>[!CAUTION]
>
>Images included in the message must be publicly accessible. Adobe Campaign does not provide any image upload mechanism for transactional messages.  
>Unlike in JSSP or webApp, `<%=` doesn’t have any default escaping. In this case, you have to escape each data coming from the event properly. This escaping depends on how this field is used. For example, within a URL, please use encodeURIComponent. To be displayed in the HTML, you can use escapeXMLString.

Once you have defined your message content, you can integrate event information into the message body and personalize it. Event information is inserted into the body of the text thanks to personalization tags.

![](assets/messagecenter_create_content_001.png)

To insert personalization tags into the body of an email message, apply the following steps:

1. In the message template, click the tab that matches the email format (HTML or text).
1. Enter the body of the message.
1. In the body of the text, insert the tag using the **Real time events>Event XML** menus.

   ![](assets/messagecenter_create_custo_002.png)

1. Fill in the tag using the following syntax: **element name**.@**attribute name** as shown below.

   ![](assets/messagecenter_create_custo_003.png)

