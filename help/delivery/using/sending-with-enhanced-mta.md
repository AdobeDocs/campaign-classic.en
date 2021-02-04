---
solution: Campaign Classic
product: campaign
title: Sending an email with Adobe Campaign Classic
description: Learn about email delivery parameters
audience: delivery
content-type: reference
topic-tags: sending-emails
---

# Sending with the Enhanced MTA{#sending-with-enhanced-mta}

The Adobe Campaign Enhanced MTA (Mail Transfer Agent) provides an upgraded sending infrastructure allowing for improved deliverability, reputation, throughput, reporting, bounce handling, IP ramp up and connection setting management.

It is implemented to improve scalability, increase delivery throughput and help send more emails faster. This is achieved with new adaptive delivery techniques that alter email sending settings in real-time based on feedback from Internet Service Providers.

If you were provisioned a Campaign Classic instance after September 2018, no action is required as you’re already using the Enhanced MTA. For all other Campaign Classic customers, see the Frequently asked questions below.

>[!IMPORTANT]
>
>The Adobe Campaign Enhanced MTA is only available for Campaign Classic hosted or hybrid customers. Campaign Classic on-premise installations cannot be upgraded to use the Enhanced MTA.

Enhanced MTA impacts

## Enhanced MTA headers

The latest Campaign Classic instances include code that adds the required Enhanced MTA headers to every message. If you are using Adobe Campaign 19.1 (build 9032) or above and if this is not the case, you must add the "useMomentum=true" parameter to your marketing instance configuration (in the serverConf.xml file).

However, if you're using an older instance that doesn't include this code, a new typology rule named Typology Rule for Enhanced MTAs must be added to all the existing typologies in your Campaign instance.
This rule is added by a Typology package installed as part of the upgrade to the Enhanced MTA.

>[!IMPORTANT]
>
>If you see this typology rule in your typologies, do not delete or modify it in any way. Otherwise, your email deliveries could be adversely affected.

This Typology package needs to be installed on the Adobe Campaign marketing instance.

If you're a hybrid client, the Adobe Campaign team will provide you with instructions on how to install the Typology package on your marketing instance as part of the upgrade to the Enhanced MTA. Contact your account executive to get the full instructions.

>[!IMPORTANT]
>
>Instructions provided by the Adobe Campaign team on how to install the Typology package should be carefully followed. Otherwise you may encounter major issues with your IPs used to send emails.

For more on typologies, see About campaign typologies in Campaign Classic.

## New MX rules

The MX management delivery throughput rules are no longer used. The Enhanced MTA has its own MX rules that allow it to customize your throughput by domain based on your own historical email reputation, and on the real-time feedback coming from the domains where you’re sending emails.

For more on MX management, see MX configuration in Campaign Classic.

## Bounce qualification

The bounce qualifications in the Campaign Delivery log qualification table are no longer used. The Enhanced MTA determines the bounce type and qualification, and sends back that information to Campaign.

>[!NOTE]
>
>The Enhanced MTA qualifies the SMTP bounce and sends that qualification back to Campaign in the form of a bounce code mapped to a Campaign bounce reason and qualification.

For more on bounce qualification, see Bounce mail qualification in Campaign Classic.

## Sent status

### With Enhanced MTA {#efs}

All messages will show as Sent as soon as they are successfully relayed from Campaign to the Enhanced MTA. They will stay in that state unless or until a bounce for that message is communicated back from the Enhanced MTA to Campaign.

Consequently:

* In the Summary view of each message, the Success percentage will start out at 100% and then go down throughout the validity period of the delivery as the soft and hard bounces get reported back from the Enhanced MTA to Campaign.
* Soft-bouncing messages will no longer show as Failed after day one of the delivery, and be retried on each additional day of the validity period for the delivery. They will stay in the Enhanced MTA retry queue throughout the delivery validity period.

>[!NOTE]
>
>You should wait until the end of the validity period to see the final Success percentage, and the final number of Sent and Failed messages.

The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.

The Campaign Delivery throughput graph will no longer display the throughput to your email recipients. That graph will now show the throughput speed for the relay of your messages from Campaign over to the Enhanced MTA.
For more on the delivery throughput, see Accessing deliveries throughput information in Campaign Classic.

### Email Feedback Service

## Validity period

The validity period setting in your Campaign deliveries will be used by the Enhanced MTA only if set to 3.5 days or less. If you define a value higher than 3.5 days in Campaign, it will not be taken into account.

>[!NOTE]
>
>For example, if the validity period is set to the default value of 5 days in Campaign, soft-bouncing messages will go into the Enhanced MTA retry queue and be retried for only up to 3.5 days from when that message reached the Enhanced MTA. In that case, the value set in Campaign will not be used.

Once a message has been in the Enhanced MTA queue for 3.5 days and has failed to deliver, it will time out and its status will be updated from Sent to Failed in the delivery logs.

For more on the validity period, see Defining the validity period in Campaign Classic.

## DKIM-signing

DKIM (DomainKeys Identified Mail) email authentication signing is done by the Enhanced MTA. DKIM-signing by the native Campaign MTA will be turned off within the Domain management table as part of the Enhanced MTA upgrade.
For more on DKIM, see DKIM authentication in Campaign Classic.