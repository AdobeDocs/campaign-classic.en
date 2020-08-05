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

* As a hosted customer, you can leverage [Campaign Contol Panel capabilities](https://docs.adobe.com/content/help/en/control-panel/using/discover-control-panel/key-features.html) to monitor your platform, using [performance monitoring](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) functionalities.

### Checking network configuration {#network-config}

To optimize delivery when handling emails in large volumes and avoid being mistaken for a spammer, make sure that you have a legitimate network configuration that does not try to hide the identity of the server.

**Tip**:  Use a transparent sender address corresponding to your brand's website. For example, the TravelAgency company manages the Valentino hotel chain. Its owns the valentino.com domain for its website. To promote the Valentino hotel in Paris, it uses the paris.valentino.com sub-domain. Therefore, a relevant sender address can be hotel@paris.valentino.com.

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

A [delivery template](../../delivery/using/creating-a-delivery-template.md) enables you to define once a set of technical and functional properties that suit your needs and that can be reused for future deliveries. You can then save time and standardize deliveries when needed.

When you manage several brands in Adobe Campaign, Adobe recommends having one sub-domain per brand. For example, a bank can have several sub-domains corresponding to each of its regional agencies. If a bank owns the bluebank.com domain, its sub-domains can be @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, etc. Having one delivery template per sub-domain enables you to always use the right pre-configured parameters for each of your brand, which avoids errors and saves you time.

**Tip**:  To avoid configuration errors in Campaign Standard, we recommend that you duplicate a native template and alter its properties rather than create a new template.

**Configure addresses**

* The sender's address is mandatory to allow an email to be sent.

* Some ISPs (Internet Service Providers) check the validity of the sender address before accepting messages. 

* A badly formed address may result in it being rejected by the receiving server. You must make sure a correct address is given.

* The address must explicitly identify the sender. The domain must be owned by and registered to the sender.

* Adobe recommends creating email accounts that correspond to the addresses specified for deliveries and replies. Check with your messaging system administrator.

To configure addresses in Campaign interface, follow the steps below:

1. In the [delivery template](../../delivery/using/creating-a-delivery-template.md), click the **[!UICONTROL From]** link. In the **[!UICONTROL Email header parameters]** window, fill in the following fields:

    ![](assets/d_best_practices_email_header.png)

1. In the **[!UICONTROL Sender address]** field, make sure the address domain is the same as the sub-domain that you delegated to Adobe. You can change the part preceding the '@' but not the domain address.

1. In the **[!UICONTROL From]** field, use a name that is easily identifiable by the recipients, such as your brand's name, to increase the opening rate of your deliveries. To further improve the recipient's experience, you can add a person's name, for example "Emma from Megastore".

1. In the **[!UICONTROL Reply address text]** fiels, the sender's address is used by default for replies. However, Adobe recommends using an existing real address such as your brand's customer care. In this case, if a recipient sends a reply, the customer care will be able to handle it.

**Set up a control group**

Once the delivery is sent, you can compare the behavior of the excluded recipients with the recipients who did receive the delivery. You can then measure the efficiency of your campaigns. Learn more about control groups [this section](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

To set up a control group, click the **[!UICONTROL To]** link. In the **[!UICONTROL Select target]** window, select the **[!UICONTROL Control group]** tab. You can extract a portion of the target, for example a 5% random sample.

   ![](assets/d_best_practices_control_group.png)

**Use typologies to apply filters or control rules**

A typology contains checking rules that are applied during the analysis phase, before sending any message.

In the **[!UICONTROL Typology]** tab of the template's properties, change the default typology according to your needs.

For example, to better control the outbound traffic, you can define which IP addresses can be used by defining one affinity per sub-domain and creating one typology per affinity. The affinities are defined in the instance's configuration file. Contact your Adobe Campaign administrator.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## Design and personalize {#design-and-personalize}

When designing your message content, try to avoid common issues that could prevent you from executing your delivery. Most of the time, possible errors are related to [personalization](../../delivery/using/about-personalization.md), [formatting](../../delivery/using/defining-the-email-content.md#message-content) and [images](../../delivery/using/defining-the-email-content.md#adding-images).

### Optimize personalization {#optimize-personalization}

To avoid common issues that could prevent you from executing your delivery and to improve your recipients' experience, Adobe Campaign enables you to personalize your messages.

You can use recipients' data stored in the Adobe Campaign database, or collected through tracking, landing pages, subscriptions, etc.
Personalization basics are presented in [this section](../../delivery/using/personalization-fields.md).

Make sure your message content is properly designed to avoid any errors, which are generally related to personalization.

**Tips**: In personalization fields coming from external files provided by third-party vendors, external HTML content can be wrong. To avoid this, check syntax, use of tags, characters, etc. For example, an Adobe Campaign personalization tag always has the following form: <%=table.field%>. For more on this, see [this section](../../delivery/using/about-personalization.md).

The incorrect use of parameters in personalization blocks can be an issue. For example, variables in JavaScript should be used as follows:

    <%

    var brand = "xxx"

    %>

For more on personalization blocks, refer to the [this section](../../delivery/using/personalization-blocks.md).

You can prepare personalization data in a workflow to improve delivery preparation analysis. This should be used specially if the personalization data come from an external table through Federated Data Access (FDA). This option is described in this [this section](../../delivery/using/personalization-fields.md#optimizing-personalization)

### Build optimized content {#optimize-content}

When building your emails, keep the general best practices below in mind.

* Keep design simple

* Keep mobile users in mind

* Avoid entirely image-based emails

* Use email-safe fonts

* Encode special characters

**Subject line** - Work on the [subject line](../../delivery/using/defining-the-email-content.md#message-content) to improve open rates:

* Avoid subjects that are too long. Use 50 characters maximum

* Avoid using repetitively words like "free" or "offer", that could be considered as spam

* Avoid capital letters, and special characters like "!", "£", "€", "$"

**Mirror page** - Always include a mirror page link. Preferred position is a the top of the email. [Learn more](../../delivery/using/sending-messages.md#generating-the-mirror-page) 

**Unsubscription link** - The unsubscription link is essential. It must be visible and valid, and the form must be functional. By default, when the message is analyzed, a [typology rule](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) checks whether an opt-out link has been included and generates a warning if it is missing.

**Tip**: Because human error is always possible, check that the opt-out link works correctly before each time you send. For example, when sending the proof, make sure the link is valid, that the form is on-line and that the No longer contact this recipient field is changed to Yes.

Learn how to insert an opt-out link [in this section](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

**Email size** - To avoid performance or deliverability issues, the recommended maximum size of an email is about **35KB**. To check the message size, go the **[!UICONTROL Preview]** tab and choose a test profile. Once generated, the message size will be displayed in the top right corner.

To keep your email under the limit, consider the following:

* Remove redundant or unused styles

* Move some of the email content to a landing page

* Minify your code

Make sure to test any changes before the final sending

**SMS length**

By default, the number of characters in an SMS meets the GSM (Global System for Mobile Communications) standards. SMS messages using GSM encoding are limited to 160 characters, or 153 characters per SMS for messages sent in multiple parts.

Transliteration consists of replacing one character of an SMS by another when that character is not taken into account by the GSM standard. Note that inserting personalization fields into the content of your SMS message may introduce characters that are not taken into account by the GSM encoding. You can authorize character transliteration by checking the corresponding box in the SMPP channel settings tab of the corresponding **[!UICONTROL External account]**. 
Learn more [in this section](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Tips**:

* To keep all of the characters in your SMS messages as they are, to not alter proper names for example, do not enable transliteration.

* However, if your SMS messages contain a lot of characters that are not taken into account by the GSM standard, enable transliteration to limit the costs of sending your messages.

Learn more [in this section](../../delivery/using/sms-channel.md#about-character-transliteration).

### Work on formatting {#formatting}

To avoid common formatting errors, check the following elements:

* Correct **date formatting**: Adobe Campaign provides date formatting functions for the JavaScript templates and XSL stylesheets. [Learn more](../../delivery/using/formatting.md#date-display)

* Usage of **authorized characters** in emails: the list of valid characters for email addresses is defined in the "XtkEmail_Characters" option. Learn how to access Campaign options [in this section](../../installation/using/configuring-campaign-options.md). To correctly handle special characters, Adobe Campaign needs to be installed in Unicode. 

* Configuration of **Email Authentication**: make sure that the email headers contain the DKIM signature. DKIM (Domain Keys Identified Mail) authentication allows the receiving email server to verify that a message was indeed sent by the person or entity it claims it was sent by, and whether the message content was altered in between the time it was originally sent (and DKIM "signed") and the time it was received. This standard typically uses the domain in the From or Sender header. For more on this, refer to [this section](../../delivery/using/technical-recommendations.md#dkim).

* **Responsive email design** ensures that an email renders optimally for the device on which it is opened. 

    * Use responsive email HTML rather than web HTML.

    * Use the preview mode and send proofs to test the rendering on as much devices as possible.

    * The Adobe Campaign Classic Digital Content Editor (DCE) module includes some responsive design formatted templates for mobile available via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Learn more [in this article](https://theblog.adobe.com/responsive-email-design-101/).



### Manage images {#manage-images}

Follow the guidelines below when it comes to using images.

* **Prevent images blocking** - Some email clients block images by default, and some users change their settings to block images for saving on data usage. Therefore, if images are not downloaded, the whole message can be lost. To avoid this:

    * Balance your content with image and text. Avoid entirely image-based emails.

    * If text must be contained in an image, use alt and title text to make sure your message gets across. Style your alt/title text to improve its appearance.

    * Avoid the use of background images as they are not supported by some email clients.

* **Make images responsive** - Try to make images responsive and resizable. Note that this can have a cost impact as it takes longer to build.

* **Use absolute image references** - To be accessible from the outside, the images used in emails and public resources linked to campaigns must be present on an externally accessible server.

    * You can check if the instance configuration enables public resource management. [Learn more](../../installation/using/deploying-an-instance.md#managing-public-resources)
    
    * From the delivery wizard, you can import an HTML page containing images or insert images directly using the HTML editor via the **[!UICONTROL Image]** icon. [Learn more](../../delivery/using/defining-the-email-content.md#adding-images)

    * If images are not displayed, check that the images are available on the server. To do this, click the Source tab from your delivery. Find your images and copy-paste each image's URL in a web browser. If the images are not displayed, contact your IT administrator or the third-party vendor providing your delivery content.

### Preview your message {#preview-msg}

Adobe recommends previewing your message to check its personalization and how your recipients will see your delivery. 

* In the delivery wozard, the **[!UICONTROL Preview]** sub-tab lets you view the rendering of each content for a recipient. The personalization fields and the conditional elements of content are replaced with the corresponding information for the selected profile. [Learn more](../../delivery/using/defining-the-email-content.md#message-content)

*  An automatic anti-spam checking is performed during each preview. In the **[!UICONTROL Preview]** sub-tab, check [SpamAssassin](../../delivery/using/spamassassin.md) spam scoring.  Click **[!UICONTROL More...]** to find out more about the warning.  Before doing so, make sure SpamAssassin is correctly installed and configured on the Adobe Campaign application server. [Learn more](../../installation/using/configuring-spamassassin.md)

## Define the right target {#define-the-right-target}

Targeted population is key: build your lists carefully, test your emails on popular email clients and mobile devices, and ensure that your email lists are up-to-date (with no unknown or obsolete addresses). You can also send proofs that help set up a complete validation cycle.

Learn more about target populations [in this section](../../delivery/using/steps-defining-the-target-population.md)

### Target the right audience {#target-the-right-audience}

When you have your content ready, you need to carefully define who will receive your message.

To make your delivery successful, you want to send the most relevant personalized content to the right recipients. Adobe Campaign enables you to build the most accurate target: you can select recipients according to their age, localization, what they bought, if they clicked a link in a previous delivery, etc. With Adobe Campaign, you can also define test profiles, control groups and seed addresses to make sure your target is correct.

### Target mappings {#target-mappings}

In Campaign Classic, by default, delivery templates target **Recipients**. Adobe Campaign offers other target mappings for your deliveries, that you can change based on your needs.

For example, you can deliver to visitors whose profiles have been collected via social networks or to visitors who are subscribed to an information service.

These mappings are presented [in this section](../../delivery/using/selecting-a-target-mapping.md).

You can also create and use a customized target mapping. For more on this, refer to [this section](../../configuration/using/target-mapping.md).

### External recipients {#external-recipients}

You can deliver to recipients who are stored in an external file rather than saved in the database. Learn more [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

### Send to your subscribers {#send-to-subscribers}

To send messages to the subscribers of a newsletter, you can directly target the subscribers to the corresponding information service. Learn more [in this section](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


### Test recipients and seed addresses {#test-recipients-seed-addresses}

To test your delivery, use proofs before sending to the main target.

Make sure you select appropriate proof recipients, because they validate the form and the content of the message. The steps for defining the proof recipients are presented [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Seed addresses are used to target recipients who do not match the defined target criteria in order to test a delivery before sending to the main target. They are presented [in this section](../../delivery/using/about-seed-addresses.md).

### Deduplicate addresses {#deduplicate-addresses}

It is important to avoid having duplicate email addresses, because this can have an impact on your target:

* The same message can be sent more than once when a target is split.

* If a recipient unsubscribes after receiving a message, their duplicate profile will still receive future messages.

Deduplicating addresses protects your sending reputation and ensures good quarantine management.

Learn more [in this use case](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery).


### Index email addresses {#index-addresses}

To optimize the performance of the SQL queries used in the application, an index can be declared from the main element of the data schema.

The steps for adding an index to the email address are presented [in this section](../../configuration/using/database-mapping.md#indexed-fields).

## Perform all checks before sending {#perform-all-checks}

Once your message is ready, make sure its content is displayed correctly, on all devices, and does not contain any errors such as wrong personalization or broken links.

Before sending your message, also ensure that the parameters and configuration are consistent with the delivery.

### Validation is key {#validation-is-key}

Before sending a delivery, you need to ensure that your recipients will receive the message that you really want to send them. To do this, you need to validate the message content and delivery parameters.

This step enables you to detect possible errors and fix them before delivering to your main target.

The steps for validating a delivery are presented [in this section](../../delivery/using/steps-validating-the-delivery.md).

### Inbox rendering {#inbox-and-email-rendering}

Inbox rendering enables you to preview your messages on major email clients, scan content and reputation, discover how recipients are reading messages.

**Tips**:

* You can view the sent message in the different contexts in which it may be received: webmail, message service, mobile, etc.

* Inbox rendering capabilities are crucial to identifying whether your email campaigns successfully make it past the filters of major ISPs (Internet Service Providers) and webmail services. Such tools send a pre-flight copy of an email to a network of test inboxes, so you can see how the message will display, or render, across these services. They may also include reports and code correction options that help you quickly identify and make fixes that improve deliverability.

Learn more [in this section](../../delivery/using/inbox-rendering.md).

### Proof messages {#proof-messages}

Sending proofs enables you to check the opt-out link, mirror page and any other links, validate the message, verify that images are displayed, detect possible errors, etc. You may also want to check your design and rendering on different devices.

Learn more [in this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Set up A/B testing deliveries {#a-b-testing-deliveries}

If you have several contents for an email delivery, you can use A/B testing to find out which version will have the biggest impact on the targeted population.

**Tips**:

* Send the different versions to some of your recipients

* Select the one with the highest success rate and send it to the rest of your target

Learn more [in this section](../../workflow/using/a-b-testing.md).

### Make sure your message is delivered {#make-sure-your-message-is-delivered}

As a final step, maximize your chances and leverage the power of Adobe Campaign Classic to ensure that your message will be indeed delivered to the relevant recipients.

**Go through a validation process** - You can define a full validation process, involving Adobe Campaign operators and groups, to validate both the target and the message content. This will ensure full monitoring and control of the various processes of the campaign: targeting, content, budget, extraction, and sending a proof. Depending on their permissions, users will be notified, receive proofs and be able to validate or reject the message. Learn more [in this section](../../campaign/using/marketing-campaign-approval.md#approval-process).

**Use waves** - You can progressively increase the volume sent using waves. This will avoid your messages being marked as spam or when you want to restrict the number of messages per day. Using waves you can divide deliveries into several batches instead of sending high volumes of messages at the same time. Learn more [in this section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

**Prioritize messages** - You can set the sending order for your deliveries by stating the priority level. To do so:

1. Edit the delivery properties, and select the **[!UICONTROL Delivery]** tab.

1. Define the priority level for the delivery on a scale from **[!UICONTROL Very low]** to **[!UICONTROL Very high]**.

>[!NOTE]
>
>It is not possible to define the order of sending messages from within a delivery.

**Setup IP Affinities** - To better control the outbound SMTP traffic, you can manage affinities by defining which specific IP addresses can be used for each affinity. This lets you restrict the number of emails for specific deliveries towards machines or output addresses. For example, you can use one affinity per country or sub-domain. You can then create one typology per country and link each affinity to the corresponding typology.

You can:

* Define the IP affinities in the serverConf.xml configuration file. [Learn more](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* For each IPAffinity element, declare the IP addresses that can be used. [Learn more](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* In the [typology](../../campaign/using/about-campaign-typologies.md) of your choice, use the **[!UICONTROL Managing affinities with IP addresses]** field to link deliveries to the delivery server (MTA) which manages the said affinity. [Learn more](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Once the email is sent, check the header to verify which IP address the delivery was sent from. Your email administrator should help you obtain the header information.

>[!NOTE]
>
>Most of these steps can only be performed by an expert user.

**Use typologies** - You can use typology rules to exclude part of the target based on specific criteria. This guarantees that the messages sent best meet the needs and expectations of customers, in keeping with company communication policies. For example, you can filter the recipients who are underage from the target of your newsletter. Learn more [in this example](../../campaign/using/filtering-rules.md).

**Avoid attachments** - Attachments remain one of the most common vectors for the proliferation of malware, most especially when they are sent in bulk. Include a secure link to the document instead of attaching it. This ensures an additional layer of security to prevent unintended redistribution, and vastly reduces the chances that the message will be rejected at inbound email gateways for message size or security reasons.

## Track and monitor {#track-and-monitor}

You clicked the Send button? Let's see what happens. Once the delivery is sent, Adobe Campaign enables you to keep track of the sent messages and discover how your recipients react to your delivery. This will help you improve future sending and optimize your next campaigns.

### Monitoring deliveries {#monitoring-deliveries}

To control your campaigns, you must ensure that the message has indeed been delivered to your recipients.

From Campaign delivery dashboard, you can check the processed messages and delivery audit logs.
You can also control the status of the messages in the delivery logs. [Learn more](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

What if the deliveries are not being sent and their status remains **Pending**?

* The execution process is waiting on the availability of some resources. The MTA may have not been started.
Check that your mta@instance modules are launched on your MTA servers and start the MTA module if necessary. [Learn more](../../production/using/administration.md).

* The delivery may be using an affinity that has not been configured on the sending instance.
Tip: Check the configuration of traffic management (IP affinity). For more on this, see Control outgoing SMTP traffic.

>[!NOTE]
>
>These steps can only be performed by an expert user.

### Tracking {#tracking-deliveries}

To better know the behavior of your recipients, you can track how they react to a delivery: reception, opening, clicks on links, unsubscriptions, etc. In Campaign Classic, this information is displayed in the Tracking tab of the recipients targeted by the delivery and in the Tracking tab of the delivery. In Campaign Standard, it is displayed in the Tracking logs tab of the delivery.

**Tip**: Message tracking is enabled by default. To configure URLs, select the Display URLs option in the lower section of the delivery wizard. For each URL of the message, you can choose whether to activate tracking.

For more on this, refer to the [Configuring tracking](../../delivery/using/how-to-configure-tracked-links.md) section and the [Tracking indicators](../../reporting/using/delivery-reports.md#tracking-indicators) description. 

### Delivery performances {#delivery-performances}

To measure the speed at which the messages are delivered, you can control the delivery throughput. The criteria are the number of messages sent per hour and the size of the messages (in bits per second). For more on this, see [Delivery throughput](../../reporting/using/global-reports.md#delivery-throughput).

**Tips**:

* Do not keep deliveries in failed state on the instance, as this maintains temporary tables and impacts the performance.

* Remove deliveries which are no longer needed and inactive recipients from the database to maintain address quality.

* Do no try to schedule large deliveries together. Please note that it can take 5 to 10 minutes to spread the load uniformly over the system.

## Delivery troubleshooting {#delivery-troubleshooting}

Specific actions can be performed when encountering issues with deliveries:

* [Deliverability issues](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Image display issues](../../production/using/image-display-issues.md)

* [Delivery performance issues](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Temporary files issues](../../production/using/temporary-files.md) - *on-premise customers only*
