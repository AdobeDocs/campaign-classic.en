---
solution: Campaign Classic
product: campaign
title: Sending with the Enhanced MTA in Adobe Campaign Classic
description: Learn about the scope and the specificities of sending emails with the Adobe Campaign Enhanced MTA.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
---
# Sending with the Enhanced MTA {#sending-with-enhanced-mta}

The **Adobe Campaign Enhanced MTA** (Mail Transfer Agent) provides an upgraded sending infrastructure allowing for improved deliverability, reputation, throughput, reporting, bounce handling, IP ramp up and connection setting management.

It is implemented to improve scalability, increase delivery throughput and help send more emails faster. This is achieved with new adaptive delivery techniques that alter email sending settings in real-time based on feedback from Internet Service Providers.

>[!IMPORTANT]
>
>The Adobe Campaign Enhanced MTA is only available for Campaign Classic hosted or hybrid customers. Campaign Classic on-premise installations cannot be upgraded to use the Enhanced MTA.

If you were provisioned a Campaign Classic instance after September 2018, you are using the Enhanced MTA. For all other Campaign Classic customers, see the [Frequently asked questions](#enhanced-mta-faq) below.

The Enhanced MTA implementation may impact some of the existing Campaign functionality. For more on this, see the [Enhanced MTA specificities](#enhanced-mta-impacts).

>[!NOTE]
>
>If you are an end user of Adobe Campaign and you want to know whether your instance has been upgraded to the Enhanced MTA, contact your internal Campaign administrator.

## Frequently asked questions {#enhanced-mta-faq}

### Usage and benefits

**What is the Enhanced MTA?**

Adobe Campaign can now be upgraded to use a new MTA (Mail Transfer Agent) which runs SparkPost’s commercial email MTA called **Momentum**.

Momentum represents innovative, high-performance MTA technology which includes smarter bounce handling and an automated deliverability optimization capability that helps senders achieve and maintain optimal inbox delivery rates. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**What are the benefits?**

* Adobe Campaign clients using the Enhanced MTA have seen a <!--300%-->massive increase in overall throughput speed, and a <!--90%+-->significant reduction in soft bounces.
* The Enhanced MTA uses the latest MTA technology to provide you with the optimal throughput speeds for your email delivery.
* By adapting instantly and automatically to the feedback it receives, it also ensures more accurate and intelligent email delivery with real-time delivery data.

**Can I use the native Adobe Campaign MTA and the Enhanced MTA at the same time?**

No. Only the Enhanced MTA can be used for your email deliveries after your instance has been upgraded.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Upgrading to the enhanced MTA

**What is required to upgrade to the Enhanced MTA?**

If you were provisioned a Campaign Classic instance after September 2018, no action is required as you are already using the Enhanced MTA.

For all other hosted or partially hosted (hybrid) customers, the Adobe Campaign team will reach out to coordinate a date for migration and will provide details on the appropriate steps needed to migrate.

>[!IMPORTANT]
>
>The Enhanced MTA is not available for on-premise installations.

**What is the process to upgrade my instance to the Enhanced MTA?**

The entire process for your hosted instances requires a few minutes of downtime. Adobe will monitor the email throughput and deliverability for up to 24 hours post-upgrade to assess any impact to your email deliveries.

In case any issues are discovered, Adobe can quickly and temporarily revert your instance back to the native Adobe Campaign MTA.

Currently, the Enhanced MTA only affects the email channel. Your push notifications and SMS deliveries will continue to use the native Campaign MTA and will not be affected in any way by the upgrade.

**Do I need to go through IP warming again after upgrading to the Enhanced MTA?**

No. Upgrading does not require switching to new IPs, so you can continue using your existing, warmed email IPs.

**Will upgrading to the Enhanced MTA impact any campaigns or deliveries currently in progress?**

Any deliveries that were prepared before your instance was upgraded to use the Enhanced MTA will need to be re-prepared in order to properly use the new MTA.

For customers using Adobe Campaign transactional messaging functionality, any API calls to trigger an email will be queued during the very short upgrade downtime and will be attempted upon completion of the upgrade.

## Enhanced MTA specificities {#enhanced-mta-impacts}

### Enhanced MTA headers

The latest Campaign Classic instances include code that adds the required Enhanced MTA headers to every message. If you are using Adobe Campaign 19.1 (build 9032) or above and if this is not the case, you must request [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) to add the "useMomentum=true" parameter to your execution instance configuration (in the [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta) file), which may be your marketing instance, [mid-sourcing instance](../../installation/using/mid-sourcing-server.md), or [transactional messaging execution instance](../../message-center/using/creating-a-shared-connection.md#execution-instance), depending on your configuration.

However, if you are using an older instance that does not include this code, a new typology rule named **[!UICONTROL Typology Rule for Enhanced MTAs]** must be added to all the existing typologies in your Campaign instance.
This rule is added by a **[!UICONTROL Typology]** package installed as part of the upgrade to the Enhanced MTA.

>[!IMPORTANT]
>
>If you see this typology rule in your typologies, do not delete or modify it in any way. Otherwise, your email deliveries could be adversely affected.

This **[!UICONTROL Typology]** package needs to be installed on the Adobe Campaign marketing instance.

If you are a hybrid client, the Adobe Campaign team will provide you with instructions on how to install the **[!UICONTROL Typology]** package on your marketing instance as part of the upgrade to the Enhanced MTA. Contact your account executive to get the full instructions.

>[!IMPORTANT]
>
>Instructions provided by the Adobe Campaign team on how to install the **[!UICONTROL Typology]** package should be carefully followed. Otherwise you may encounter major issues with your IPs used to send emails.

For more on typologies, see [this section](../../campaign/using/about-campaign-typologies.md).

### New MX rules

The MX management delivery throughput rules are no longer used. The Enhanced MTA has its own MX rules that allow it to customize your throughput by domain based on your own historical email reputation, and on the real-time feedback coming from the domains where you’re sending emails.

For more on MX configuration, see [this section](../../installation/using/email-deliverability.md#mx-configuration).

### Bounce qualification

The bounce qualifications in the Campaign **[!UICONTROL Delivery log qualification]** table are no longer used for **synchronous** delivery failure error messages. The Enhanced MTA determines the bounce type and qualification, and sends back that information to Campaign.

>[!NOTE]
>
>The Enhanced MTA qualifies the SMTP bounce and sends that qualification back to Campaign in the form of a bounce code mapped to a Campaign bounce reason and qualification.

For more on bounce qualification, see [this section](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

### Delivery throughput

The Campaign Delivery throughput graph will no longer display the throughput to your email recipients. That graph will now show the throughput speed for the relay of your messages from Campaign over to the Enhanced MTA.

For more on the delivery throughput, see [this section](../../reporting/using/global-reports.md#delivery-throughput).

### Validity period

The validity period setting in your Campaign deliveries will be used by the Enhanced MTA only if set to **3.5 days or less**. If you define a value higher than 3.5 days in Campaign, it will not be taken into account.

For example, if the validity period is set to the default value of 5 days in Campaign, soft-bouncing messages will go into the Enhanced MTA retry queue and be retried for only up to 3.5 days from when that message reached the Enhanced MTA. In that case, the value set in Campaign will not be used.

Once a message has been in the Enhanced MTA queue for 3.5 days and has failed to deliver, it will time out and its status will be updated from **[!UICONTROL Sent]** to **[!UICONTROL Failed]** in the delivery logs.

For more on the validity period, see [this section](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

### DKIM-signing

DKIM (DomainKeys Identified Mail) email authentication signing is done by the Enhanced MTA. DKIM-signing by the native Campaign MTA will be turned off within the Domain management table as part of the Enhanced MTA upgrade.
For more on DKIM, see the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Delivery success reporting

In the **[!UICONTROL Summary]** view of an email delivery [dashboard](../../delivery/using/delivery-dashboard.md), the **[!UICONTROL Success]** percentage starts out at 100% and then progressively goes down throughout the delivery [validity period](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period), as the soft and hard bounces get reported back from the Enhanced MTA to Campaign.

Indeed, all messages show as **[!UICONTROL Sent]** in the [sending logs](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) as soon as they are successfully relayed from Campaign to the Enhanced MTA. They remain in that status unless or until a [bounce](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) for that message is communicated back from the Enhanced MTA to Campaign.

When hard-bouncing messages get reported back from the Enhanced MTA, their status changes from **[!UICONTROL Sent]** to **[!UICONTROL Failed]** and the **[!UICONTROL Success]** percentage is decreased accordingly.

When soft-bouncing messages get reported back from the Enhanced MTA, they still show as **[!UICONTROL Sent]** and the **[!UICONTROL Success]** percentage is not yet updated. Soft-bouncing messages are then [retried](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) throughout the delivery validity period:

* If a retry is successful before the end of the validity period, the message status remains as **[!UICONTROL Sent]** and the **[!UICONTROL Success]** percentage remains unchanged.

* Otherwise, the status changes to **[!UICONTROL Failed]** and the **[!UICONTROL Success]** percentage is decreased accordingly.

Consequently, you should wait until the end of the validity period to see the final **[!UICONTROL Success]** percentage, and the final number of actually **[!UICONTROL Sent]** and **[!UICONTROL Failed]** messages.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Email Feedback Service (beta) {#email-feedback-service}

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

When soft-bouncing messages get reported back from the Enhanced MTA, their log status remains unchanged (**[!UICONTROL Taken into account by the service provider]**): only the [error reason](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) is updated<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. The **[!UICONTROL Success]** percentage remains unchanged. Soft-bouncing messages are then retried throughout the delivery [validity period](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period):

* If a retry is successful before the end of the validity period, the message status changes to **[!UICONTROL Sent]** and the **[!UICONTROL Success]** percentage is increased accordingly.

* Otherwise, the status changes to **[!UICONTROL Failed]**. The **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->percentage remains unchanged.
  
>[!NOTE]
>
>For more on hard and soft bounces, see [this section](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>For more on retries after a delivery temporary failure, see [this section](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


The tables below show the changes in KPIs and sending logs statuses introduced by the EFS capability.

**With Email Feedback Service**

| Step in the sending process  | KPI summary | Sending logs status |
|--- |--- |--- |
| Message is successfully relayed from Campaign to the Enhanced MTA | **[!UICONTROL Success]** percentage is not displayed (starts out at 0%) | Taken into account by the service provider |
| Hard-bouncing messages get reported back from the Enhanced MTA | No change in **[!UICONTROL Success]** percentage | Failed |
| Soft-bouncing messages get reported back from the Enhanced MTA | No change in **[!UICONTROL Success]** percentage | Taken into account by the service provider |
| Soft-bouncing messages retries are successful | **[!UICONTROL Success]** percentage is increased accordingly | Sent |
| Soft-bouncing messages retries fail |  No change in **[!UICONTROL Success]** percentage  | Failed |

**Without Email Feedback Service**

| Step in the sending process | KPI summary | Sending logs status | 
|--- |--- |--- |
| Message is successfully relayed from Campaign to the Enhanced MTA | **[!UICONTROL Success]** percentage starts out at 100%| Sent |
| Hard-bouncing messages get reported back from the Enhanced MTA | **[!UICONTROL Success]** percentage is decreased accordingly | Failed |
| Soft-bouncing messages get reported back from the Enhanced MTA | No change in **[!UICONTROL Success]** percentage | Sent |
| Soft-bouncing messages retries are successful | No change in **[!UICONTROL Success]** percentage | Sent | **[!UICONTROL Success]** percentage is increased accordingly | Sent |
| Soft-bouncing messages retries fail | **[!UICONTROL Success]** percentage is decreased accordingly | Failed |
