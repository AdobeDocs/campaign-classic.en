---
title: Implementation
seo-title: Implementation
description: Implementation
seo-description: 
page-status-flag: never-activated
uuid: 63141c30-9a95-44cf-bdac-21599a0ac992
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 2cb918d1-17a4-4741-bc8c-5b3788935572
index: y
internal: n
snippet: y
---

# Implementation{#implementation}

Here is a diagram with the different steps involved in this scenario.

![](assets/message-center-uc1.png)

First, start by designing your attachment. See this [article](../../delivery/using/attaching-files.md#attach-a-personalized-file). This allows you to have the files attached to an email, even if they are not hosted on the execution instance.

You can send emails via a SOAP message trigger. For more information on SOAP requests, see [Event description](../../message-center/using/event-description.md). In the SOAP call, there is a URL parameter (attachmentURL).

When designing your email, click on **Attachment**. In the **Attachment definition** screen, enter the SOAP attachment parameter:

```
<%= rtEvent.ctx.attachementUrl %>
```

When the message is processing/deploying, the system will get the file from the remote location (third-party server) and attach it to the individual message.

Since this parameter can be a variable, it should accept the fully formed remote URL variable of your file, sent via the SOAP call.

![](assets/message-center-uc2.png)

