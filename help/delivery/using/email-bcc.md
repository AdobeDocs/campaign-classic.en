---
solution: Campaign Classic
product: campaign
title: Sending an email with Adobe Campaign Classic
description: Learn about email delivery parameters
audience: delivery
content-type: reference
topic-tags: sending-emails
---

# Email BCC {#email-bcc}

Adobe Campaign enables you to store emails on an external system through BCC by simply adding a BCC email address to your message target.

Once the option activated, an exact copy of all sent messages will be kept for this delivery.

For more information on Email BCC configuration and best practices, refer to [this section](../../installation/using/email-archiving.md).

>[!NOTE]
>
>Email BCC is an optional capability. Please check your license agreement and contact your account executive to activate it.

When creating a new delivery or delivery template, Email BCC is not enabled by default. You need to enable it manually at the email delivery or delivery template level.

>[!IMPORTANT]
>
>If you have upgraded to the Enhanced MTA, you can request to use Email BCC with Enhanced MTA for improved efficiency and less latency. In that case, all sent emails are automatically sent to the BCC address. You cannot enable it at the delivery or delivery template level, thus the steps below do not apply. For more on this, see [this section](../../installation/using/email-archiving.md).

To enable Email BCC for an email delivery template, follow the steps below:

1. Go to **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** or **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Select the delivery of your choice or duplicate the out-of-the-box **Email delivery** template, then select the duplicated template.
1. Click the **Properties** button.
1. Select the **[!UICONTROL Delivery]** tab.
1. Check the **Email BCC** option. A copy of all sent messages for each delivery based on this template will be sent to the Email BCC address which has been configured.

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>If the emails sent to the BCC address are opened and clicked through, this will be taken into account in the **[!UICONTROL Total opens]** and **[!UICONTROL Clicks]** from the send analysis, which could cause some miscalculations.
