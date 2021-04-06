---
solution: Campaign Classic
product: campaign
title: Key points when managing deliverability in Adobe Campaign Classic
description: What are the key points to check when managing deliverability in Adobe Campaign Classic?
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
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

If the problem persists, contact the commercial or deliverability services, [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Denylist versus quarantine {#denylist-versus-quarantine}

* **What is the difference between a email address on denylist and a quarantined email address?**

    * The status **[!UICONTROL Denylisted]** is a result of a feedback loop (when a person reports a message as spam).

    * The status **[!UICONTROL Quarantined]** is a result of a soft or hard bounce.
    
    For more on this, see [this section](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist).

* **What do the different quarantine error reasons mean?**

    Here are 10 possible reasons: not defined, user unknown, invalid domain, on denylist, refused, error ignored, unreachable, account disabled, mailbox full, not connected.
    
    For more on this, see [Understanding quarantine management](../../delivery/using/understanding-quarantine-management.md).

## Removing from denylist {#remove-from-denylist}

* **One of my recipients was added to denylist by mistake. How do I remove them from the denyist so that I can start sending them messages again?**

    * Go to **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
    * In the details of the corresponding record, set the value of the **[!UICONTROL Status]** field to **[!UICONTROL Valid]**.
    * Save the record.

* **How can I find out whether one of my IPs is on a denylist? How do I remove my IP(s) from a denylist?**

    To check whether your IP address is on a denylist, you can use various web sites to verify it, such as:
    * [MX Toolbox](https://mxtoolbox.com/)
    * [What is my IP address](https://whatismyipaddress.com)

    Generally, the result of the IP address check will return a list that contains details of the denylist and also the name of the web site that denied the IP address.

    By clicking the corresponding link, you can access the web site details. Then, you can request that your web site be delisted from the web site that added the IP address to its denylist.

    >[!NOTE]
    >
    >The delisting process may vary depending on the web site. Some sites require you to create an account, while others just need you to provide the IP address.
