---
title: About deliverability in Adobe Campaign Classic
description: Learn more about managing deliverability in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
---

# About deliverability {#about-deliverability}

Adobe Campaign offers a certain number of tools to track the deliverability performance of your platform. This section also highlights the main principles you should have in mind when managing and optimizing deliverability.

## Configuration {#configuration}

[TBC]
This feature is available through a dedicated package in Adobe Campaign. To use it, this package must be installed. Once done, restart the server for the package to be taken into account.

For hosted and hybrid clients, **Deliverability monitoring** is configured on your instance by Adobe technical support and consultants. For more information, contact your Adobe Account executive.
 
For on-premise installations, you must install the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package via the **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. For more on this, see [Installing Campaign Classic standard packages](../../installation/using/installing-campaign-standard-packages.md).
 
**Deliverability monitoring** is managed by the **[!UICONTROL Refresh for deliverability]** workflow. It is installed by default on all instances and lets you initialize the list of bounce mail qualification rules, the list of domains and the list of MXs. Once the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package is installed, this workflow runs nightly to regularly update the list of rules and enables you to actively manage platform deliverability.

## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)

## Data Quality {#data-quality}

The first fundamental of email deliverability success is data quality. Proper email database hygiene starts from the moment addresses are acquired - with proper consent, expectation-setting, and preference management - and is an ongoing process with specific best practices for handling inactive addresses, bounces, and unsubscribes. Collectively, these efforts are necessary to increase or maintain marketing reputation and ultimately achieve higher email deliverability rates and business results.

### Opt-In {#opt-in}

Permission is the starting point for all effective communications, whether online or offline. Active consent from your recipients is essential - and in many countries, required by law. At the very minimum, you should provide an unconfirmed opt-in, which allows individuals to subscribe to your list simply by entering their email address.

From a deliverability standpoint, though, the more preferred option is a double opt-in, which requires new subscribers to take explicit action, such as clicking a confirmation link, before they're added to the list. Double opt-in ensures that no person can subscribe someone else to your list out of malice or error, thus reducing bounces and unwarranted spam complaints.

Since web tracking is often used in tandem with email marketing, it's worth noting that the European Union's new Internet privacy rules require companies to receive opt-in consent to track individuals' actions online. These regulations apply not only to European companies, but to any business conducting online marketing campaigns in the 27 EU member countries.

### Welcome Message {#welcome-message}

It is important to send new subscribers a welcome message to establish the first contact and start building a relationship of trust. Even if your registration form clearly sets expectations, use the welcome email to remind them of the types of content or offers they'll be receiving, and at what frequency. A few recipients might rethink their choice and unsubscribe, but this is preferable to them submitting spam complaints down the road.

As an aside, don't overlook the revenue potential of welcome emails. Because it is the first email that subscribers receive, it often has the highest open, click, and conversion rates. In fact, welcome emails have transaction rates that are nine times higher than other promotional mailings2. The results are significantly better for real-time messages vs. bulk emails, so sending triggered welcome emails containing an offer can pay dividends for your business.

### Preference Centers {#preference-centers}

Consumers today exert greater control over how, when, and where they interact with brands. Rather than ignoring or fighting this trend, businesses should embrace it. Doing so can not only improve deliverability but drive better business results. Your preference center should allow consumers to explicitly state which products/topics interest them, which types of messages they wish to receive, how frequently they wish to be contacted, and through which channels. Advanced preference centers provide the granularity to indicate the frequency and channel for each type of message selected.

While this means you might send fewer messages overall, your communications will be much more targeted, relevant, and effective - dramatically reducing complaints while increasing engagement and response rates. Ultimately, this enhances your organization's IP reputation and ensures more messages reach the inbox.

### Inactive Addresses and Spam Traps {#inactive-addresses-and-spam-traps}

Inactive email addresses might seem perfectly harmless, but they can actually hinder your deliverability efforts - and in some cases, do major damage. For starters, engagement metrics (e.g. opens, clicks, etc.) are playing an increasingly prominent role in how Internet Service Providers (ISPs) determine mailbox placement. Consequently, emailing a lot of inactive addresses might hurt your reputation with some ISPs and lower your deliverability rate. Instead of continuing to send inactive users your standard emails, segment them for a win-back campaign; if they don't respond, stop emailing them altogether.

An even more dangerous deliverability threat is spam traps, which are email addresses used to identify and blacklist spammers. Often, valid email addresses that have been abandoned or inactive for a certain period of time are repurposed by ISPs as spam traps. Hitting one can lead your IP address to be blacklisted and your messages to be blocked. Hence, another important reason why inactive addresses should be removed from your list altogether.

### Bounce Management {#bounce-management}

Proper bounce management is an important email deliverability best practice. Repeatedly sending email to even a few bad addresses can get all your messages blocked by ISPs. Therefore, it's crucial to have strategies and processes in place for managing both hard bounces, emails that are permanently undeliverable, and soft bounces, emails that can't be delivered temporarily due because the recipient's mailbox is full, the server is down or overloaded, the message is too large, etc.

Hard bounces should be identified and automatically excluded from subsequent email campaigns. Soft bounces, on the other hand, can safely be retried up to five times; if these attempts aren't successful, the addresses should then be removed from the list. Because soft bounces may also be caused by temporary ISP blocking, it's also important to regularly investigate their cause in order to diagnose and correct any issues with authentication, volume, or reputation.

For more on this, refer to [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md).

### Data Hygiene {#data-hygiene}

In order to keep your reputation intact, be sure to perform regular database hygiene, removing duplicate records, undeliverables, and inactive or incorrect email addresses. If you buy or rent lists, make sure they are certified 'opt-in' records. In addition, send test messages to a small sample of the addresses to gauge the response - and potential for spam complaints.

When recipients unsubscribe, it is essential to keep a permanent record in your database to avoid soliciting them again and generating complaints that damage your marketing reputation. In general, remember that a hundred qualified addresses provide far more marketing potential than a thousand non-qualified addresses.

## Message and Content {#message-and-content}

You have taken the time to qualify your contacts and make sure your database is pristine. Now, don't waste the communication by neglecting the message. Every element of an email - from the reply-to address and subject line to the message body and HTML code - is important and should not be overlooked, both from a deliverability and overall campaign effectiveness standpoint.

### From/Reply-To {#from-reply-to}

Recipients must be able to identify the sender of any commercial email without having to open the message. Whether it contains the name of the brand or an individual at that company, the 'from' field must be clearly recognizable. Otherwise, you risk your emails being labeled as spam before they're even opened.

Another important consideration is the reply-to address. For optimal deliverability, it is recommended that you use a valid, existing email address (versus no-reply@domain. com) and actively encourage interaction. ISPs are increasingly factoring engagement metrics in their spam-detection algorithms. If recipients reply to a specific address enough times, it will automatically be added to their trusted contacts and have a better chance of reaching the inbox. Conduct polls, ask questions, request feedback - do whatever it takes to engage subscribers.

### Subject Line {#subject-line}

The subject line should provide a clear indication of the email's purpose rather than hide it. If this rule is violated, recipients will quickly log complaints that damage your reputation. In addition, subject lines should be brief (generally less than 45 characters), compelling, and action-oriented to drive recipients to open the message. Remember: higher engagement plays a role in deliverability; it also generates better results!

In addition, it's important to avoid special characters (!, ?, $) and to judiciously use words or phrases that could lead your email to be construed as spam. While the worst offenders can cause your emails to get caught in spam filters, another important element to consider is the perception of your recipients. Do frequent uses of words like "cheap","free", or "discount"; make them suspicious or s your emails - or worse, your brand? Negative perception can ultimately have as damaging an effect on deliverability.

### Message Body {#message-body}

The quality of your content is inextricably linked to how well you know each recipient. The better you understand their interests, preferences, and buying habits, the more relevant and effective your communications will be. Without this knowledge, it is better to send nothing at all than to run the risk of conveying a negative image of your company. Remember, some recipients will click the "report spam" button as a convenient way to unsubscribe from an email, even though it's not actual spam. In other words, sending irrelevant content can directly impact your deliverability.

Although graphics are an important element of emails, you'll want to use them in moderation. Otherwise, your messages could end up in junk or spam filters. A good best practice is to use 2/3 text and 1/3 images. In addition, multipart delivery lets you send both HTML and text versions of your message to increase your chances of it getting through. The recipient's mail software will select the format it prefers.

The purpose of every communication should be clearly stated somewhere in the message body. That's because your recipients cannot be expected to remember every email to which they have subscribed. Including a sentence such as "You are receiving this message because you subscribed to..." can help prevent errant spam complaints.

### Advanced Personalization {#advanced-personalization}

Certain messages are naturally geared towards certain segments of your database, and you should be able to easily target these audiences in the list selection process. Other communications, such as newsletters or fliers, are more general in nature, but that doesn't mean they should be any less relevant. Advanced personalization capabilities allow you to define rules for personalizing blocks of content within your message by audience segment or even recipient. The latter uses profile information and response history to serve up the best message or offer for each individual recipient. Again, heightened relevance goes a long way in warding off unnecessary spam complaints.

### Useful Links {#useful-links}

According to the CAN-SPAM Act, "a visible and operable unsubscribe mechanism" must be present in all emails. Although many companies often try to bury the unsubscribe link at the bottom of their emails, a better practice is to include it at the beginning. Otherwise, if recipients are forced to scroll all the way down, they may be tempted to click the "report spam" button instead. To further minimize friction, we recommend a one-step unsubscription process that doesn't require logging in or any additional action. Finally, recognizing that some recipients may unsubscribe simply by replying to the email, it's important to use a valid reply-to address.

Another best practice is to encourage recipients to add your email address to their address book or safe senders list to ensure that that future communications flow smoothly, with links and images activated by default. Beyond simply making the request, many businesses include a link to step-by-step instructions on how to whitelist an email address for each of the main ISPs.

### HTML Code {#html-code}

Using high-quality HTML code in email campaigns is critical to boosting deliverability, particularly in the desired format. Emails containing minor coding errors may trigger spam filters, as well as render poorly within the interfaces of many webmail services. Within certain email readers, the messages may even appear completely broken. Use code parsing tools (described further below) to remove redundant code and identify and fix errors.

It is also important to check the syntax of your HTML file for compliance with W3C standards if you want accessible, portable, and usable email messages. Because of the variety of web browsers and devices used today (e.g. computers, PDAs, smartphones, mobile phones, etc.), communication standards are essential to guaranteeing universal accessibility to digital content.

### Cross-Channel Approach {#cross-channel-approach}

Depending on each particular campaign and each particular customer, you might consider combining email with other communication channels, including direct mail, web, mobile, call center, point of sale, and social media. In some cases, you might use channels in tandem - for instance, sending a follow-up direct mail piece to recipients who responded to a specific email. In other cases, you might send your platinum customers a direct mail piece and everyone else an email with the same message.

This integrated cross-channel approach allows you to serve each customer via the most appropriate channel for that specific relationship and that specific message. In turn, you can better align resources and spend with business value.

## Sending Infrastructure {#sending-infrastructure}

The third fundamental of email deliverability success is the sending infrastructure. Since it's the critical link to ISPs and corporate mail servers, a proper sending infrastructure goes a long way towards eliminating potential bottlenecks and opening the floodgates for your messages. It can also automate many of the technical aspects of deliverability, reducing marketing's dependence on IT.

### IP Configuration {#ip-configuration}

Any new IP addresses should first be primed, a process known as IP warming. This is crucial to establishing a reputation as a legitimate email sender in the eyes of ISPs. When ISPs observe email coming from a new IP address, they immediately evaluate the traffic. Since volume is perhaps the most telling factor in terms of spam, it is best to start small and gradually increase the volume of emails. Sending too many messages out of the gate is a sure way to get your messages blocked.

As a best practice, we recommend having three distinct pools of IP addresses for email communications: one for prospects, one for customers, and one for transactional messages (e.g. notifications, password changes, etc.). The last is crucial. Although you may be marketing by the book, you don't want any deliverability issues stemming from promotional messages to taint your transactional email program. Transactional messages are important to customers - and a tremendous marketing opportunity, given their high open rate - so they must always get through.

In addition, we recommend maintaining a semi-backup IP address that is already warmed up. Ideally, your sending infrastructure will have load balancing capabilities for distributing messages across multiple IPs. This way, you can route a percentage of your emails via your semi-backup IP, keeping it warm at all times. You can also automatically switch over to a backup if your primary IP address is throttled or blacklisted. Otherwise, you will have to spend weeks or months warming a new IP, which could seriously impact your campaign results in the interim.

### Authentication {#authentication}

Authentication refers to the methods used by ISPs and corporate mail servers to identify and verify valid IPs/senders, thus preventing spam. There are four authentication systems: SPF (Sender Policy Framework), Domain Keys, DKIM (Domain Keys Identified Mail), and SenderID. Because of the pros and cons of each, ISPs use various combinations of these methods. Yahoo! Mail uses DKIM and Domain Keys, for instance, while Gmail uses DKIM, Domain Keys, and SPF. Until there's one universal standard, your sending infrastructure must support all four systems to prevent any deliverability problems.

### Volume Control {#volume-control}

ISPs use throttling mechanisms to control the volume of data traveling over their networks. If you attempt to open too many SMTP connections at the same time or send too many email messages within a short period, they'll quickly close the floodgates. When this happens, you are likely to receive errors such as 'timeout', 'server has exceeded the rate limit allowed', or 'too many connections from your IP'. To avoid these errors and keep your emails flowing, your sending infrastructure must be able to adapt to the rules set out in the ISP postmaster pages. These rules generally include: number of connections per sending IP address, number of messages per session, sending speed, and authentication rules. It's important to remember that a good IP reputation can help extend the throttling limits.

### Inbox Rendering {#inbox-rendering}

Inbox rendering capabilities are crucial to identifying whether your email campaigns successfully make it past the filters of major ISPs and webmail services. Such tools send a pre-flight copy of an email to a network of test inboxes, so you can see how the message will display, or render, across these services. They may also include reports and code correction options that help you quickly identify and make fixes that improve deliverability.

### Spam Scoring {#spam-scoring}

Also useful are spam scoring tools, which run a series of tests on an email campaign prior to delivery and calculate a score indicating the likelihood of it being treated as spam by ISPs. In general, any score above 2.0 will be considered spam by most ISPs. Often, a diagnosis is appended to this score, allowing marketers to identify corrective action to be applied to the content.

### Controlling Pressure {#controlling-pressure}

To achieve optimal results from your email campaigns while protecting your reputation, it is essential to control pressure in order to avoid over-soliciting your contacts. Your sending infrastructure should be able to handle this consideration in real time, using pre-defined rules to automatically exclude contacts that have received a certain number of messages within a given timeframe. Keep in mind that reacquisition is significantly more expensive than retention, so the cost associated with losing subscribers eradicates any additional revenues generated by sending more emails.

## Reputation {#reputation}

The last and most important fundamental is reputation. Great email deliverability programs are built on a great marketing reputation, both with ISPs and recipients. When you think about it, the first three fundamentals outlined in this white paper - data quality, message and content, and sending infrastructure - ultimately boil down to best practices for building or protecting your reputation. There are a few additional tools that can help you monitor and enhance your reputation, and ensure optimal deliverability rates. They are described below.

### IP Reputation and RBLs {#ip-reputation-and-rbls}

The reputation of your IP addresses has a major impact on how quickly your email messages are delivered - or whether they reach the inbox at all. Like a credit score, IP reputation is an indication of the trustworthiness of an email sender. If your reputation is bad or non-existent, ISPs may choose to block your messages altogether, which could be devastating to your business. Reputation also determines whether ISPs throttle your messages, which is the process of controlling or limiting their average throughput. When communications are urgent or time-sensitive, throttling can be just as harmful as being blocked.

In order to build and maintain a good IP reputation, you must route regularly with consistent volumes. When you do increase the volume, it should be done gradually over time, as any sudden spikes or drops might be perceived as suspicious (i.e. spammy) activity and therefore hurt your IP reputation.

To track your reputation, refer to the main real-time blacklists (RBLs), such as SpamCop, SpamHaus, etc. RBLs are databases that contain the IP addresses of known spammers, as well as IPs with open mail relays, as spammers can easily use these systems to send out spam. All modern mail transport agents (mail servers) can be configured to automatically reject messages sent from a site listed on an RBL. Consequently, ending up on an RBL is a near-guarantee that your emails won't be delivered. It bears repeating that this can be detrimental not only to your marketing efforts but your business results.

<!--### Non-Commercial White Lists {#non-commercial-white-lists}

Non-commercial white lists are maintained by the primary ISPs and email services such as Yahoo! and AOL. Inclusion on these white lists grants faster delivery, including via lifting of the "throttling" filter.

In order to be accepted to non-commercial white lists, email senders must pass a series of tests based on a verification of their infrastructure (for instance, they must have static IP addresses, and their server must not be configured as an open mail relay), and of their activity (campaign frequency, volume, number of complaints, etc.). If any of these rules are breached, the sender may be removed from the white list.

### Commercial White Lists {#commercial-white-lists}

Commercial white lists are based on a system that allows the sender to bypass antispam filters altogether or be assigned incremental points as they enter the system. Those commercial white lists operate on a CPM (cost per thousand) or annual basis and are offered by independent commercial organizations such as Return Path. ISPs are free to use those services and the number that do vary depending on each white list.

A sender that has been certified may then be more confident as it executes new campaigns. Some white lists also facilitate opening of images in Webmail interfaces and activation of hyperlinks. Certification on such commercial white lists has undeniable upside for email marketers.-->

### IP Certification {#ip-certification}

IP Certification is a whitelisting and sending practices program that helps ensuring that emails are received without being blocked by antispam filters or other email blocking systems.

Currently two providers offer IP Certification: Return Path and Certified Senders Alliance.

Certified senders are added to email whitelists which are used by global mailbox providers and email security companies. These commercial whitelists are based on a system that allows the sender to bypass antispam filters altogether or be assigned incremental points as they enter the system.

The [Return Path Certification](https://www.validity.com/products/returnpath/certification/) program offers a number of benefits, including the following:

* A measurable increase in inbox placement at top mailbox providers like Microsoft, AOL, Yahoo, Gmail, Comcast, Orange, Mail.ru, and more
* Favorable reputation and treatment at critical filters like Cloudmark, SpamAssassin, and Cisco Ironport
* A compliance team dedicated to 24/7 monitoring, providing with security alerts and working with you through the resolution of any compromises
* Mailbox provider data delivering detailed information about KPIs, placement, and Certification performance
* Simplified and faster IP warming, including stronger reputation and recognition when migrating or obtaining a new IP address

The [Certified Senders Alliance](https://certified-senders.org/certification-process/) Certification offers amongst other benefits:

* Certification of senders of commercial emails who can comply with high quality standards
* Improved delivery and deliverability of commercial emails to increase the inbox placement rate and reduce spam filtering
* Protection from legal and financial risks by fully complying with legal standards
* Protecting reputation by means of early warnings from the CSA Complaints Office and daily spam trap reports

ISPs are free to use these services and the number of ISPs can vary depending on the whitelist.

However, because more and more ISPs build their antispam filters based on each inbox owner's behavior rather than analyzing the message content itself, using IP Certification cannot be a guarantee of inbox placement or even delivery.

### Email Monitoring Reports {#email-monitoring-reports}

Throughout the campaign and after each delivery, it is important to monitor the delivery rate in order to readjust the settings, correct any problems, and ensure a stellar reputation. Consequently, your system should have built-in reports that - for every domain name and primary webmail service - measure the number of emails received in the inbox, spam folder, or flagged as "undelivered". There should also be diagnostic reports for analyzing the reasons for failed deliveries, as well as more granular reports for identifying deliverability rates and response rates for individual ISPs.

As a general best practice, we recommend the use of seed lists: a list of email addresses spanning the major ISPs that is used to monitor email delivery. Seed lists often power the inbox rendering capabilities described above. They should also be incorporated into the main email monitoring reports, so you can see how your main target list is performing against the seed list.

For more on this, refer to [Monitoring a delivery](../../delivery/using/monitoring-a-delivery.md).

### Technical Monitoring Reports {#technical-monitoring-reports}

In addition, technical teams need reports that help them to quickly identify the potential root cause of a sudden drop in deliverability. These reports offer comprehensive diagnostics that bring together the primary indicators of an email delivery platform, including SPF verifications, DomainKeys, reverse DNS, connectivity and reporting from the primary RBL lists for each IP and domain used during the email delivery process.

### Complaint Handling {#complaint-handling}

Even if your practices are professional, you are not immune to mistakes, and the handling of complaints from recipients needs to be considered. To do this, you can set up a feedback loop that informs you of any complaints received by your ISP following the sending of your campaigns. For more on this, refer to [Feedback loop](../../delivery/using/technical-recommendations.md#feedback-loop).

Once the request has been accepted by your ISP, your system should automatically quarantine these e-mail addresses, preventing future communication. With the same aim in mind, be sure to process messages received in mailboxes such as postmaster@company.com and abuse@company.com. The goal is to ensure your complaint rate does not exceed .3% per ISP at any point, as this key metric determines whether your messages are delivered or not.
