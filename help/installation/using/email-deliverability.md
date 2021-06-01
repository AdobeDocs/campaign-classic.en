---
product: campaign
title: Technical email configuration
description: Learn how to configure Campaign to control the output of your instances when delivering emails.
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
---
# Technical email configurations{#email-deliverability}

## Overview {#overview}

The following section provides an overview of the configuration required for controlling the output of Adobe Campaign instances when delivering emails.

>[!NOTE]
>
>Some configurations can only be performed by Adobe for deployments hosted by Adobe, for example, to access the server and instance configuration files. To learn more about the different deployments, refer to the [Hosting models](../../installation/using/hosting-models.md) section or to [this page](../../installation/using/capability-matrix.md).

For more on the concepts and best practices related to deliverability with Adobe Campaign, refer to this [section](../../delivery/using/about-deliverability.md).

For a deeper dive on what deliverability is, including all technical recommendations concerning the efficient sending and receiving of emails by an Adobe platform, refer to the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).

## Operating principle {#operating-principle}

It is possible to control the output of one or more Adobe Campaign instances to restrict the number of emails sent depending on a domain. For example, you can restrict the output to 20,000 per hour for **yahoo.com** addresses, while configuring 100,000 messages per hour for all other domains.

Message output needs to be controlled for each IP address used by the delivery servers (**mta**). Several **mta** broken down over several machines and belonging to various Adobe Campaign instances can share the same IP address for email delivery: a process needs to be set up to coordinate the use of these IP addresses.

This is what the **stat** module does: it forwards all connection requests and messages to be sent to the mail servers for a set of IP addresses. The statistics server keeps track of deliveries and can enable or disable sending based on set quotas.

![](assets/s_ncs_install_mta.png)

* The statistics server (**stat**) is linked to an Adobe Campaign base to load its configuration.
* The delivery servers (**mta**) use a UDP to contact a statistics server which does not always belong to their own instance.

### Delivery servers {#delivery-servers}

The **mta** module distributes messages to its **mtachild** child modules. Each **mtachild** prepares messages before requesting an authorization from the statistics server, and sending them.

The steps are as follows:

1. The **mta** selects eligible messages and assigns them an available **mtachild**.
1. The **mtachild** loads all information required for building the message (content, personalization elements, attachments, images, etc.) and forwards the message to the **Email Traffic Shaper**.
1. As soon as the email traffic shaper receives the statistics server's authorization (**smtp stat**), the message is sent to the recipient.

![](assets/s_ncs_install_email_traffic_shaper.png)

### Email server statistics and limitations {#email-server-statistics-and-limitations}

The statistics server maintains the following statistics for each email server which receives messages:

* Number of point-in-time connections open,
* Number of messages sent in the last hour,
* Rate of successful/rejected connections,
* Rate of connections to unreachable servers.

At the same time, the module loads a list of limitations for certain email servers:

* Maximum number of simultaneous connections,
* Maximum number of messages per hour, 
* Maximum number of messages per connection.

### Managing IP addresses {#managing-ip-addresses}

The statistics server can combine several instances or several machines with the same public IP address. It is therefore not linked to a specific instance, but it does have to contact an instance to recover limitations per domain.

Delivery statistics are kept for each target MX and for each source IP. For example, if the targeted domain has 5 MX and the platform can use 3 different IP addresses, the server can manage up to 15 series of indicators for this domain.

The source IP address matches the public IP address, i.e. the address as it is seen by the remote email server. This IP address can be different from the address of the machine which hosts the **mta**, if an NAT router is provided. This is why the statistics server uses an identifier which matches the public IP (**publicId**). The association between the local address and this identifier is declared in the **serverConf.xml** configuration file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

## Delivery output controlling {#delivery-output-controlling}

To deliver messages to email servers, the **Email Traffic Shaper** component requests a connection from the statistics server. Once the request is accepted, the connection is opened.

Before sending messages, the module requests 'tokens' from the server. These are generally sets of at least 10 tokens, which reduces the number of queries to the server.

The server saves all the statistics related to connections and deliveries. In case of rebooting, the information is temporarily lost: each client keeps a local copy of their sending statistics and returns them to the server on a regular basis (every 2 minutes). The server may then re-aggregate the data.

The following sections describe the processing of a message by the **Email Traffic Shaper** component.

### Message delivery {#message-delivery}

When a message is sent, there are 3 possible results:

1. **Success**: the message was sent successfully. The message is updated.
1. **Message Failed**: the contacted server rejected the message for the chosen recipient. This result matches return codes 550 to 599, but exceptions can be defined.
1. **Session Failed** (for 5.11 upward): if the **mta** receives an answer for this message, the message is abandoned (refer to [Message abandonment](#message-abandonment)). The message is sent to another path or set to pending if no other paths are available (refer to [Message pending](#message-pending)).

   >[!NOTE]
   >
   >A **path** is a connection between the Adobe Campaign **mta** and the target **mta**. The Adobe Campaign **mta** can choose from several start IPs and several target domain IPs.

### Message abandonment {#message-abandonment}

Abandoned messages are returned to the **mta** and are no longer managed by the **mtachild**.

The **mta** decides on the procedure for this message (recovery, abandonment, quarantine, etc.) depending on the response code and the rules.

### Message pending {#message-pending}

A message is pended when it arrives in the active queue and there are no available paths.

A path is generally marked as unavailable for a variable amount of time after a connection error. The unavailability period depends on the frequency and age of errors.

## Statistics server configuration {#statistics-server-configuration}

The statistics server can be used by several instances: it has to be configured independently from the instances that will use it.

Start by defining the Adobe Campaign database that will host the configuration.

### Start configuration {#start-configuration}

By default, the **stat** module is started for each instance. When the instances are mutualized on the same machine, or when instances share the same IP address, a single statistics server is used: the others have to be disabled.

### Definition of the server port {#definition-of-the-server-port}

By default, the statistics server listens on port 7777. This port can be modified in the **serverConf.xml** file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## MX configuration {#mx-configuration}

>[!IMPORTANT]
>
>For hosted or hybrid installations, if you have upgraded to the [Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md), the **[!UICONTROL MX management]** delivery throughput rules are no longer used. The Enhanced MTA uses its own MX rules that allow it to customize your throughput by domain based on your own historical email reputation, and on the real-time feedback coming from the domains where you’re sending emails.

### About MX rules {#about-mx-rules}

>[!NOTE]
>
>This section and the sections below only apply to on-premise installations and hosted/hybrid installations using the legacy Campaign MTA.

MX rules (Mail eXchanger) are the rules that manage communication between a sending server and a receiving server.

These rules are reloaded automatically every morning at 6AM (server time) in order to regularly supply the client instance.

Depending on the material capacities and the internal policy, an ISP will accept a predefined number of connections and messages per hour. These variables may be automatically modified by the ISP system depending on the reputation of the IP and sending domain. Via its deliverability platform, Adobe Campaign manages more than 150 specific rules by the ISP, and, in addition, one generic rule for other domains.

The maximum number of connections does not depend exclusively on the number of public IP addresses used by the MTA.

For instance, if you have allowed 5 connections in the MX rules and you have configured 2 public IPs you might think that you cannot have more than 10 connections simultaneously opened to this domain. This is not true, in fact the maximum number of connections refers to a path and a path that is a combination of one of our MTA public IPs and a public IP of the client's MTA.

In the example below, the user has two public IP addresses configured and the domain is yahoo.com.

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

MX records for yahoo.com tell us that yahoo.com has 3 Mail Exchangers. To connect the Peer Mail Exchanger, the MTA is going to request it's IP address from the DNS.

```
user:~ user$ host -t a mta5.am0.yahoodns.net
                mta5.am0.yahoodns.net has address 98.136.216.26
                mta5.am0.yahoodns.net has address 98.136.217.202
                mta5.am0.yahoodns.net has address 98.138.112.38
                mta5.am0.yahoodns.net has address 66.196.118.37
                mta5.am0.yahoodns.net has address 63.250.192.46
                mta5.am0.yahoodns.net has address 66.196.118.240
                mta5.am0.yahoodns.net has address 98.136.217.203
                mta5.am0.yahoodns.net has address 98.138.112.35
```

For this record, the user can contact 8 peer IP addresses. As he has 2 public IP address this gives him 8 * 2 = 16 combinations to reach the yahoo.com mail servers. Each of those combinations is called a path.

The second MX record appears as:

```
user:~ user$ host -t a mta6.am0.yahoodns.net
                mta6.am0.yahoodns.net has address 98.138.112.38
                mta6.am0.yahoodns.net has address 98.136.216.26
                mta6.am0.yahoodns.net has address 63.250.192.46
                mta6.am0.yahoodns.net has address 66.196.118.35
                mta6.am0.yahoodns.net has address 98.136.217.203
                mta6.am0.yahoodns.net has address 98.138.112.32
                mta6.am0.yahoodns.net has address 98.138.112.37
                mta6.am0.yahoodns.net has address 66.196.118.33
```

4 of these 8 IP addresses are already used in mta5 (98.136.216.26, 98.138.112.38, 63.250.192.46 and 98.136.217.203). This record lets the user use 4 new IP addresses. The third MX record will do the same.

In total, we have 16 remote IP addresses. In combination with our 2 local public IPs we have 32 paths to reach yahoo.com mail servers.

>[!NOTE]
>
>If 2 MX records are referencing the same IP address, this one will count as one path and not two.

Below are some examples of using MX rules:

   ![](assets/s_ncs_examples_mx_rules.png)

In the example below, the user has a limit of 10,000 messages per hour for a particular domain, but the MTA throughput capacity is higher than this limit.

In this case, the traffic is divided into 12 periods of 5 minutes for each hour, and the real limit is 833 messages per period.

These messages will be delivered as quickly as possible.

   ![](assets/s_ncs_traffic_shaping.png)

### Configuring MX management {#configuring-mx-management}

The rules to be complied with for MX are defined in the **[!UICONTROL MX management]** document of the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** node of the tree.

If the **[!UICONTROL MX management]** document does not exist in the node, you can create it manually. To do this:

1. Create a new set of mail rules.
1. Choose the **[!UICONTROL MX management]** mode.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Enter **defaultMXRules** in the **[!UICONTROL Internal name]** field.

In order for changes to be taken into account, you need to restart the statistics server.

To reload the configuration without restarting the statistics server, use the following command on the machine which hosts the server: `nlserver stat -reload`

>[!NOTE]
>
>This command line is preferred to **nlserver restart**. It prevents statistics collected before the restart being lost and avoids peaks in use which can go against quotas defined in the MX rules.

### Configuring MX rules {#configuring-mx-rules}

The **[!UICONTROL MX management]** document lists all domains that are linked to an MX rule.

These rules are applied in sequence: the first rule whose MX mask is compatible with the targeted MX is applied.

The following parameters available for each rule are:

* **[!UICONTROL MX mask]**: domain on which the rule is applied. Each rule defines an address mask for the MX. Any MX whose name matches this mask is therefore eligible. The mask can contain "&#42;" and "?" generic characters.

  For example, the following addresses:

  * a.mx.yahoo.com 
  * b.mx.yahoo.com 
  * c.mx.yahoo.com

  are compatible with the following masks:

  * &#42;.yahoo.com
  * ?.mx.yahoo.com

  For example, for the email address foobar@gmail.com, the domain is gmail.com and the MX record is:

  ```
  gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
  ```

  In this case the MX rule `*.google.com` will be used. As you can see, the MX rule mask does not necessarily match the domain in the mail. The MX rules applied for gmail.com email addresses will be the ones with the mask `*.google.com`.

* **[!UICONTROL Range of identifiers]**: this option lets you indicate the ranges of identifiers (publicID) for which the rule applies. You can specify:

  * A number: the rule will only apply to this publicId,
  * A range of numbers (**number1-number2**): the rule will apply to all publicIds between these two numbers.

  >[!NOTE]
  >
  >If the field is empty, the rule applies to all identifiers.

  A Public ID is an internal identifier of a Public IP used by one or several MTAs. These IDs are defined in the MTA servers in the **config-instance.xml** file.
  
  ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**: defines the scope of the properties for this MX rule. When checked, all of the parameters are shared on all IPs available on the instance. When unchecked, the MX rules are defined for each IP. The maximum number of messages is multiplied by the number of available IPs.
* **[!UICONTROL Maximum number of connections]**: maximum number of simultaneous connections to to the sender's domain.
* **[!UICONTROL Maximum number of messages]**: maximum number of messages that can be sent on a connection. When the messages exceed this number, the connection is closed and a new one is opened.
* **[!UICONTROL Messages per hour]**: maximum number of messages that can be sent in one hour to the sender's domain.
* **[!UICONTROL Connection time out]**: time threshold for connecting to a domain.

  >[!NOTE]
  >
  >Windows can issue a **timeout** before this threshold, which depends on your version of Windows.

* **[!UICONTROL Timeout Data]**: maximum wait time after sending message content (DATA section of the SMTP protocol). 
* **[!UICONTROL Timeout]**: maximum wait time for other exchanges with the SMTP server. 
* **[!UICONTROL TLS]**: The TLS protocol, which allows you to encrypt email deliveries, can be enabled selectively. For each MX mask, the following options are available:

  * **[!UICONTROL Default configuration]**: This is the general configuration specified in the serverConf.xml configuration file which is applied.

    >[!IMPORTANT]
    >
    >It is not recommended to modify the default configuration.

  * **[!UICONTROL Disabled]** : The messages are systematically sent without encryption.
  * **[!UICONTROL Opportunistic]** : Message delivery is encrypted if the receiving server (SMTP) can generate the TLS protocol.

Configuration example:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>For more on using MX servers with Adobe Campaign, see [this section](../../installation/using/using-mx-servers.md).

### Managing email formats {#managing-email-formats}

You can define the format of sent messages, so that the content displayed automatically adapts according to the domain of each recipient's address.

To do this, go to the **[!UICONTROL Management of email formats]** document, which is located in **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**.

This document contains a list of all of the predefined domains that correspond to the Japanese formats managed by Adobe Campaign. For more information, refer to [this document](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

The **MIME structure** (Multipurpose Internet Mail Extensions) parameter allows you to define the message structure that will be sent to the different mail clients. There are three options available:

* **Multipart**: The message is sent in text or HTML format. If the HTML format is not accepted, the message will still be able to be displayed in text format.

  By default, the multipart structure is **multipart/alternative**, but it automatically becomes **multipart/related** when an image is added to the message. Certain providers expect the **multipart/related** format by default, the **[!UICONTROL Force multipart/related]** option imposes this format even if no image is attached.

* **HTML**: An HTML only message is sent. If the HTML format is not accepted, the message will not be displayed.
* **Text**: A message in text only format is sent. The advantage of text format messages is their very small size.

If the **[!UICONTROL Image inclusion]** option is enabled, these are displayed directly in the body of the email. The images will then be uploaded and the URL links will be replaced by their content.

This option is particularly used by the Japanese market for **Deco-mail**, **Decore Mail** or **Decoration Mail**. For more information, consult [this document](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

>[!IMPORTANT]
>
>Inserting images in an email increases its size considerably.

## Delivery server configuration {#delivery-server-configuration}

### Clock synchronization {#clock-synchronization}

The clocks of all the servers that make up the Adobe Campaign platform (including the database) must be synchronized, and their systems set to the same time-zone.

### Coordinates of the statistics server {#coordinates-of-the-statistics-server}

The address of the statistics server has to be provided in the **mta**.

The **statServerAddress** property of the **mta** element of the configuration lets you specify the address and number of the port to be used.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

To use the statistics server on the same machine, you must enter at least the name of the machine with the **localhost** value:

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>If this field is not populated, the **mta** will not start.

### List of IP addresses to use {#list-of-ip-addresses-to-use}

The configuration concerning traffic management is located in the **mta/child/smtp** element of the configuration file.

For each **IPAffinity** element, you need to declare the IP addresses that can be used for the machine.

Example:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

The parameters are as follows:

* **address**: this is the IP address of the MTA host machine to be used. 
* **heloHost**: this identifier represents the IP address as it will be seen by the SMTP server. 

* **publicId**: this information is useful when an IP address is shared by several Adobe Campaign **mtas** behind an NAT router. The statistics server uses this identifier to memorize connection and sending statistics between this starting point and the target server. 
* **weight**: lets you define the relative frequency of use of the address. By default, all addresses have a weight equal to 1.

>[!NOTE]
>
>In the serverConf.xml file, you need to verify that that one IP corresponds to a single helohost with a unique identifier (public_id). It cannot be mapped to multiple helohosts, which could result in delivery throttling issues.

  In the previous example, with normal conditions, the addresses will be distributed as follows:

    * "1": 5 / (5+5+1) = 45% 
    * "2": 5 / (5+5+1) = 45% 
    * "3": 1 / (5+5+1) = 10%

  If, for example, the first address cannot be used towards a given MX, messages will be sent as follows:

    * "2": 5 / (5+1) = 83% 
    * "3": 1 / (5+1) = 17%

* **includeDomains**: lets you reserve this IP address for emails belonging to a specific domain. This is a list of masks that can contain one or more wildcards ('&#42;'). If the attribute is not specified, all domains can use this IP address.

  Example: **includeDomains="wanadoo.com,orange.com,yahoo.&#42;"**

* **excludeDomains**: excludes a list of domains for this IP address. This filter is applied after the **includeDomains** filter. 

  ![](assets/s_ncs_install_mta_ips.png)

## Email sending optimization {#email-sending-optimization}

The internal architecture of the Adobe Campaign **mta** has an impact on the configuration for optimizing email delivery. Here are a few tips on improving your deliveries.

### Adjust the maxWaitingMessages parameter {#adjust-the-maxwaitingmessages-parameter}

The **maxWaitingMessages** parameter indicates the highest number of messages prepared in advance by the **mtachild**. Messages are only deleted from this list once they have been sent or abandoned.

This parameter is very important and particularly critical if messages are not sorted by domain.

Once the **maxWorkingSetMb** (256) threshold is reached, the delivery server stops sending messages. Performance will decrease significantly until the **mtachild** starts up again. To sidestep this issue, you can either increase the threshold of the **maxWorkingSetMb** parameter, or decrease the threshold of the **maxWaitingMessages** parameter.

The **maxWorkingSetMb** parameter is calculated empirically by multiplying the maximum number of messages by the average message size and multiplying the result by 2.5. For instance, if a message has an average size of 50 kB and the **maxWaitingMessages** parameter equals 1,000, the memory used will average 125 MB.

### Adjust the number of mtachild {#adjust-the-number-of-mtachild}

The number of children should not exceed the number of processors in the machine (approx. 1000 sessions). We recommend that you do not exceed 8 **mtachild**. You may then increase the number of messages per **child** (**maxMsgPerChild**) to achieve a sufficient life-span.
