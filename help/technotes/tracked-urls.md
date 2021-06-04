---
product: campaign
title: Technote
description: Technote
hide: yes
hidefromtoc: yes
---
# Tracked URLs signature issue {#tracked-urls}

Following recent changes, tracked URLs can fail when URL signature is active in Campaign. Some mailboxes can be more impacted than others, as some companies have specific security tools which can impact links and alter the URL signature mechanism.

As a consequence, Adobe recommends that you disable the signature mechanism for tracking links. This procedure fixes old tracking links except the ones received with a double escaping.

Note that unsubscription links can fail as any other links, the frequency is variable from host to host but is less than 1%.

**Are you impacted?**

To improve security, the signature mechanism for tracking links in emails has been introduced in [Campaign Gold Standard 8](../rn/using/gold-standard.md#gs8) - April 2020 - and is enabled by default for all customers starting Build 19.1.4 (9032@3a9dc9c) and Campaign 20.2.

If your environment is running on one of the versions listed below, you can be impacted:

* Gold Standard 8 to 11. [Learn more](../rn/using/gold-standard.md#gs-8)
* Campaign 21.1.1 (build 9277) to 21.1.2 (build 9282) releases. [Learn more](../rn/using/latest-release.md)
* Campaign 20.3.1 (build 9228) to 20.3.3 (build 9234) releases. [Learn more](../rn/using/release--20-3.md)
* Campaign 20.2.1 (build 9178) to 20.2.4 (build 9187) releases. [Learn more](../rn/using/release--20-2.md)
* Campaign 20.1.1 (build 9122) to 21.1.3 (build 9124) releases. [Learn more](../rn/using/release--20-1.md)
* Campaign 19.2.2 (build 9080) to 19.2.3 (build 9081) releases. [Learn more](../rn/using/release--19-2.md)
* Campaign 19.1.5 (build 9033) to 19.1.7 (build 9036) releases. [Learn more](../rn/using/release--19-1.md)

Learn how to check your version [in this section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**How to update?**

As a **hosted customer**, Adobe will be working with you to update your configuration shortly.

As an **on-premise/hybrid customer**, you need to update your configuration.

Follow the step below:

1. In the [server configuration file](../installation/using/the-server-configuration-file.md) (serverConf.xml), change **signEmailLinks** to **false**.
1. Restart the **nlserver** service.
1. On the tracking server, restart the web server (apache2 on Debian, httpd on CentOS/RedHat, IIS on Windows).

    ```
    nlserver restart web
    ```

>[!NOTE]
>
>The **config-`<instance>`.xml** file overrides the **serverConf.xml** settings. If the **signEmailLinks** is present in the  **config-`<instance>`.xml** (where **instance** is the name of your instance), it must also be turned to **false**.
>

**What is the impact?**

The maintenance requires a maximum of 25-minutes downtime and during this period all the deliveries, tracking links and API calls will not work.

Once the update is done, all links work as expected.

>[!NOTE]
>
>For any questions about these changes, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>
