---
title: Key points when managing deliverability in Adobe Campaign Classic
description: What are the key points to check when managing deliverability in Adobe Campaign Classic?
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

# Deliverability troubleshooting{#deliverability-faq}

Are you experiencing a deliverability problem? You may find the solution here.

## MX rule error {#mx-rule-error}

**What does the error message 'quotas met' mean?**

This message indicates that you have reached the quota limit for a specific MX and that you have to wait to be able to send another email to this provider.

In Adobe Campaign, there is a configuration regarding the number of emails per hour that can be sent. This configuration must be used with vigilance, as the number defined in the instance concerns the number of connections carried out with the ISP and not the number of emails actually sent.

This means a connection can use an MX rule without successfully sending an email. In this case, a configuration with an IP or a domain with a low reputation will have to try several connections before sending an email. For each attempt, a messages per hour credit will be used. As a result, the marketing campaign performance will be significantly impacted.

Therefore, 'quotas met' is not only a configuration issue, but can also be linked to reputation. It is important to analyze error messages in the [SMTP log](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

For more on MX configuration, see [this section](../../installation/using/email-deliverability.md#mx-configuration).

## Same error message for an ISP {#same-error-for-an-isp}

**Why do I always get the same error message for a particular ISP?**

If you always get the same error message for an ISP, your email or IP may have been detected as faulty by the ISP. Carry out the following recommendations:
* Check whether you receive a large percentage of failures linked to inexistent email addresses (**User unknown** failures).
* Update your subscription forms to detect any errors in the domain names entered (for example: gmaul.com or yaho.com).
* If you notice errors stating that your messages are declared as spam, or that your messages are constantly blocked, try excluding the recipients that have not opened or clicked in one of your messages in the last 12 months from the target.

If the problem persists, contact the commercial or deliverability services, Adobe Campaign Client Care or Adobe Campaign support.

## Block list versus quarantine {#block-list-versus-quarantine}

* **What is the difference between an email address on the block list and a quarantined email address?**

    * The status **[!UICONTROL On block list]** is a result of a feedback loop (when a person reports a message as spam).

    * The status **[!UICONTROL Quarantined]** is a result of a soft or hard bounce.
    
    For more on this, see [this section](../../delivery/using/understanding-quarantine-management.md##quarantine-vs-block-list).

* **What do the different quarantine error reasons mean?**

    Here are 10 possible reasons: not defined, user unknown, invalid domain, address on block list, refused, error ignored, unreachable, account disabled, mailbox full, not connected.
    
    For more on this, see [Understanding quarantine management](../../delivery/using/understanding-quarantine-management.md).

## Removing from block list {#remove-from-block-list}

* **One of my recipients was added to the block list by mistake. How do I remove them from the block list so that I can start sending them messages again?**

    * Go to **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
    * In the details of the corresponding record, set the value of the **[!UICONTROL Status]** field to **[!UICONTROL Valid]**.
    * Save the record.

* **How can I find out whether one of my IPs is on a block list? How do I remove my IP(s) from a block list?**

    To check whether your IP address is on a block list, you can use various web sites to verify it, such as:
    * [MX Toolbox](https://mxtoolbox.com/)
    * [What is my IP address](https://whatismyipaddress.com)

    Generally, the result of the IP address check will return a list that contains details of the block list and also the name of the web site that blocked the IP address.

    By clicking the corresponding link, you can access the web site details. Then, you can request that your web site be delisted from the web site that added the IP address to its block list.

    >[!NOTE]
    >
    >The delisting process may vary depending on the web site. Some sites require you to create an account, while others just need you to provide the IP address.

## Best practices {#best-practices}

Below are a few best practices that can help to identify and address deliverability issues.

### Identify a deliverability issue {#identify-deliverability-issue}

The following elements may draw your attention:

* Mailing or campaign metrics: unsubscribe, abuse complaint and/or bounce rates are higher than usual.
* Subscriber activity: opens, clicks and/or transactions are lower than usual.
* Seed accounts show filtered or non-delivered mailings.

### Hypothesize potential causes {#potential-causes}

Ask yourself the following questions to identify the possible causes to your deliverability issue:

* Was there a recent change in list segmentation?
* Have I acquired any new data sources?
* Did I accidentally mail a quarantine file?
* Could the problem be due to my message content?
* Do I mail frequently enough to maintain warm IPs?
* Am I segmenting my mailings by activity/engagement, or sending full-files?
* What is the 'safe' segment on my file in terms of recency?
* Do I have reactivation & reconfirmation strategies in place for segments that are not defined as safe?

### Address the issue {#address-issue}

**Complaints**

Complaints are defined by subscribers who **report email as a spam** by hitting the corresponding button from their inbox.

If your delivery issue was caused by complaints:
* You need to try to determine why recipients are complaining.
* You may also want to consider moving your unsubscribe link to the top of your email. This will encourage subscribers to unsubscribe instead of complaining with the spam button.

Senders can glean a wealth of information from their [feedback loop](../../delivery/using/technical-recommendations.md#feedback-loop) complaints:
* It is important to bucket the data and look for patterns in things like opt-in source, how long the address has been subscribed, or even certain behavioral demographics.
* Complaints can often identify a risky data source or segment within the file. Risky is defined as most likely to complain, which can damage reputation, and in turn, inbox rates.

Complaints also stem from subscribers who just no longer want to receive email:
* This can often be due to over-messaging, your subscribers' perception of the message, that they were not expecting the message, or do not recall opting in.
* It is also important to run an audit to ensure that all points of collection are clear, and that there are no pre-checked boxes in your points of acquisition.
* You should also send a welcome email when subscribers opt-in to set the tone and explain how often they can expect to receive emails from you.

**Data validity**

**Hard bounces** occur when you send to an **undeliverable address** at an ISP. An address can be undeliverable for many reasons such as:
* Misspelled address. This can be addressed with a real-time data validation service, or by requiring a confirmed opt-in before sending marketing emails to that address.
* Bad list or data source. If it comes from a new source, review how the addresses were collected and ensure that there was permission.
* Mailing to an address that was at one time active, but has been closed or terminated after a period of inactivity.

**Engagement**

In addition to complaints and data validity, ISPs are concentrating more than ever on **positive engagement** to make delivery decisions. They are looking to see whether your subscribers are opening your emails, or deleting them without reading them. Because they don’t share this data with senders, we must utilize the information that we have available and translate opens/clicks/transactions as engagement. 

As part of ongoing reputation maintenance, it is important to understand how engaged subscribers are on your list and develop a **recency risk hierarchy** for the subscribers on each file. Recency is defined as last open/click/transact or sign-up date. This time-frame may differ by vertical. To do this:

1. Determine active (‘safe’) segments for each vertical. This is typically subscribers who have been active within the last 3-6 months.
1. Reduce frequency to inactives.
1. Create a [re-engagement](../../delivery/using/re-engagement-best-practices.md) series for moderate risk inactives. This is typically 6-9 months without engagement.
1. Develop a reconfirmation campaign for higher risk inactives. This is typically subscribers who haven’t engaged with an email in 9-12 months.
1. Finally, set a drop-off rule and remove subscribers who haven’t opened your emails in 'x' months. We typically recommend 12+ months, but this can differ based on sales and buying cycle.
