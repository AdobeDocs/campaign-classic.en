---
title: Campaign delivery best practices
seo-title: Delivery best practices
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
---

# Delivery best practices {#delivery-best-practices}

## Optimize delivery {#optimize-delivery}

Before even starting creating deliveries, you can take several actions to secure and optimize the sending process upstream.

The following section outlines best practices and recommended procedures for the optimal configuration of Adobe Campaign. Following these practices will minimize issues that you might face downstream.

### Platform performance

Several factors can directly impact server performance and slow the platform:

* The number and type of personalization elements: personalization in emails pulls data out of the database for each recipient. If there are many personalization elements, that increases the amount of data needed to prepare the delivery.  Learn more about personalization in [this section](../../delivery/using/about-personalization.md)

* The server load: when the marketing server is handling many different tasks at the same time, it can slow down performance. The marketing server needs to coordinate all of the incoming and outgoing data for all of the deliveries to ensure that the data is correct and on time.

    **TIP** - To avoid this, coordinate the scheduling of deliveries with the other members of your team to ensure the best performance.

* The workflow execution: monitoring your workflows is essential to avoid platform performance issues. Follow the guidelines listed [in this document](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* As a hosted customer, you can leverage [Campaign Contol Panel capabilities](https://docs.adobe.com/content/help/en/control-panel/using/discover-control-panel/key-features.html) to monitor your platform, using [performance monitoring](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) functionalities. Learn more

### Checking network configuration {#network-config}

To optimize delivery when handling emails in large volumes and avoid being mistaken for a spammer, make sure that you have a legitimate network configuration that does not try to hide the identity of the server.

**Tip** -  Use a transparent sender address corresponding to your brand's website. For example, the TravelAgency company manages the Valentino hotel chain. Its owns the valentino.com domain for its website. To promote the Valentino hotel in Paris, it uses the paris.valentino.com sub-domain. Therefore, a relevant sender address can be hotel@paris.valentino.com.

### Deliverability management {#deliverability-management}

To reach your recipients' inbox without bouncing or being marked as spam, you need to improve the deliverability rate of your messages.

* What is deliverability?

    * It refers to the factors of an email that determine its ability to be accepted by a recipient’s server. ISPs (Internet Service Providers) filter out emails that they identify as SPAM, or they block images from downloading. If they determine that a certain domain is sending too many emails, they will set a limit on the number of emails that they will accept from that sender.

    * When checking your email for deliverability, you want to focus on four main categories: data quality, message and content, sending infrastructure, and reputation. For a deeper dive on this topic, refer to [this section](../../delivery/using/about-deliverability.md).

* Apply the recommendations detailed [in this document](../../delivery/using/deliverability-key-points.md).

* Contact your Adobe representative for assistance.

### Quarantine management {#quarantine-management}

It is in your best interest to maintain good quarantine management processes.

When starting to send emails on a new platform, you may use a list of addresses that are not fully qualified. If you send to invalid addresses or to honeypot addresses (mailboxes only created to trick spammers), this will start to diminish the reputation of your platform. Good quarantine management processes help to: maintain address quality, avoid block list by internet access providers, and reduce your error rate, speeding up deliveries and throughput.

**Tips**

* If you have a list of invalid addresses, Adobe recommends importing it to the quarantine table, through **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* The recipients whose addresses are quarantined are excluded by default during the delivery analysis: they are not targeted. This will speed up deliveries, as the error rate has a significant effect on delivery speed. An email address can be quarantined for example when the inbox is full or if the address does not exist. [Learn more](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign manages erroneous addresses according to the type of error returned. For more on this, refer to [this section](../../delivery/using/understanding-quarantine-management.md).


* Some internet access providers automatically consider emails to be spam if the rate of invalid addresses is too high. Quarantine therefore allows you to avoid being added to a block list by these providers.

* Quarantines management will also help reducing SMS sending costs by excluding erroneous phone numbers from deliveries. 

### Double opt-in mechanism {#double-opt-in}

To avoid sending messages to invalid addresses, limit improper communications and improve sender reputation, Adobe recommends implementing a double opt-in mechanism for post-subscription confirmation. This helps ensure a recipient subscribed intentionally.

Details for implementing this mechanism are outlined in [this section](../../web/using/use-cases--web-forms.md).

## Use templates {#use-templates}

Delivery templates allow for increased efficiency by providing ready-made scenarios for most common types of activities. With templates, marketers can deploy new campaigns with minimal customization in a shorter amount of time.

Learn more about delivery templates in [this section](../../delivery/using/creating-a-delivery-template.md).

### Get started with delivery templates {#gs-templates}

A delivery template enables you to define once a set of technical and functional properties that suit your needs and that can be reused for future deliveries. You can then save time and standardize deliveries when needed.

When you manage several brands in Adobe Campaign, Adobe recommends having one sub-domain per brand. For example, a bank can have several sub-domains corresponding to each of its regional agencies. If a bank owns the bluebank.com domain, its sub-domains can be @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, etc. Having one delivery template per sub-domain enables you to always use the right pre-configured parameters for each of your brand, which avoids errors and saves you time.

**Tip** -  To avoid configuration errors in Campaign Standard, we recommend that you duplicate a native template and alter its properties rather than create a new template.

Below are a few best practices when configuring a delivery template:

**Configure addresses**

* The sender's address is mandatory to allow an email to be sent.

* Some ISPs (Internet Service Providers) check the validity of the sender address before accepting messages. 

* A badly formed address may result in it being rejected by the receiving server. You must make sure a correct address is given.

* Adobe Campaign checks the syntax of email addresses entered.

* The address must explicitly identify the sender. The domain must be owned by and registered to the sender.

* Adobe recommends creating email accounts that correspond to the addresses specified for deliveries and replies. Check with your messaging system administrator.

To configure addresses in Campaign interface, follow the steps below:

1. In the delivery template, click the **[!UICONTROL From]** link. In the **[!UICONTROL Email header parameters]** window, fill in the following fields:

    ![](assets/d_best_practices_email_header.png)

1. In the **[!UICONTROL Sender address]** field, make sure the address domain is the same as the sub-domain that you delegated to Adobe. You can change the part preceding the '@' but not the domain address.

1. In the **[!UICONTROL From]** field, use a name that is easily identifiable by the recipients, such as your brand's name, to increase the opening rate of your deliveries. To further improve the recipient's experience, you can add a person's name, for example "Emma from Megastore".

1. In the **[!UICONTROL Reply address text]** fiels, the sender's address is used by default for replies. However, Adobe recommends using an existing real address such as your brand's customer care. In this case, if a recipient sends a reply, the customer care will be able to handle it.

**Set up a control group**

Once the delivery is sent, you can compare the behavior of the excluded recipients with the recipients who did receive the delivery. You can then measure the efficiency of your campaigns.

To set up a control group, click the **[!UICONTROL To]** link. In the **[!UICONTROL Select target]** window, select the **[!UICONTROL Control group]** tab. You can extract a portion of the target, for example a 5% random sample.

   ![](assets/d_best_practices_control_group.png)

**Use typologies to apply filters or control rules**

A typology contains checking rules that are applied during the analysis phase, before sending any message.

In the **[!UICONTROL Typology]** tab of the template's properties, change the default typology according to your needs.

For example, to better control the outbound traffic, you can define which IP addresses can be used by defining one affinity per sub-domain and creating one typology per affinity. The affinities are defined in the instance's configuration file. Contact your Adobe Campaign administrator.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## Design and personalize {#design-and-personalize}

When designing your message content, try to avoid common issues that could prevent you from executing your delivery. Most of the time, possible errors are related to [personalization](../../delivery/using/about-personalization.md), [formatting](../../delivery/using/defining-the-email-content.md#message-content) and [images](../../delivery/using/defining-the-email-content.md#adding-images).

###  Optimize personalization {#optimize-personalization}

To avoid common issues that could prevent you from executing your delivery and to improve your recipients' experience, Adobe Campaign enables you to personalize your messages.

You can use recipients' data stored in the Adobe Campaign database, or collected through tracking, landing pages, subscriptions, etc.
Personalization basics are presented in [this section](../../delivery/using/personalization-fields.md).

Make sure your message content is properly designed to avoid any errors, which are generally related to personalization.

**Tips** - In personalization fields coming from external files provided by third-party vendors, external HTML content can be wrong. To avoid this, check syntax, use of tags, characters, etc. For example, an Adobe Campaign personalization tag always has the following form: <%=table.field%>. For more on this, see [this section](../../delivery/using/about-personalization.md).

The incorrect use of parameters in personalization blocks can be an issue. For example, variables in JavaScript should be used as follows:

    <%

    var brand = "xxx"

    %>

For more on personalization blocks, refer to the [this section](../../delivery/using/personalization-blocks.md).

You can prepare personalization data in a workflow to improve delivery preparation analysis. This should be used specially if the personalization data come from an external table through Federated Data Access (FDA). This option is described in this [this section](../../delivery/using/personalization-fields.md#optimizing-personalization)

## Delivery troubleshooting {#delivery-troubleshooting}

Specific actions can be performed when encountering issues with deliveries:
* [Deliverability issues](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Image display issues](../../production/using/image-display-issues.md)
* [Delivery performance issues](../../delivery/using/monitoring-a-delivery.md#performance_issues)
* [Temporary files issues](../../production/using/temporary-files.md) - *on-premise customers only*