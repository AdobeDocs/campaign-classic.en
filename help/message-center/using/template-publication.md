---
title: Template publication
seo-title: Template publication
description: Template publication
seo-description: 
page-status-flag: never-activated
uuid: 2bb87937-9f82-4c6d-9893-e53bf5b68ffd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 6a09685d-fa67-4f9f-8f4d-728f8ca6bfc0
index: y
internal: n
snippet: y
---

# Template publication{#template-publication}

Once the message template created on the control instance is complete, you can publish it on all execution instances. Publication lets you automatically create two message templates on the execution instance which will allow you to send messages linked to real time and batch events.

>[!CAUTION]
>
>Remember to publish the template whenever you make any changes to it in order for these changes to be effective during transactional message delivery.

>[!NOTE]
>
>When publishing transactional message templates, typology rules are automatically published on the execution instances.

1. In the control instance, go to the **Message Center > Transactional message templates** folder of the tree.
1. Select the template you want to publish on your execution instances.
1. Click **Publication**.

   ![](assets/messagecenter_publish_model_008.png)

Once publication is complete, both message templates to be applied to batch and real time type events are created in the tree of the production instance in the **Administration > Production > Message Center > Default > Transactional message templates** folder. 

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>If you replace an existing field of the transactional message template, such as the sender address, with an empty value, the corresponding field on the execution instance(s) will not be updated once the transactional message is published again. It will still contain the previous value. However, if you add a non-empty value, the corresponding field will be updated as usual after the next publication.

