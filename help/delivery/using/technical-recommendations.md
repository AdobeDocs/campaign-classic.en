---
solution: Campaign Classic
product: campaign
title: Technical recommendations for improving deliverability with Adobe Campaign Classic
description: Discover techniques, configurations, and tools that you can use to improve your deliverability rate with Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
---

# Technical recommendations{#technical-recommendations}

Several techniques, configurations, and tools that you can use to improve your deliverability rate are listed below.

## Configuration {#configuration}

### Reverse DNS {#reverse-dns}

Adobe Campaign checks whether a reverse DNS is given for an IP address and that this correctly points back to the IP.

An important point in the network configuration is making sure a correct reverse DNS is defined for each of the IP addresses for outgoing messages. This means that for a given IP address, there is a reverse DNS record (PTR record) with a matching DNS (A record) looping back to the initial IP address.

The domain choice for a reverse DNS has an impact when dealing with certain ISPs. AOL, in particular, only accepts feedback loops with an address in the same domain as the reverse DNS (see [Feedback loop](#feedback-loop)).

A tool is available to verify the configuration of a domain: [https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx).

### MX rules {#mx-rules}

MX rules (Mail eXchanger) are the rules that manage communication between a sending server and a receiving server.

More precisely, they are used to control the speed at which the Campaign MTA (Message Transfer Agent) sends emails to each individual email domain or ISP (e.g. hotmail.com, comcast.net). These rules are typically based on limits published by the ISPs (e.g. do not include more than 20 messages per each SMTP connection).

For more on MX management, refer to [this section](../../installation/using/email-deliverability.md#mx-configuration).

### TLS {#tls}

TLS (Transport Layer Security) is an encryption protocol that can be used to secure the connection between two email servers and protect the content of an email from being read by anyone other than the intended recipients.

<!--#### Configuring the application {#configuring-the-application}

To define the domain used for the HELO command, edit the instance's configuration file (conf/config-instance.xml) and define a "localDomain" attribute as follows:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

The MAIL FROM domain is the domain used in technical bounce messages. This address is defined in the deployment wizard or via the NmsEmail_DefaultErrorAddr option.

#### DNS configuration {#dns-configuration}

An SPF record can currently be defined on a DNS server as a TXT type record (code 16) or an SPF type record (code 99). An SPF record takes the form of a character string. For example:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

defines the 2 IP addresses 12.34.56.78 and 12.34.56.79 as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

Recommendations for defining an SPF record:

* Add **~all** (SoftFail) or **-all** (Fail) at the end to reject all servers other than those defined. Without this, servers will be able to forge this domain (with a Neutral evaluation).
* Do not add **ptr** (openspf.org recommends against this as costly and unreliable).-->

## List-Unsubscribe {#list-unsubscribe}

### About List-Unsubscribe {#about-list-unsubscribe}

Adding an SMTP header called **List-Unsubscribe** is mandatory to ensure optimal deliverability management.

This header can be used as an alternative to the "Report as SPAM" icon. It will display as an unsubscription link in the email interface.

Using this functionality helps to protect your reputation and feedback will be executed as an unsubscription.

>[!NOTE]
>
>This functionality is available from Build 6831.

To use List-Unsubscribe, you must enter a command line similar to as follows:

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

>[!IMPORTANT]
>
>The example above is based on the recipient table. If database implementation is done from another table, make sure to reword the command line with the correct information.

The following command line can be used to create a dynamic **List-Unsubscribe**:

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail, Outlook.com and Microsoft Outlook support this method and an unsubscribe button is available directly in their interface. This technique lowers complaint rates.

![](assets/s_tn_del_msn_unsubscribe_list.png)

![](assets/s_tn_del_gmail_unsubscribe_list.png)

You can implement the **List-Unsubscribe** by:

* directly adding the command line in the delivery template - see [this section](#adding-a-command-line-in-a-delivery-template),
* or, creating a typology rule - see [this section](#creating-a-typology-rule).

### Adding a command line in a delivery template {#adding-a-command-line-in-a-delivery-template}

The command line must be added in the additional section of the email's SMTP header.

This addition can be done in each email, or in existing delivery templates. You can also create a new delivery template that includes this functionality.

### Creating a typology rule {#creating-a-typology-rule}

The rule must contain the script that generates the command line and it must be included in the email header.

>[!NOTE]
>
>We recommend creating a typology rule: the List-Unsubscribe functionality will be automatically added in each email.

1. List-Unsubscribe: &lt;mailto:unsubscribe@domain.com&gt;

   Clicking the **unsubscribe** link opens the user's default email client. This typology rule must be added in a typology used for creating email.

1. List-Unsubscribe: `<https://domain.com/unsubscribe.jsp>`

   Clicking the **unsubscribe** link redirects the user to your unsubscription form.

   Example:

   ![](assets/s_tn_del_unsubscribe_param.png)

## Email optimization {#email-optimization}

### SMTP {#smtp}

SMTP (Simple mail transfer protocol) is an Internet standard for email transmission.

The SMTP errors that aren't checked by a rule are listed in the **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]** folder. These error messages are by default interpreted as unreachable soft errors. The most common errors must be identified and a corresponding rule added in **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]** if you wish to correctly qualify the feedback from the SMTP servers. Without this, the platform will perform unnecessary retries (case of unknown users) or wrongly place certain recipients in quarantine after a given number of tests.

### Dedicated IPs {#dedicated-ips}

Adobe provides a dedicated IP strategy for each customer with a ramp-up IP in order to build a reputation and optimize delivery performance.
