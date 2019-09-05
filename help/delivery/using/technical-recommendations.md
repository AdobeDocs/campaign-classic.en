---
title: Technical recommendations
seo-title: Technical recommendations
description: Technical recommendations
seo-description: 
page-status-flag: never-activated
uuid: 71be1087-e5ff-4a7a-85ca-36803839e72f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: fc95538b-b54d-44ec-81aa-f51b62982699
index: y
internal: n
snippet: y
---

# Technical recommendations{#technical-recommendations}

## Reverse DNS {#reverse-dns}

A tool to verify the configuration of a domain: [https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx).

An important point in the network configuration is making sure a correct reverse DNS is defined for each of the IP addresses for outgoing messages. This means that for a given IP address, there is a reverse DNS record (PTR record) with a matching DNS (A record) looping back to the initial IP address.

The domain choice for a reverse DNS has an impact when dealing with certain ISPs. AOL, in particular, only accepts feedback loops with an address in the same domain as the reverse DNS (see [Feedback loop](../../delivery/using/technical-recommendations.md#feedback-loop)).

## SPF {#spf}

Refer to [https://www.openspf.org/](https://www.openspf.org/). A wizard is available to create SPF records.

A tool to verify an SPF record: [https://www.kitterman.com/spf/validate.html](https://www.kitterman.com/spf/validate.html)

The SPF (Sender Policy Framework) is a technique that, to a certain extent, enables you to make sure that the domain name used in an email is not forged. When a message is a received from a domain, the DNS server of the domain is queried. The response is a short record (the SPF record) that details which servers are authorized to send emails from this domain. If we assume that only the owner of the domain has the means to change this record, we can consider that this technique does not allow the sender address to be forged, at least not the part from the right of the "@".

In the final RFC 4408 specification ([https://openspf.org/svn/project/specs/rfc4408.txt](https://www.openspf.org/svn/project/specs/rfc4408.txt)), two elements of the message are used to determine the domain considered as the sender: The domain specified by the SMTP "HELO" (or "EHLO") command and the domain specified by the address of the "Return-Path" (or "MAIL FROM") header, which is also the bounce address. Different considerations make it possible to take into account one of these values only; we recommend making sure that both sources specify the same domain.

Checking the SPF provides an evaluation of the validity of the sender's domain:

* **None**: No evaluation could be performed,
* **Neutral**: The domain queried does not enable evaluation,
* **Pass**: The domain is considered authentic,
* **Fail**: The domain is forged and the message should be rejected,
* **SoftFail**: The domain is probably forged but the message should not be rejected solely on the basis of this result,
* **TempError**: A temporary error stopped the evaluation. The message can be rejected,
* **PermError**: The SPF records of the domain are invalid.

It is worth noting that records made at the level of the DNS servers can take up to 48 hours to be taken into account. This delay depends on how often the DNS caches of the receiving servers are refreshed.

### Configuring the application {#configuring-the-application}

To define the domain used for the HELO command, edit the instance's configuration file (conf/config-instance.xml) and define a "localDomain" attribute as follows:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

The MAIL FROM domain is the domain used in technical bounce messages. This address is defined in the deployment wizard or via the NmsEmail_DefaultErrorAddr option.

### DNS configuration {#dns-configuration}

An SPF record can currently be defined on a DNS server as a TXT type record (code 16) or an SPF type record (code 99). An SPF record takes the form of a character string. For example:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

defines the 2 IP addresses 12.34.56.78 and 12.34.56.79 as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

Recommendations for defining an SPF record:

* Add **~all** (SoftFail) or **-all** (Fail) at the end to reject all servers other than those defined. Without this, servers will be able to forge this domain (with a Neutral evaluation).
* Do not add **ptr** (openspf.org recommends against this as costly and unreliable).

## Feedback loop {#feedback-loop}

A feedback loop works by declaring at the ISP level a given email address for a range of IP addresses used for sending messages. The ISP will send to this mailbox, in a similar way as what is done for bounce messages, those messages that are reported by recipients as spam. The platform should be configured to block future deliveries to users who have complained. It is important to no longer contact them even if they did not use the proper opt-out link. It is on the basis of these complaints that an ISP will blacklist an IP address. Depending on the ISP, a complaint rate of around 1% will result in the blacklisting of an IP address.

A standard is currently being drawn up to define the format of feedback loop messages: the **Abuse Feedback Reporting Format (ARF)**. See [https://www.mipassoc.org/arf/](https://www.mipassoc.org/arf/) for further details.

Implementing a feedback loop for an instance requires:

* A mailbox dedicated to the instance, which may be the bounce mailbox
* IP sending addresses dedicated to the instance

Implementing a simple feedback loop in Adobe Campaign uses the bounce message functionality. The feedback loop mailbox is used as a bounce mailbox and a rule is defined to detect these messages. The email addresses of the recipients who reported the message as spam will be added to the quarantine list.

* Create or modify a bounce mail rule, **Feedback_loop**, in **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** with the reason **Refused** and the type **Hard**.
* If a mailbox has been defined specially for the feedback loop, define the parameters to access it by creating a new external Bounce Mails account in **[!UICONTROL Administration > Platform > External accounts]**.

The mechanism is immediately operational to process complaint notifications. To make sure this rule is working correctly, you can temporarily deactivate the accounts so that they do not collect these messages, then check the contents of the feedback loop mailbox manually. On the server, execute the following commands:

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

If you are forced to use one single feedback loop address for multiple instances, you must:

* Replicate the messages received on as many mailboxes as there are instances,
* Have each mailbox picked up by one single instance,
* Configure the instances so that they only process the messages that concern them: the instance information is included in the Message-ID header of messages sent by Adobe Campaign and is therefore located also in the feedback loop messages. Simply specify the **checkInstanceName** parameter in the instance configuration file (by default, the instance is not verified and this may lead certain address to be quarantined incorrectly):

  ```
  <serverConf>
    <inMail checkInstanceName="true"/>
  </serverConf>
  ```

Adobe Campaign's Deliverability service manages your subscription to feedback loop services for the following ISPs: AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho.

## List-Unsubscribe {#list-unsubscribe-}

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

>[!CAUTION]
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

* directly adding the command line in the delivery template - see [this section](../../delivery/using/technical-recommendations.md#adding-a-command-line-in-a-delivery-template),
* or, creating a typology rule - see [this section](../../delivery/using/technical-recommendations.md#creating-a-typology-rule).

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

## SMTP header for reattributing inactive addresses by Yahoo! {#smtp-header-for-reattributing-inactive-addresses-by-yahoo-}

### Introduction {#introduction}

The new SMTP header is a mandatory tool to control future communication and personal information that will be sent to Yahoo! users using an address which has been reattributed.

### Installation {#installation}

Adobe Campaign lets you add additional headers that use delivery properties such as List-Unsubscribe for example.

If you wish, this type of addition can be used for certain domains only.

This SMTP header is named "Require-Recipient-Valid-Since" and the deliveries containing this tag "ask" Yahoo! for validation of the targeted account.

Specific additional tags:

* Name: Require-Recipient-Valid-Since,
* Information used in the tag: email address.

>[!NOTE]
>
>These elements are necessary for implementing the tag and are called when it is about a marketing instance.
>
>However, real-time instances operate with a feed: you must update this feed with the **Date** information.

### Operating principle {#operating-principle}

If the target email address is kelyslater@yahoo.com and this address has been present in the database since 12th October 2010, the header must be as follows:

```
Require-Recipent-Valid-Since: kelyslater@yahoo.com; 12 Oct 2010
```

If this email address has been reattributed to another Yahoo! user, an error message will indicate this reattribution as a quarantined address.

You can then use a workflow to contact the target via Facebook or an sms and update its profile.

## Precedence tag {#precedence-tag}

### About precedence tag {#about-precedence-tag}

Some ISPs ask for mass senders to add a tag to their header which allows them to be identified. A good example is Gmail where this tag is a pre-requisite.

### Installing SMTP headers {#installing-smtp-headers}

Adobe Campaign lets you add additional SMTP headers using the delivery properties, such as the 'List-Unsubscribe' tag. This type of SMTP addition can also be added to certain domains only.

For example, to only include this SMTP header in Gmail, the function is as follows:

```
<%
  if (recipient.domain == 'gmail.com')
    {
%>
  Precedence: bulk
<%
    }
%>
```

![](assets/precedence-tag.png)

## DomainKeys {#domainkeys}

### About DomainKeys {#about-domainkeys}

This technology, mainly sponsored by Yahoo, can be implemented in Adobe Campaign.

However, this authentication method was replaced by **DKIM**. Refer to [this section](../../delivery/using/technical-recommendations.md#domainkeys-identified-mail--dkim-).

### Using keys {#using-keys}

DomainKeys is a specification using public key technology to digitally sign an email to prove the origin of the message.

#### Private/Public key {#private-public-key}

The domain owner generates a pair of keys (public/private) that will be used to sign the messages sent by the users of this domain. The public key is placed in the DNS of the domain as a TXT type record. The private key is kept on the messaging server that sends emails for this domain.

When an email is sent by the user of the domain, the messaging server uses the private key to sign the message. The signature is added to the message header before it is sent.

When a signed message is received, the messaging server reads the signature and message domain then queries the DNS in order to obtain the public key of the domain. With this public key, the messaging server then checks whether the signature of the message is valid.

#### Selectors {#selectors}

Selectors enable a domain to have multiple public keys in the DNS. The administrator can then choose a given key depending on the type of traffic. If the selector is 'test' and the domain is 'example.com', the public key will be available from the **test._domainkey.example.com** TXT-type DNS record. The name preceding **_domainkey** is the selector.

Adobe Campaign uses **default** as the default selector.

### Enabling DomainKeys {#enabling-domainkeys}

This section describes the required configuration in Adobe Campaign to enable DomainKeys.

You must be able to update the DNS records for your domain to enable DomainKeys.

To do this, follow the steps below:

1. Generate the keys: from a command prompt, use the following syntax: `$ openssl genrsa -out rsa.private 1024`

  The result is an **rsa.private** file such as:

   ```
   -----BEGIN RSA PRIVATE KEY-----
   MIICXQIBAAKBgQCUBBPm/6CGCw3Imbgka0GWIp95KTlE645kZVLp3MWLMox4bQUu
   2Jks9+3eg/qk5ITFmxH//LB6efRgroW005En7u18nZ4FPWj0rKUuGYQTbMLq7+sB
   KmSZNiVFcuGCl3O8oA7EPPuf0oK9B84FAwp94cBw5qzSdkvd5bMMCwkfVQIDAQAB
   AoGAWgo8/SmFweTZhq0UGntwk18Oecr8/pL4tNP6Yy8csHeYge132K6ER5muhszs
   XQByUC7r/Tf/NxIW+fVQeta0lpRki+SBvQOJyzTfXYf1S9XyyIgbPmVz8sQK2nWr
   KdzUeM1ueSuL82dPJXvkXaXirpm0rSHSYu0D7878/CGzxaUCQQDFUAXsIq3u+iwl
   27kkMPKqAb96fUxmF14huxmoB6oMbblFwAT94IxfoXOR5lwEoHZvklcnfk0wiIyk
   vUv+Fj1/AkEAwAp1NARz6wtYChft+ruMAI5cZyfC9BmaCesTkvmLb3411ooql5QP
   m2vAeuUw3I8GmjI3uzdnJ18gTeTV6S61KwJBALLZEkU0Ogx/3zyBqZPQemT3KKTS
   pklzrPNOMLdKGy0g1+sNXnjw7MxR//ujnozjFfeT4kP+C+GOJE2+9/7cEekCQGrb
   ptnZ/HJ2bne3VwmkoEOS86HGwzk2obsRHmQzDT5t2SFW4lpT3ddavtDjhSvFPiRA
   +zfmnTSQPxZ41fqZrd8CQQDCcnFVQUMtMasfV5hGQjOPLoX8a6ivFNmSk7P0gPVt
   2iwz49E+Os0q5AhghyOmxsmwLjUOmptLBrWMR/gt2w7Q
   -----END RSA PRIVATE KEY-----
   ```

   >[!NOTE]
   >
   >Adobe Campaign supports 512, 768, 1024, 1536 and 2048-bit keys. To date, a minimum length key is not a prerequisite, however, it is generally accepted that a 512-bit key can potentially be falsified. The length of the key can have an impact on throughput (if CPU is the only limiting factor):
   >
   >* 512 bit: - 19 % compared to sending unsigned
   >* 768 bit: - 37 %
   >* 1024 bit: - 60 %
   >* 1536 bit: - 80 %
   >* 2048 bit: - 90 %

1. To extract the public key from the private key, use the following command: `$ openssl rsa -in rsa.private -out rsa.public -pubout -outform PEM`

   The result is an **rsa.public** file such as:

   ```
   -----BEGIN PUBLIC KEY-----
   MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCUBBPm/6CGCw3Imbgka0GWIp95
   KTlE645kZVLp3MWLMox4bQUu2Jks9+3eg/qk5ITFmxH//LB6efRgroW005En7u18
   nZ4FPWj0rKUuGYQTbMLq7+sBKmSZNiVFcuGCl3O8oA7EPPuf0oK9B84FAwp94cBw
   5qzSdkvd5bMMCwkfVQIDAQAB
   -----END PUBLIC KEY-----
   ```

   >[!NOTE]
   >
   >In Windows, you must download the OpenSSL library from the following URL: [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

1. Save the public key in the DNS

   Here is the syntax to create a TXT-type DNS record for **selector._domainkey.example.com**:

    * Syntax for BIND

      ```
      default._domainkey.example.com. IN TXT "k=rsa; t=y; 
      p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCUBBPm
      /6CGCw3Imbgka0GWIp95KTlE645kZVLp3MWLMox4bQUu2Jks9+3eg
      /qk5ITFmxH/
      /LB6efRgroW005En7u18nZ4FPWj0rKUuGYQTbMLq7
      +sBKmSZNiVFcuGCl3O8oA7EPPuf0oK9B84FAwp94cBw5qzSdkvd5bMMCwkfVQIDAQAB"
      ```

    * Syntax for DJBDNS (TINYDNS)

      ```
      'default._domainkey. example.com:k=rsa;t=y; 
      p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCUBBPm
      /6CGCw3Imbgka0GWIp95KTlE645kZVLp3MWLMox4bQUu2Jks9+3eg
      /qk5ITFmxH/
      /LB6efRgroW005En7u18nZ4FPWj0rKUuGYQTbMLq7
      +sBKmSZNiVFcuGCl3O8oA7EPPuf0oK9B84FAwp94cBw5qzSdkvd5bMMCwkfVQIDAQAB;:86400
      ```

      The parameters of the record are defined with the syntax **parameter=value**.

      The valid parameters are:

        * **g=** defines the applicability of the key in relation to the local name of the sender.

          **g=&#42;** enables all senders in the domain **example.com** to use the key.

          **g=sender;** enables this key to be used for messages sent from **sender@example.com**.
        * **k =** key type. Only the value **rsa** is supported. This parameter is optional.
        * **n =** note concerning the key. This note is intended for administrators and is not used by the signature and authentication processes. This parameter is optional.
        * **p =** public key encoded in Base64. An empty value means that the key has been revoked. This parameter is mandatory.
        * **t =** flags defining attributes. One single attribute is currently defined by the specification: **t=y** means that the domain is using this key in test phase.

      The public key encoded in Base64 corresponds to the contents of the **rsa.public** file between the lines `----- BEGIN PUBLIC KEY-----` and `-----END PUBLIC KEY-----`

      You must also delete the spaces and the carriage returns.

1. Save the private key in Adobe Campaign

   The private key is saved in the form of an option in the Adobe Campaign database. Connect to Adobe Campaign as the Administrator and then create an option:

   ```
   Internal name: selector_RSA_PRIVATE_KEY_domain
   Type:          Long text
   Value:        The private key encoded in Base64. 
   ```

   In the internal name of the option, the **selector** part is optional. As the default selector in Adobe Campaign is **default**, the **default_RSA_PRIVATE_KEY_example.com** and **RSA_PRIVATE_KEY_example.com** options are equivalent.

   For the domain value, the period is changed by Adobe Campaign into the underscore character `"_"`.

   The private key populated in the option must be the exact contents of the rsa.private, including `----- BEGIN PRIVATE KEY----- and -----END PRIVATE KEY-----`

1. Enable DomainKeys management

   To enable message signing for a domain, go to the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** folder and then select **[!UICONTROL Domain management]** from the list. If the domain is already in the list, simply select the **[!UICONTROL DomainKeys]** database, else create a new rule for this domain and then select the **[!UICONTROL DomainKeys]** option.

   Enabling **senderId** on the domain forces the technical domain to be used to sign the message.
   
   Enabling **senderId** with **DomainKeys** may be useful when managing multiple sender domains.

1. Test the configuration

   The easiest thing to do is to create a test mailbox on **yahoo.com**. If DomainKeys is correctly configured, you should receive a message from Yahoo! using the address of the sender confirming the origin of the message.

   ![](assets/s_tn_del_domainkey01.png)

   Further information is given in the full headers:

   ![](assets/s_tn_del_domainkey02.png)

## DomainKeys Identified Mail (DKIM) {#domainkeys-identified-mail--dkim-}

DKIM comes from a combination of the DomainKeys, Yahoo! and Cisco Identified Internet Mail authentication principles and is used to check the authenticity of the sender domain and guarantee the integrity of the message.

DKIM replaced **DomainKeys** authentication. Refer to [this section](../../delivery/using/technical-recommendations.md#domainkeys).

Using DKIM requires some prerequisites:

* **Security**: encryption is a key element of the DKIM and to insure the security level of the DKIM since the spring 2013, 1024b is the Best Practices recommended encryption size. Lower DKIM keys will not be considered as valid by the majority of access providers.
* **Reputation**: reputation is based on the IP and/or the domain, but the less transparent DKIM selector is also a key element to be taken into account. Choosing the selector is important: avoid keeping the “default” one which could be used by anyone and therefore has a very weak reputation. You must implement a different selector for **retention vs. acquisition communications** and for authentication.
* **Adobe Campaign option declaration**: in Adobe campaign the DKIM private key is based on a DKIM selector and a domain. It is not currently possible to create multiple private keys for the same domain/sub-domain with different selectors. It is not possible to define which selector domain/sub-domain must be used for the authentication in neither the platform or the email. The platform will alternatively select one of the private keys, which means the authentication has a high chance of failing.

>[!NOTE]
>
>* This functionality is available from build 1937 onwards.
>* If you have configured DomainKeys for your Adobe Campaign instance, you just need to select **dkim** in the domain handling rules. If not, follow the same configuration steps (private/public key) as for DomainKeys.
>* It is not necessary to enable both DomainKeys and DKIM for the same domain as DKIM is an improved version of DomainKeys.
>* The following domains currently validate DKIM: AOL, Gmail.

## MX rules {#mx-rules}

MX rules (Mail eXchanger) are the rules that manage communication between a sending server and a receiving server.

Depending on the material capacities and the internal policy, an ISP will accept a predefined number of connections and messages per hour. These variables may be automatically modified by the ISP system depending on the reputation of the IP and sending domain. Via its deliverability platform, Adobe Campaign manages more than 150 specific rules by the ISP, and, in addition, one generic rule for other domains.

These rules are updated via a daily workflow in order to regularly supply the client instance.

### About MX rules {#about-mx-rules}

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

### Configuring MX management {#configuring-mx-management}

From the **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]** > **[!UICONTROL MX management node]**, you can access the list of domains that are linked to an MX rule. You will find:

* MX mask: domain on which the rule is applied.

  For example, for the email address foobar@gmail.com, the domain is gmail.com and the MX record is:

  ```
  gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
  ```

In this case the MX rule `*.google.com` will be used. As you can see, the MX rule mask does not necessarily match the domain in the mail. The MX rules applied for gmail.com email addresses will be the ones with the mask `*.google.com`.

* **Shared**: Defines the scope of the properties for this MX rule. When checked, all of the parameters are shared on all IPs available on the instance. When unchecked, the MX rules are defined for each IP. The maximum number of messages is multiplied by the number of available IPs.
* **Maximum number of connections**: maximum number of simultaneous connections to the sender's domain.
* **Maximum number of messages**: maximum number of messages sent by a connection.
* **Messages per hour**: maximum number of messages sent per hour to the sender's domain.
* **Messages per hour (speed)**: maximum number of messages sent per hour to the sender's domain for the speed selected.

There are five speeds available: Slow, Normal, Fast, Very fast, Boost.

>[!NOTE]
>
>For more information on MX rules, refer to [this section](../../installation/using/email-deliverability.md).

MX rules are reloaded automatically every morning at 6AM (server time).

You can also reload them manually running the following command line on the server: `$ nlserver stat -reload`.

>[!NOTE]
>
>This command line is preferred to **nlserver restart**. It prevents statistics collected before the restart being lost and avoids peaks in use which can go against quotas defined in the MX rules.

### Public ID {#public-id}

A Public ID is an internal identifier of a Public IP used by one or several MTAs.

These IDs are defined in the MTA servers in the **config-instance.xml** file.

   ![](assets/s_ncs_install_MTA_IPs.png)

### Example {#example}

Below are some examples of using MX rules.

   ![](assets/s_ncs_examples_mx_rules.png)

In the example below, the user has a limit of 10,000 messages per hour for a particular domain, but the MTA throughput capacity is higher than this limit.

In this case, the traffic is divided into 12 periods of 5 minutes for each hour, and the real limit is 833 messages per period.

These messages will be delivered as quickly as possible.

   ![](assets/s_ncs_traffic_shaping.png)

### Checking SMTP and bounce error messages {#checking-smtp-and-bounce-error-messages}

The SMTP errors that aren't checked by a rule are listed in the **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]** folder. These error messages are by default interpreted as unreachable soft errors. The most common errors must be identified and a corresponding rule added in **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]** if you wish to correctly qualify the feedback from the SMTP servers. Without this, the platform will perform unnecessary retries (case of unknown users) or wrongly place certain recipients in quarantine after a given number of tests.

As for the SMTP errors, unprocessed bounce mail or bounce mail processed by Ignored type rules must be monitored to determine whether new rules should be added. For this, it is possible to specify an address the platform will forward these messages to.

### Optimizing quarantine management {#optimizing-quarantine-management}

Upgrading the quarantine management process concerns mid-sourcing/Cloud Messaging and a platform configured with an architecture format with n marketing instances and a mid-sourcing instance.

This upgrade ensures that the marketing instance at the origin of the bounce can process its own bounce and add it to its quarantine table.

>[!NOTE]
>
>The bounce log has two IDs to identify the marketing instance that must process the bounce and add it to its quarantine table: Message ID and Broadlog ID.

For more on quarantine management in Adobe Campaign, refer to [this page](../../delivery/using/understanding-quarantine-management.md).

### Quota met {#quota-met}

In Adobe Campaign, there is a configuration regarding the number of emails per hour that can be sent. This configuration must be used with vigilance, as the number defined in the instance concerns the number of connections carried out with the ISP and not the number of emails actually sent.

This means a connection can use an MX rule without successfully sending an email. In this case, a configuration with an IP or a domain with a low reputation will have to try several connections before sending an email. For each attempt, a **messages per hour** credit will be used. As a result, the marketing campaign performance will be significantly impacted.

So quota met is not only a configuration issue but can also be linked to reputation. It is important to analyze error messages in the SMTP log.

### IP rotation {#ip-rotation}

In particular when starting up a new platform, we recommend implementing a system of rotating the IP addresses used at the hardware level. This consists of keeping a certain number of IP address as backup addresses if the IP addresses being used are blacklisted by an ISP. You can start reusing the IP addresses you have let 'lie fallow' once the restriction is raised, in general after a few hours or at worst a few days. You must, however, make sure each IP is used regularly (at least 100 messages over a day per month) so that it does not lose its reputation or get removed from the feedback loops or whitelists. When the reputation of the platform is firmly established, you may consider permanently using all the IPs.

### Email volume per IP {#email-volume-per-ip}

Adobe Campaign stores the IP reputation and volume sent per IP in a log file in order to have a better control over this. This information is available in a dedicated report.

>[!CAUTION]
>
>When this option is implemented, it is mandatory to add a column in the database. The update can then take more or less time: it is important to schedule this update during a period of low activity.

### Exchange between stat servers {#exchange-between-stat-servers}

In the context of a migration or certain mid-sourcing/cloud messaging projects, we need to have a marketing instance communicating with a new version of a mid-sourcing/cloud messaging instance.

Most of the time the versioning is different from an update to a minor build, but the configuration may require you to install the most recent version of the software.

During this phase (which is a mix of the old version and the new version, which use the same IPs) it is necessary to keep the integrity of the MX rules. In this case only, the stat server can run the two different versions of the mid-sourcing/cloud messaging.

>[!NOTE]
>The most recent version of the software must always be the master version, however you must ensure there is correct communication between the MTAs and stat server.

### External hosting {#external-hosting}

When discussing sending emails, we shall refer to external hosting when the Adobe Campaign platform is:

* **Entirely hosted externally** (database, tracking servers and MTA servers),
* **In mid-sourcing mode**: the database and application server are located within the local network whereas the MTA portion is externalized.

#### Choice of domains {#choice-of-domains}

External hosting, for technical reasons, implies almost systematically that the domain used in the technical sending addresses and the tracked links is different from the main address of the sender. For example:

* The advertiser uses the domain domain.com in all communications.
* The hoster cannot technically use this domain to receive bounce messages because domain.com is the corporate messaging domain and is not intended for such purposes.
* The hoster cannot technically use domain.com for tracking because it is used by the Web site of the advertiser.

The hoster must therefore use a different domain that we will refer to as a technical domain, for example dmnl.net. This domain will be used to receive bounce mail and redirect tracked links. With this said, we will make two points:

1. The sender address (From), which is the most commonly displayed address, can always be given as the address of the advertiser domain.com
1. The tracked links within the message will use the technical domain dmnl.net

To date, this way of operating is permitted, however:

* If we consider Hotmail, using SenderId will display the sender as From: dm-bounces@dmnl.net on behalf of Marketing Domain (marketing@domain.com), which may confuse the recipient as to the origin of the message.
* If the message is supposed to be sent by an advertiser recognized by the domain domain.com, then an email containing links using the domain dmnl.net could be considered as an attempt at phishing.
* In extreme cases, certain anti-spam filters may reject the message as suspicious based on the difference between the bounce domain and the sender domain.

It is therefore increasingly important that there is no doubt as to the authenticity of the sender based on the technical sending domain. For this reason, we recommend using a technical sending address that is a sub-domain of the advertiser's domain. In the previous example, we could use nl.domain.com, and in this way a recipient would have no doubt that the technical sender of the message and the tracked links really do come from domain.com. The bounce address as nl.domain.com can be managed directly by the hoster and the tracking links nl.domain.com can point to their redirection servers.

#### Domain delegation {#domain-delegation}

If a sub-domain needs to be set up by the hoster it must be initiated by the domain owner (the advertiser). It is technically possible for the owner to perform the DNS configuration (MX, A, SPF...) of the sub-domain, however we advise against this because the hoster depends on it for any modification made to the DNS and this is a potentially dangerous situation (risk of losing bounce mail, or failure of tracking mechanisms) given the constraints of running an email platform. We strongly recommend delegating the sub-domain to the hoster.

To delegate the administration of a sub-domain to a third party, the owner of the main domain must declare NS records for the sub-domain designating the DNS servers of the hoster.

#### Sender and bounce mail addresses {#send-and-bounce-mail-addresses}

Because the sender address is the most visible address to the recipient, there should be no doubt as to its identity and should be defined using the domain of the advertiser or at least a sub-domain, for example marketing@domain.com or marketing@nl.domain.com.

If the SPF record of the advertiser's domain authorizes the IP addresses used by the platform, it is not necessary to enable the Sender ID parameter in Adobe Campaign for MSN Hotmail domains and the choice of the address for bounce messages is not restricted.

If the SPF record of the advertiser's domain does not authorize the IP addresses used by the platform, the Sender ID parameter will have to be used for MSN Hotmail. In this case, the bounce address is given to the recipient in the message header. You must choose an address that does not suggest spam, meaning an address that refers to the sender and does not appear to be too technical, for example marketingerr@dmnl.net rather than dm-bounces405@dmnl.net.

#### Other aliases {#other-aliases}

Adobe Campaign lets you define different aliases for tracking, mirror pages and web forms and thus define an architecture that is appropriate for the availability and production constraints you have. To maintain consistency between these domains, you can, for example, define extra sub-domains as shown below:

* Tracking: nl.domain.com
* Mirror pages: m.nl.domain.com
* Web forms: f.nl.domain.com

### DMARC {#DMARC}

**DMARC** (Domain-based Message Authentication, Reporting and Conformance), is a specific technique created by a group of organizations that want to help reduce the abuse of emails, such as spam and phishing, by offering a solution that deploys and monitors problems linked to email authentication.
