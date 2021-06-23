---
product: campaign
title: Optimize message delivery
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: 24b2ee47-bec7-43ce-81b3-0b2d1a5cebae
---
# Optimize delivery {#optimize-delivery}

Before even starting creating deliveries, you can take several actions to secure and optimize the sending process upstream.

The following section outlines best practices and recommended procedures for the optimal configuration of Adobe Campaign. Following these practices will minimize issues that you might face downstream.

## Platform performance

Several factors can directly impact server performance and slow the platform:

* The number and type of personalization elements: personalization in emails pulls data out of the database for each recipient. If there are many personalization elements, that increases the amount of data needed to prepare the delivery.  Learn more about personalization in [this section](about-personalization.md)

* The server load: when the marketing server is handling many different tasks at the same time, it can slow down performance. The marketing server needs to coordinate all of the incoming and outgoing data for all of the deliveries to ensure that the data is correct and on time.

    **TIP** - To avoid this, coordinate the scheduling of deliveries with the other members of your team to ensure the best performance.

* The workflow execution: monitoring your workflows is essential to avoid platform performance issues. Follow the guidelines listed [in this document](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* If you are eligible, you can leverage [Campaign Contol Panel capabilities](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html) to monitor your platform, using [performance monitoring](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html) functionalities.

## Checking network configuration {#network-config}

To optimize delivery when handling emails in large volumes and avoid being mistaken for a spammer, make sure that you have a legitimate network configuration that does not try to hide the identity of the server.

**Tip**:  Use a transparent sender address corresponding to your brand's website. For example, the TravelAgency company manages the Valentino hotel chain. Its owns the valentino.com domain for its website. To promote the Valentino hotel in Paris, it uses the paris.valentino.com sub-domain. Therefore, a relevant sender address can be hotel@paris.valentino.com.

## Deliverability management {#deliverability-management}

To reach your recipients' inbox without bouncing or being marked as spam, you need to improve the deliverability rate of your messages.

* What is deliverability?

    * It refers to the factors of an email that determine its ability to be accepted by a recipient’s server. ISPs (Internet Service Providers) filter out emails that they identify as SPAM, or they block images from downloading. If they determine that a certain domain is sending too many emails, they will set a limit on the number of emails that they will accept from that sender.

    * When checking your email for deliverability, you want to focus on four main categories: data quality, message and content, sending infrastructure, and reputation. For a deeper dive on this topic, refer to [this section](about-deliverability.md).

* Apply the recommendations detailed [in this document](about-deliverability.md).

* Contact your Adobe representative for assistance.

## Quarantine management {#quarantine-management}

It is in your best interest to maintain good quarantine management processes.

When starting to send emails on a new platform, you may use a list of addresses that are not fully qualified. If you send to invalid addresses or to honeypot addresses (mailboxes only created to trick spammers), this will start to diminish the reputation of your platform. Good quarantine management processes help to: maintain address quality, avoid denylist by internet access providers, and reduce your error rate, speeding up deliveries and throughput.

**Tips**

* If you have a list of invalid addresses, Adobe recommends importing it to the quarantine table, through **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* The recipients whose addresses are quarantined are excluded by default during the delivery analysis: they are not targeted. This will speed up deliveries, as the error rate has a significant effect on delivery speed. An email address can be quarantined for example when the inbox is full or if the address does not exist. [Learn more](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign manages erroneous addresses according to the type of error returned. For more on this, refer to [this section](understanding-quarantine-management.md).


* Some internet access providers automatically consider emails to be spam if the rate of invalid addresses is too high. Quarantine therefore allows you to avoid being added to denylist by these providers.

* Quarantines management will also help reducing SMS sending costs by excluding erroneous phone numbers from deliveries. 

## Double opt-in mechanism {#double-opt-in}

To avoid sending messages to invalid addresses, limit improper communications and improve sender reputation, Adobe recommends implementing a double opt-in mechanism for post-subscription confirmation. This helps ensure a recipient subscribed intentionally.

Details for implementing this mechanism are outlined in [this section](../../web/using/use-cases--web-forms.md).
