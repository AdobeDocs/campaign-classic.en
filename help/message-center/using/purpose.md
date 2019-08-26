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

# Purpose{#purpose}

The purpose of this use case is to add email attachments on the fly to outbound dispatches.

In this scenario, we will see how to send transactional emails with individual / personalized attachments. The attachments will not be pre-uploaded on the Transactional Messaging server but generated on the fly.

When you capture customer interactions or details, you may need to send this information back to the customer at the end of the process, for example in a PDF file attached to an email. Here are the general steps of this scenario.

1. The customer enters the website, finds a product that they want to purchase.
1. The customer selects the product and customizes some options.
1. The customer completes the transaction.
1. An email is sent to the customer confirming the transaction. We don't want to send PII (Personally Identifiable Information) out in the email so we generate a secure PDF and attach it to the email.
1. The customer receives the email and its attachment containing all the needed data.

In this scenario, the attachments are not pre-created but added on the fly to the outbound emails. This also allows you to personalize the content of the attachment. Also, if the attachment is associated with a transaction (as in the example above), then you may need it to contain dynamic data that is generated during the customer process. Attaching PDFs in this way also optimizes security as you can encrypt them and send them over HTTPS.
