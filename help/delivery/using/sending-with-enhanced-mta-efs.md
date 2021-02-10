---
solution: Campaign Classic
product: campaign
title: Sending with the Enhanced MTA in Adobe Campaign Classic
description: Learn about the scope and the specificities of sending emails with the Adobe Campaign Enhanced MTA.
audience: delivery
content-type: reference
topic-tags: sending-emails
---

# Sending with the Enhanced MTA {#sending-with-enhanced-mta}

<!--## Sent status with Enhanced MTA

In the **[!UICONTROL Summary]** view of an email delivery [dashboard](../..delivery/using/delivery-dashboard.md), the **[!UICONTROL Success]** percentage starts out at 100% and then progressively goes down throughout the delivery [validity period](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period), as the soft and hard bounces get reported back from the Enhanced MTA to Campaign.

Indeed, all messages show as **[!UICONTROL Sent]** in the [sending logs](../../delivery/using/delivery-dashboard.md##delivery-logs-and-history) as soon as they are successfully relayed from Campaign to the Enhanced MTA (Message Transfer Agent). They remain in that status unless or until a [bounce](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) for that message is communicated back from the Enhanced MTA to Campaign.

When hard-bouncing messages get reported back from the Enhanced MTA, their status changes from **[!UICONTROL Sent]** to **[!UICONTROL Failed]** and the **[!UICONTROL Success]** percentage is decreased accordingly.

When soft-bouncing messages get reported back from the Enhanced MTA, they still show as **[!UICONTROL Sent]** and the **[!UICONTROL Success]** percentage is not yet updated. Soft-bouncing messages are then [retried](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) throughout the delivery validity period:

* If a retry is successful before the end of the validity period, the message status remains as **[!UICONTROL Sent]** and the **[!UICONTROL Success]** percentage remains unchanged.

* Otherwise, the status changes to **[!UICONTROL Failed]** and the **[!UICONTROL Success]** percentage is decreased accordingly.

Consequently, you should wait until the end of the validity period to see the final **[!UICONTROL Success]** percentage, and the final number of actually **[!UICONTROL Sent]** and **[!UICONTROL Failed]** messages.

Note: The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

## Email Feedback Service (beta) {#email-feedback-service}

With the Email Feedback Service (EFS) capability, the status of each email is accurately reported, because feedback is captured directly from the Enhanced MTA (Message Transfer Agent).

>[!IMPORTANT]
>
>The Email Feedback Service is currently available as a beta capability.
>
>If you’re interested in participating in this beta program, fill out [this form](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) and we’ll get back to you.

Once the delivery has started, there is no change in the **[!UICONTROL Success]** percentage when the message is successfully relayed from Campaign to the Enhanced MTA.

<!--![](assets/efs-sending.png)-->

The delivery logs show the **[!UICONTROL Taken into account by the service provider]** status for each targeted address.

<!--![](assets/efs-pending.png)-->

When the message is actually delivered to the targeted profiles and once this information is reported back in real time from the Enhanced MTA, the delivery logs show the **[!UICONTROL Sent]** status for each address that successfully received the message. The **[!UICONTROL Success]** percentage is increased accordingly with each successful delivery.

When hard-bouncing messages get reported back from the Enhanced MTA, their log status changes from **[!UICONTROL Taken into account by the service provider]** to **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

When soft-bouncing messages get reported back from the Enhanced MTA, their log status also changes from **[!UICONTROL Taken into account by the service provider]** to **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. The **[!UICONTROL Success]** percentage remains unchanged. Soft-bouncing messages are then retried throughout the delivery [validity period](../../administration/using/configuring-email-channel.md#validity-period-parameters):

* If a retry is successful before the end of the validity period, the message status changes to **[!UICONTROL Sent]** and the **[!UICONTROL Success]** percentage is increased accordingly.

* Otherwise, the status remains as **[!UICONTROL Failed]**. The **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->percentage remains unchanged.
  
>[!NOTE]
>
>For more on hard and soft bounces, see [this section](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>For more on retries after a delivery temporary failure, see [this section](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

## Changes introduced by EFS {#changes-introduced-by-efs}

The table below shows the changes in KPIs and sending logs statuses introduced by the EFS capability.

| Step in the<br>sending process | KPI summary<br>WITHOUT EFS | Sending logs status<br>WITHOUT EFS | KPI summary<br>WITH EFS | Sending logs status<br>WITH EFS |
|--- |--- |--- | --- | --- |
| Message is successfully relayed from Campaign to the Enhanced MTA | **[!UICONTROL Success]** percentage starts out at 100%| Sent | **[!UICONTROL Success]** percentage is not displayed (starts out at 0%) | Taken into account by the service provider |
| Hard-bouncing messages get reported back from the Enhanced MTA | **[!UICONTROL Success]** percentage is decreased accordingly | Failed | No change in **[!UICONTROL Success]** percentage | Failed |
| Soft-bouncing messages get reported back from the Enhanced MTA | No change in **[!UICONTROL Success]** percentage | Sent | No change in **[!UICONTROL Success]** percentage | Taken into account by the service provider (no change in status, but [error reason](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) is updated) |
| Soft-bouncing messages retries are successful | No change in **[!UICONTROL Success]** percentage | Sent | **[!UICONTROL Success]** percentage is increased accordingly | Sent |
| Soft-bouncing messages retries fail | **[!UICONTROL Success]** percentage is decreased accordingly | Failed |  No change in **[!UICONTROL Success]** percentage  | Failed |