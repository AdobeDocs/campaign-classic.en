---
title: Purpose
seo-title: Purpose
description: Purpose
seo-description: 
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
---

# Use case: Sending a transactional message with attachments{#purpose}


## Key steps {#key-steps}

The purpose of this use case is to add email attachments on the fly to outbound dispatches.

In this scenario, we will see how to send transactional emails with individual and/or personalized attachments. The attachments will not be pre-uploaded on the Transactional Messaging server but generated on the fly.

When you capture customer interactions or details, you may need to send this information back to the customer at the end of the process, for example in a PDF file attached to an email. Here are the general steps of this scenario.

1. The customer enters the website, finds a product that they want to purchase.
1. The customer selects the product and customizes some options.
1. The customer completes the transaction.
1. An email is sent to the customer confirming the transaction. We don't want to send PII (Personally Identifiable Information) out in the email so we generate a secure PDF and attach it to the email.
1. The customer receives the email and its attachment containing all the needed data.

In this scenario, the attachments are not pre-created but added on the fly to the outbound emails. This also allows you to personalize the content of the attachment. Also, if the attachment is associated with a transaction (as in the example above), then you may need it to contain dynamic data that is generated during the customer process. Attaching PDFs in this way also optimizes security as you can encrypt them and send them over HTTPS.

## Recommendations {#important-notes}

* The Transactionnal Messaging instances should not be used to keep/export/upload files or data. It is only used for event data and related information. They should not be considered as a file storage system.
* Since there is no direct access to the Transactionnal Messaging instances or servers outside of Adobe, there is no standard way to push such files on these servers (no FTP access). 
* It is not contractually correct to use the disk space on the Transactional Messaging instaces isk space to store files of any sort, not even for attachments. 
* You need to use another online disk system to host these files. You need an FTP access to this system and be able to write and delete files.

## Implementation {#implementation}

Here is a diagram with the different steps involved in this scenario.

![](assets/message-center-uc1.png)

1. Start by designing your attachment. For more on this, see [this section](../../delivery/using/attaching-files.md#attach-a-personalized-file).
    
    This allows you to have the files attached to an email, even if they are not hosted on the execution instance.

1. You can send emails via a SOAP message trigger. In the SOAP call, there is a URL parameter (attachmentURL).

    For more information on SOAP requests, see [Event description](../../message-center/using/event-description.md).

1. When designing your email, click **[!UICONTROL Attachment]**.

1. In the **[!UICONTROL Attachment definition]** screen, enter the SOAP attachment parameter:

    ```
    <%= rtEvent.ctx.attachementUrl %>
    ```

1. When the message is processing/deploying, the system will get the file from the remote location (third-party server) and attach it to the individual message.

Since this parameter can be a variable, it should accept the fully formed remote URL variable of your file, sent via the SOAP call.

![](assets/message-center-uc2.png)
