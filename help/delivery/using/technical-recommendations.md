---
title: Technical recommendations
seo-title: Technical recommendations
description: Technical recommendations
seo-description: 
page-status-flag: never-activated
uuid: 714b8fe7-4e87-4e00-9808-dfb428b03d82
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 9f3e3b86-748d-48fb-af2e-db05fa1f5978
index: y
internal: n
snippet: y
---

# Technical recommendations{#technical-recommendations}

## Reverse DNS {#reverse-dns}

The domain choice for a reverse DNS has an impact when dealing with certain ISPs. AOL, in particular, only accepts feedback loops with an address in the same domain as the reverse DNS (see [Feedback loop](../../delivery/using/technical-recommendations.md#feedback-loop)).

Refer to [https://www.openspf.org/](https://www.openspf.org/). A wizard is available to create SPF records.

A tool to verify an SPF record: [https://www.kitterman.com/spf/validate.html](https://www.kitterman.com/spf/validate.html)

## SPF {#spf}

The SPF (Sender Policy Framework) is a technique that, to a certain extent, enables you to make sure that the domain name used in an email is not forged. When a message is a received from a domain, the DNS server of the domain is queried. The response is a short record (the SPF record) that details which servers are authorized to send emails from this domain. If we assume that only the owner of the domain has the means to change this record, we can consider that this technique does not allow the sender address to be forged, at least not the part from the right of the "@".

In the final RFC 4408 specification ( [https://openspf.org/svn/project/specs/rfc4408.txt](https://www.openspf.org/svn/project/specs/rfc4408.txt)), two elements of the message are used to determine the domain considered as the sender: The domain specified by the SMTP "HELO" (or "EHLO") command and the domain specified by the address of the "Return-Path" (or "MAIL FROM") header, which is also the bounce address. Different considerations make it possible to take into account one of these values only; we recommend making sure that both sources specify the same domain.

Checking the SPF provides an evaluation of the validity of the sender's domain:

In the final RFC 4408 specification ( [https://openspf.org/svn/project/specs/rfc4408.txt](https://www.openspf.org/svn/project/specs/rfc4408.txt)), two elements of the message are used to determine the domain considered as the sender: The domain specified by the SMTP "HELO" (or "EHLO") command and the domain specified by the address of the "Return-Path" (or "MAIL FROM") header, which is also the bounce address. Different considerations make it possible to take into account one of these values only; we recommend making sure that both sources specify the same domain.

Checking the SPF provides an evaluation of the validity of the sender's domain:

* **None**: No evaluation could be performed,
* **Neutral**: The domain queried does not enable evaluation,
* **Pass**: The domain is considered authentic,
* **Fail**: The domain is forged and the message should be rejected,
* **SoftFail**: The domain is probably forged but the message should not be rejected solely on the basis of this result,
* **TempError**: A temporary error stopped the evaluation. The message can be rejected,
* **PermError**: The SPF records of the domain are invalid.

The MAIL FROM domain is the domain used in technical bounce messages. This address is defined in the deployment wizard or via the **NmsEmail_DefaultErrorAddr **option.

### Configuring the application {#configuring-the-application}

An SPF record can currently be defined on a DNS server as a TXT type record (code 16) or an SPF type record (code 99). An SPF record takes the form of a character string. For example:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

defines the 2 IP addresses 12.34.56.78 and 12.34.56.79 as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

### DNS configuration {#dns-configuration}

Recommendations for defining an SPF record:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

defines the 2 IP addresses 12.34.56.78 and 12.34.56.79 as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

Recommendations for defining an SPF record:

* Add **~all** (SoftFail) or **-all** (Fail) at the end to reject all servers other than those defined. Without this, servers will be able to forge this domain (with a Neutral evaluation).
* Do not add **ptr** (openspf.org recommends against this as costly and unreliable).

## Feedback loop {#feedback-loop}

Implementing a feedback loop for an instance requires:

A standard is currently being drawn up to define the format of feedback loop messages: the **Abuse Feedback Reporting Format (ARF)**. See [https://www.mipassoc.org/arf/](https://www.mipassoc.org/arf/) for further details.

Implementing a feedback loop for an instance requires:

* A mailbox dedicated to the instance, which may be the bounce mailbox
* IP sending addresses dedicated to the instance

Implementing a simple feedback loop in Adobe Campaign uses the bounce message functionality. The feedback loop mailbox is used as a bounce mailbox and a rule is defined to detect these messages. The email addresses of the recipients who reported the message as spam will be added to the quarantine list.

* Create or modify a bounce mail rule, **Feedback_loop**, in **Administration > Campaign Management > Non deliverables Management > Mail rule sets** with the reason **Refused** and the type **Hard**.
* If a mailbox has been defined specially for the feedback loop, define the parameters to access it by creating a new external Bounce Mails account in **Administration > Platform > External accounts**.

**nlserver inMail -instance:**instance** -verbose**.

If you are forced to use one single feedback loop address for multiple instances, you must:

**nlserver inMail -instance:**instance** -verbose**.

If you are forced to use one single feedback loop address for multiple instances, you must:

* Replicate the messages received on as many mailboxes as there are instances,
* Have each mailbox picked up by one single instance,
* Configure the instances so that they only process the messages that concern them: the instance information is included in the Message-ID header of messages sent by Adobe Campaign and is therefore located also in the feedback loop messages. Simply specify the **checkInstanceName** parameter in the instance configuration file (by default, the instance is not verified and this may lead certain address to be quarantined incorrectly):

  ```
  <serverConf>
    <inMail checkInstanceName="true"/>
  </serverConf>
  ```

Using this functionality helps to protect your reputation and feedback will be executed as an unsubscription.

## List-Unsubscribe {#list-unsubscribe-}

### About List-Unsubscribe {#about-list-unsubscribe}

Adding an SMTP header called **List-Unsubscribe** is mandatory to ensure optimal deliverability management.

To use List-Unsubscribe, you must enter a command line similar to as follows:

The email address client@newsletter.example.com represents the platform's technical address (returnpath address).

>[!NOTE]
>
>We recommend creating a typology rule: the **List-Unsubscribe** functionality will be automatically added in each email.

The following command line can be used to create a dynamic **List-Unsubscribe**:

>[!CAUTION]
>
>The example above is based on the recipient table. If database implementation is done from another table, make sure to reword the command line with the correct information.

You can implement the **List-Unsubscribe** by:

Gmail, Outlook.com and Microsoft Outlook support this method and an unsubscribe button is available directly in their interface. This technique lowers complaint rates.

![](assets/s_tn_del_msn_unsubscribe_list.png)

![](assets/s_tn_del_gmail_unsubscribe_list.png)

You can implement the **List-Unsubscribe** by:

* directly adding the command line in the delivery template - see [this section](../../delivery/using/technical-recommendations.md#adding-a-command-line-in-a-delivery-template),
* or, creating a typology rule - see [this section](../../delivery/using/technical-recommendations.md#creating-a-typology-rule).

### Adding a command line in a delivery template {#adding-a-command-line-in-a-delivery-template}

The rule must contain the script that generates the command line and it must be included in the email header.

This addition can be done in each email, or in existing delivery templates. You can also create a new delivery template that includes this functionality.

### Creating a typology rule {#creating-a-typology-rule}

The rule must contain the script that generates the command line and it must be included in the email header.

>[!NOTE]
>
>These elements are necessary for implementing the tag and are called when it is about a marketing instance.  
>However, real-time instances operate with a feed: you must update this feed with the **Date** information.

1. List-Unsubscribe: &lt;mailto:unsubscribe@domain.com&gt;

   Clicking the **unsubscribe** link opens the user's default email client. This typology rule must be added in a typology used for creating email.

1. List-Unsubscribe: `<https: domain.com="" unsubscribe.jsp="" />`

   Clicking the **unsubscribe** link redirects the user to your unsubscription form.

   Example:

   ![](assets/s_tn_del_unsubscribe_param.png)

## SMTP header for reattributing inactive addresses by Yahoo! {#smtp-header-for-reattributing-inactive-addresses-by-yahoo-}

### Introduction {#introduction}

If you wish, this type of addition can be used for certain domains only.

### Installation {#installation}

This SMTP header is named "Require-Recipient-Valid-Since" and the deliveries containing this tag "ask" Yahoo! for validation of the targeted account.

Specific additional tags:

This SMTP header is named "Require-Recipient-Valid-Since" and the deliveries containing this tag "ask" Yahoo! for validation of the targeted account.

Specific additional tags:

* Name: Require-Recipient-Valid-Since,
* Information used in the tag: email address.

>[!NOTE]
>
>These elements are necessary for implementing the tag and are called when it is about a marketing instance. However, real-time instances operate with a feed: you must update this feed with the **Date** information.

### Operating principle {#operating-principle}

You can then use a workflow to contact the target via Facebook or an sms and update its profile.

Some ISPs ask for mass senders to add a tag to their header which allows them to be identified. A good example is Gmail where this tag is a pre-requisite.

Adobe Campaign lets you add additional SMTP headers using the delivery properties, such as the 'List-Unsubscribe' tag. This type of SMTP addition can also be added to certain domains only.

## Precedence tag {#precedence-tag}

### About precedence tag {#about-precedence-tag}

For example, to only include this SMTP header in Gmail, the function is as follows:

### Installing SMTP headers {#installing-smtp-headers}

This technology, mainly sponsored by Yahoo, can be implemented in Adobe Campaign.

However, this authentication method was replaced by **DKIM**. Refer to [this section](../../delivery/using/technical-recommendations.md#domainkeys-identified-mail--dkim-).

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

DomainKeys is a specification using public key technology to digitally sign an email to prove the origin of the message.

The domain owner generates a pair of keys (public/private) that will be used to sign the messages sent by the users of this domain. The public key is placed in the DNS of the domain as a TXT type record. The private key is kept on the messaging server that sends emails for this domain.

### Using keys {#using-keys}

When an email is sent by the user of the domain, the messaging server uses the private key to sign the message. The signature is added to the message header before it is sent.

#### Private/Public key {#private-public-key}

When a signed message is received, the messaging server reads the signature and message domain then queries the DNS in order to obtain the public key of the domain. With this public key, the messaging server then checks whether the signature of the message is valid.

Selectors enable a domain to have multiple public keys in the DNS. The administrator can then choose a given key depending on the type of traffic. If the selector is 'test' and the domain is 'example.com', the public key will be available from the **test._domainkey.example.com** TXT-type DNS record. The name preceding **_domainkey** is the selector.

Adobe Campaign uses **default** as the default selector.

#### Selectors {#selectors}

This section describes the required configuration in Adobe Campaign to enable DomainKeys.

You must be able to update the DNS records for your domain to enable DomainKeys.

### Enabling DomainKeys {#enabling-domainkeys}

To do this, follow the steps below:

You must be able to update the DNS records for your domain to enable DomainKeys.

To do this, follow the steps below:

1. Generate the keys: from a command prompt, use the following syntax:

   **$ openssl genrsa -out rsa.private 1024**

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
   >    
   >    
   >    * 512 bit: - 19 % compared to sending unsigned
   >    * 768 bit: - 37 %
   >    * 1024 bit: - 60 %
   >    * 1536 bit: - 80 %
   >    * 2048 bit: - 90 %
   >    
   >

1. To extract the public key from the private key, use the following command:

   **$ openssl rsa -in rsa.private -out rsa.public -pubout -outform PEM**

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
   >In Windows, you must download the OpenSSL library from the following URL: [https://wiki.openssl.org/index.php/Binaries](https://www.openssl.org/related/binaries.html)

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

        * **g= ** defines the applicability of the key in relation to the local name of the sender.

          **g=&#42;** enables all senders in the domain **example.com** to use the key.

          **g=sender;** enables this key to be used for messages sent from **sender@example.com**.
        
        * **k =** key type. Only the value **rsa** is supported. This parameter is optional.
        * **n =** note concerning the key. This note is intended for administrators and is not used by the signature and authentication processes. This parameter is optional.
        * **p =** public key encoded in Base64. An empty value means that the key has been revoked. This parameter is mandatory.
        * **t =** flags defining attributes. One single attribute is currently defined by the specification: **t=y** means that the domain is using this key in test phase.

      The public key encoded in Base64 corresponds to the contents of the **rsa.public** file between the lines

      ----- BEGIN PUBLIC KEY----- and -----END PUBLIC KEY-----

      You must also delete the spaces and the carriage returns.

1. Save the private key in Adobe Campaign

   The private key is saved in the form of an option in the Adobe Campaign database. Connect to Adobe Campaign as the Administrator and then create an option:

   ```
   Internal name: selector_RSA_PRIVATE_KEY_domain
   Type:          Long text
   Value:        The private key encoded in Base64. 
   
   ```

   In the internal name of the option, the **selector** part is optional. As the default selector in Adobe Campaign is **default**, the **default_RSA_PRIVATE_KEY_example.com** and **RSA_PRIVATE_KEY_example.com** options are equivalent.

   >[!CAUTION]
   >

   The private key populated in the option must be the exact contents of the **rsa.private**, including

   ```
   ----- BEGIN PRIVATE KEY----- and -----END PRIVATE KEY-----
   ```

1. Enable DomainKeys management

   To enable message signing for a domain, go to the **Administration > Campaign Management > Non deliverables Management > Mail rule sets** folder and then select **Domain management** from the list. If the domain is already in the list, simply select the **DomainKeys** database, else create a new rule for this domain and then select the **DomainKeys** option.

   >[!CAUTION]
   >

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
>This functionality is available from build 1937 onwards. If you have configured DomainKeys for your Adobe Campaign instance, you just need to select **dkim** in the domain handling rules. If not, follow the same configuration steps (private/public key) as for DomainKeys. It is not necessary to enable both DomainKeys and DKIM for the same domain as DKIM is an improved version of DomainKeys. The following domains currently validate DKIM: AOL, Gmail.

## MX rules {#mx-rules}

MX rules (Mail eXchanger) are the rules that manage communication between a sending server and a receiving server.

Depending on the material capacities and the internal policy, an ISP will accept a predefined number of connections and messages per hour. These variables may be automatically modified by the ISP system depending on the reputation of the IP and sending domain. Via its deliverability platform, Adobe Campaign manages more than 150 specific rules by the ISP, and, in addition, one generic rule for other domains.

These rules are updated via a daily workflow in order to regularly supply the client instance.

### About MX rules {#about-mx-rules}

The maximum number of connections does not depend exclusively on the number of public IP addresses used by the MTA.

For instance, if you have allowed 5 connections in the MX rules and you have configured 2 public IPs you might think that you cannot have more than 10 connections simultaneously opened to this domain. This is not true, in fact the maximum number of connections refers to a path and a path that is a combination of one of our MTA public IPs and a public IP of the client's MTA.

In the example below, the user has two public IP addresses configured and the domain is yahoo.com.

A tool to verify the configuration of a domain: [https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx).

An important point in the network configuration is making sure a correct reverse DNS is defined for each of the IP addresses for outgoing messages. This means that for a given IP address, there is a reverse DNS record (PTR record) with a matching DNS (A record) looping back to the initial IP address.

It is worth noting that records made at the level of the DNS servers can take up to 48 hours to be taken into account. This delay depends on how often the DNS caches of the receiving servers are refreshed.

To define the domain used for the HELO command, edit the instance's configuration file (**conf/config-**instance**.xml**) and define a "localDomain" attribute as follows:

A feedback loop works by declaring at the ISP level a given email address for a range of IP addresses used for sending messages. The ISP will send to this mailbox, in a similar way as what is done for bounce messages, those messages that are reported by recipients as spam. The platform should be configured to block future deliveries to users who have complained. It is important to no longer contact them even if they did not use the proper opt-out link. It is on the basis of these complaints that an ISP will blacklist an IP address. Depending on the ISP, a complaint rate of around 1% will result in the blacklisting of an IP address.

A standard is currently being drawn up to define the format of feedback loop messages: the **Abuse Feedback Reporting Format (ARF)**. See [https://www.mipassoc.org/arf/](https://www.mipassoc.org/arf/) for further details.

Implementing a simple feedback loop in Adobe Campaign uses the bounce message functionality. The feedback loop mailbox is used as a bounce mailbox and a rule is defined to detect these messages. The email addresses of the recipients who reported the message as spam will be added to the quarantine list.

The mechanism is immediately operational to process complaint notifications. To make sure this rule is working correctly, you can temporarily deactivate the accounts so that they do not collect these messages, then check the contents of the feedback loop mailbox manually. On the server, execute the following commands:

**nlserver stop inMail@**instance****,

Adobe Campaign's Deliverability service manages your subscription to feedback loop services for the following ISPs: AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho.

Adding an SMTP header called **List-Unsubscribe** is mandatory to ensure optimal deliverability management.

This header can be used as an alternative to the "Report as SPAM" icon. It will display as an unsubscription link in the email interface.

>[!NOTE]
>
>This functionality is available from Build 6831.

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail, Outlook.com and Microsoft Outlook support this method and an unsubscribe button is available directly in their interface. This technique lowers complaint rates.

The command line must be added in the additional section of the email's SMTP header.

This addition can be done in each email, or in existing delivery templates. You can also create a new delivery template that includes this functionality.

The new SMTP header is a mandatory tool to control future communication and personal information that will be sent to Yahoo! users using an address which has been reattributed.

Adobe Campaign lets you add additional headers that use delivery properties such as **List-Unsubscribe** for example.

If the target email address is kelyslater@yahoo.com and this address has been present in the database since 12th October 2010, the header must be as follows:

```
Require-Recipent-Valid-Since: kelyslater@yahoo.com; 12 Oct 2010
```

If this email address has been reattributed to another Yahoo! user, an error message will indicate this reattribution as a quarantined address.

DKIM comes from a combination of the DomainKeys, Yahoo! and Cisco Identified Internet Mail authentication principles and is used to check the authenticity of the sender domain and guarantee the integrity of the message.

DKIM replaced **DomainKeys** authentication. Refer to [this section](../../delivery/using/technical-recommendations.md#domainkeys).

Using DKIM requires some prerequisites:

>[!NOTE]
>
>* This functionality is available from build 1937 onwards.
>* If you have configured DomainKeys for your Adobe Campaign instance, you just need to select **dkim** in the domain handling rules. If not, follow the same configuration steps (private/public key) as for DomainKeys.
>* It is not necessary to enable both DomainKeys and DKIM for the same domain as DKIM is an improved version of DomainKeys. 
>* The following domains currently validate DKIM: AOL, Gmail.
>

MX rules (Mail eXchanger) are the rules that manage communication between a sending server and a receiving server.

Depending on the material capacities and the internal policy, an ISP will accept a predefined number of connections and messages per hour. These variables may be automatically modified by the ISP system depending on the reputation of the IP and sending domain. Via its deliverability platform, Adobe Campaign manages more than 150 specific rules by the ISP, and, in addition, one generic rule for other domains.

These rules are updated via a daily workflow in order to regularly supply the client instance.

The maximum number of connections does not depend exclusively on the number of public IP addresses used by the MTA.

For instance, if you have allowed 5 connections in the MX rules and you have configured 2 public IPs you might think that you cannot have more than 10 connections simultaneously opened to this domain. This is not true, in fact the maximum number of connections refers to a path and a path that is a combination of one of our MTA public IPs and a public IP of the client's MTA.

In the example below, the user has two public IP addresses configured and the domain is yahoo.com.
