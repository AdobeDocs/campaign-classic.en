---
product: campaign
title: Key points when managing deliverability in Adobe Campaign Classic
description: Learn key points to check when managing deliverability in Adobe Campaign
feature: Deliverability, Troubleshooting
role: User
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
TQID: https://experienceleague.adobe.com/ZRai7Bd-IRaWUQQmkuUYwXhNXp2BI-B4k-4cGq1k6uk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer (Campaign)
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages (Campaign)
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging (Campaign)
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design (Campaign)
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing (Campaign)
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability (Campaign)
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
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
    
    For more on this, see [this section](delivery-failures-quarantine.md#quarantine-vs-denylist).

* **What do the different quarantine error reasons mean?**

    Here are 10 possible reasons: not defined, user unknown, invalid domain, on denylist, refused, error ignored, unreachable, account disabled, mailbox full, not connected.
    
    For more on this, see [Understanding quarantine management](delivery-failures-quarantine.md).

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
