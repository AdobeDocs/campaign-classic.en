---
solution: Campaign Classic
product: campaign
title: Template publication
description: Transactional message template publication
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
---
# Template publication{#template-publication}

When the message template created on the control instance is complete, you can publish it. This process will also publish it on all execution instances.

Publication lets you automatically create two message templates on the execution instances, which will allow you to send messages linked to real-time and batch events.

>[!NOTE]
>
>When publishing transactional message templates, typology rules are also automatically published on the execution instances.

>[!IMPORTANT]
>
>Whenever you make any changes to a template, make sure you publish it again for these changes to be effective during transactional message delivery.

1. On the control instance, go to the **[!UICONTROL Message Center > Transactional message templates]** folder of the tree.
1. Select the template you want to publish on your execution instances.
1. Click **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Once publication is complete, both message templates to be applied to batch and real-time type events are created in the tree of the production instance in the **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** folder.

![](assets/messagecenter_deployed_model_001.png)

Once a template is published, if the corresponding event is triggered, the execution instance will receive the event, link it to the transactional template and send the corresponding transactional message to each recipient.

>[!NOTE]
>
>If you replace an existing field of the transactional message template, such as the sender address, with an empty value, the corresponding field on the execution instance(s) will not be updated once the transactional message is published again. It will still contain the previous value.
>
>However, if you add a non-empty value, the corresponding field will be updated as usual after the next publication.
