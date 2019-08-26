---
title: Implementation
seo-title: Implementation
description: Implementation
seo-description: 
page-status-flag: never-activated
uuid: 12b5fbbf-fe0d-4598-8845-f7b8ee7672c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: ac1c0a00-41ef-4cc2-bb51-2808ef400bb1
index: y
internal: n
snippet: y
---

# Implementation{#implementation}

Here is a diagram with the different steps involved in this scenario.

![](assets/message-center-uc1.png)

First, start by designing your attachment. See this [article](https://helpx.adobe.com/campaign/classic/delivery/using/attaching-files.html#attach-a-personalized-file). This allows you to have the files attached to an email, even if they are not hosted on the execution instance.

You can send emails via a SOAP message trigger. For more information on SOAP requests, see [Event description](https://helpx.adobe.com/campaign/standard/message-center/using/event-description.html). In the SOAP call, there is a URL parameter (attachmentURL).

When designing your email, click on **[!UICONTROL Attachment]** . In the **[!UICONTROL Attachment definition]** screen, enter the SOAP attachment parameter:

```
<%= rtEvent.ctx.attachementUrl %>
```

When the message is processing/deploying, the system will get the file from the remote location (third-party server) and attach it to the individual message.

Since this parameter can be a variable, it should accept the fully formed remote URL variable of your file, sent via the SOAP call.

![](assets/message-center-uc2.png)

