---
title: Domain name setup
description:  Learn how to configure your Adobe product for domain name setup and delegation.
feature: Deliverability
kt: 
thumbnail: 
doc-type: article
activity: understand
team: ACS
hidefromtoc: yes
---

# Domain name setup

This document describes the business and technical requirements for domain name setup and delegation. You will need to select an email sending subdomain and, optionally, an externally facing subdomain to host web components (landing pages, opt-out page) for the Adobe platform you are using.

## Sub-Domains

With Adobe, digital marketing can truly become the contextual engine that powers your brand’s customer engagement marketing program.  Email continues to be the foundation of digital marketing programs. However, reaching the inbox has become more difficult than ever.

Creating a sub-domain for email campaigns allows brands to isolate varying types of traffic (marketing vs. corporate for example) into specific IP pools and with specific domains, which will speed the [IP warming process](../../help/additional-resources/increase-reputation-with-ip-warming.md) and improve deliverability overall. If you share a domain and it gets blocked or added to the block list it could impact your corporate mail delivery, but reputation issues or blocks on a domain specific to your email marketing communications will impact just that flow of email.  Using your main domain as the sender or ‘From’ address for multiple mail streams could also break email authentication, causing your messages to be blocked or placed in the spam folder. 

### Delegation

Domain name delegation is a method that allows the owner of a domain name (technically: a DNS zone) to delegate a subdivision of it (technically: a DNS zone under it, which can be called a sub-zone) to another entity. Basically, if a customer is handling the zone "example.com", he can delegate the sub-zone "marketing.example.com" to Adobe Campaign.

This means that Adobe Campaign’s DNS servers will have full authority on only that zone and not the top-level domain. Adobe Campaign’s DNS servers will provide authoritative answers to queries on domain names in that zone, such as "t.marketing.example.com" itself but not “www.example.com”.

By delegating a sub-domain for use with Adobe Campaign, clients can rely on Adobe to maintain the DNS infrastructure required to meet industry-standard deliverability requirements for their email marketing sending domains, while continuing to maintain and control DNS for their internal email domains.  Sub-domain delegation allows:

Clients to keep their brand image by using a DNS alias with its domain names
Adobe to autonomously implement all the technical best practices to fully optimize deliverability during emailing

## DNS Setup Options

In order to provide a cloud-based managed service, Adobe strongly encourages clients to use sub-domain delegation when deploying Adobe Campaign.  However, Adobe does offer clients an alternative option – CNAME setup – for configuring DNS.

| Option | Description | Adobe Responsibilities | Client Responsibilities |
|--- |--- |--- |--- |
| Sub-domain delegation to Adobe Campaign | Client delegates a sub-domain (email.example.com) to Adobe. In this scenario, Adobe is able to deliver the Campaign as a managed service by controlling and maintaining all aspects of DNS that are required for delivering, rendering and tracking of email campaigns. | Complete management of the sub-domain and all DNS records required for Adobe Campaign. | Proper delegation of the sub-domain to Adobe |
|Use of CNAMEs | Client creates a sub-domain and uses CNAMEs to point to Adobe-specific records.  Using this setup, both Adobe and the customer share responsibility for maintaining DNS. | Management of DNS records required for Adobe Campaign. | Creation and control of the sub-domain and creation/management of the CNAME records required for Adobe Campaign. |

## Required DNS Records

| Record Type | Purpose | Examples Record/Content |
|--- |--- |--- |
| MX | Specify mail servers for incoming messages | <i>email.example.com</i></br><i>10 inbound.email.example.com</i> |
| SPF (TXT) | Sender Policy Framework | <i>email.example.com</i></br>"v=spf1 redirect=__spf.campaign.adobe.com" |
| DKIM (TXT) | DomainKeys Identified Mail | <i>client._domainkey.email.example.com</i></br>"v=DKIM1; k=rsa;" "DKIMPUBLICKEY HERE" |
| DMARC (TXT) | Domain-based Message Authentication | Reporting & Conformance | _dmarc.email.example.com</br>“v=DMARC1; p=none; rua=mailto:mailauth-reports@myemail.com” |
| Hosts Records (A) | Mirror pages, image hosting and tracking links, all sending domains | m.email.example.com IN A 123.111.100.99</br>t.email.example.com IN A 123.111.100.98</br>email.example.com IN A 123.111.100.97 |
| Reverse DNS (PTR) | Maps the client IP addresses to a client branded hostname | 18.101.100.192.in-addr.arpa domain name pointer r18.email.example.com |
| CNAME | Provides an alias to another domain name | t1.email.example.com is an alias for | t1.email.example.campaign.adobe.com |

## Setup Requirements

### Sub-Domain delegation

This requires the client to create a sub-domain in their DNS servers and define the name servers for this sub-domain to be those maintained by Adobe.  For example, a client whose main domain name is “example.com” and who wants to delegate the management of “marketing.example.com” to Adobe for its email deliveries will have to materialize this delegation to add the following type records to its DNS:

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

Delegation of a domain name implies that this domain will be dedicated to delivering email via the Adobe Campaign platform, and therefore cannot be used for other means (e.g. sending email from another email infrastructure).

During the setup process, Adobe will ensure the domain is attached to the Adobe incoming email infrastructure in order to manage and process the rebound emails coming back to these domains (MX type DNS record configuration).

### Use of CNAMEs

If the client chooses to use CNAMEs rather than delegate a sub-domain to Adobe, during the setup phase, Adobe will provide the records to be placed in the client DNS servers and will configure the corresponding values in Adobe Campaign DNS servers.

## General requirements for Deployment

When implementing a new enterprise marketing solution, there are requirements for externally-facing components.  These include hosting landing pages and web forms, setting up links and web pages to be tracked, displaying mirror pages, and configuring an opt-out page.

While these requirements are being managed through components hosted by both Adobe and the customer, they include URLs which can be seen by the recipients of the emails.  To avoid having URLs which indicate the underlying technical solution or hosting provider, subdomains can be set up to make this transparent to the recipients of the emails.  For example, when looking at a URL such as, http://www.customer.com/, the domain would be “www.customer.com”.  The subdomain of this would be “www”.

### Sub-Domain requirements

Determine the subdomain(s) to be used for branded URLs (mirror pages and tracking URLs) from the Adobe Campaign application.  Also decide what the “From Address”, “From Name” and “Reply-To Address” will be for each subdomain on email deliveries.

Complete the table below, first line is only an example.

| Subdomain | From address | From name | Reply-to address |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | Customer | customercare@customer.com |
|  </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* The purpose of the “Reply-To Address” field is when you want the recipient to reply to a different address than the “From Address”.  While not a required field, Adobe strongly recommends that the “Reply-To Address” be valid and linked to a monitored mailbox.  This mailbox must be hosted by the customer.  It could be a support mailbox, e.g.  customercare@customer.com, where emails are read and responded to.
>* If no “Reply-To Address” is chosen by the customer, then the default address is always <tenant>-<type>-<env>@<subdomain>.
>* When the “Reply-To Address” is set up this way, replies will be sent to an unmonitored mailbox.
>* When sending emails from Adobe Campaign, the “From Address” mailbox is not monitored and marketing users cannot access this mailbox. Adobe Campaign also does not offer the ability to Auto-Reply or Auto-Forward emails received in this mailbox.
>* The Campaign From/Sender address and Error address cannot be “abuse” or “postmaster”.

## Delegating Sub-Domains

The subdomain(s) chosen to be used for the Adobe Campaign platform must be delegated by creating four name server (NS) records.  This allows the subdomain to be properly delegated to Adobe.  Below is an example of a subdomain delegation and the respective DNS instructions.  Please substitute ‘emails.customer.com’ with the subdomain you wish to delegate.  Please note that the subdomain must be unique and cannot already be in use by another party (for example, an existing ESP or MSP).

| Delegated subdomain | DNS Instructions |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com. </br> `<subdomain>` NS b.ns.campaign.adobe.com. </br> `<subdomain>` NS c.ns.campaign.adobe.com. </br> `<subdomain>` NS d.ns.campaign.adobe.com. |

Tracking, Mirror pages, Resources
Once the email sending subdomain(s) is/are properly delegated to Adobe Campaign, the Adobe TechOps team will create two or more lower-level domains to manage tracking and mirror pages independently.

| Type | Domain |
|--- |--- |
| Mirror pages | m.`<subdomain>` |
|Tracking | t.`<subdomain>` |
|Resources | res.`<subdomain>` |

## Cloud deployment (optional)

This only applies if the Adobe Campaign Classic is fully hosted in the cloud by Adobe.  This is an optional configuration.

Any surveys, web forms, and landing pages to be developed are managed through Adobe Campaign fully hosted in the cloud.  If required, an additional subdomain may be delegated to Adobe (e.g. web.customer.com) to use for any web components within the tool.  Please note that the subdomain needs to be unique and can’t be used by another party (for example, an existing ESP or MSP).

| Delegated subdomain | DNS Instructions |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com.</br>`<subdomain>` NS b.ns.campaign.adobe.com.</br>`<subdomain>` NS c.ns.campaign.adobe.com.</br>`<subdomain>` NS d.ns.campaign.adobe.com. |

>[!NOTE]
>
>By default any web components in the tool will use the initial subdomain delegated to be used for email.

## Cloud messaging deployment (optional)

In the case that the Adobe Campaign Classic marketing instance is hosted on premise at the customer, additional technical configurations will need to be made by the customer.

Any surveys, web forms, and landing pages to be developed are managed through the Adobe Campaign marketing instance, where the recipient records exist. 

Additional CNAME DNS configuration is required to deploy externally-facing web components hosted by the Adobe Campaign marketing instance.  This will allow web components (e.g. web.customer.com) to be publicly accessible to the Internet and branded with the customer's domain.

Firewall(s) will also need to be configured to allow access to the Adobe Campaign marketing instance which hosts these web components (on port 80 or 443).

**Best Practice Recommendations:**

The subdomain to host web components will be visible to customers, so be sure to make it properly branded and simple to remember as it may need to be typed in manually, e.g. https://web.customer.com.
If any forms need to be hosted on secure pages (HTTPS) addition technical configuration will be required, described below.

| Delegated subdomain | DNS Instructions |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME `<internal customer server>` |

## Services Rendered

Following these delegations, the infrastructure put in place by Adobe ensures the following services are carried out for each delegated or CNAME-aliased sending domain:

* Creation of postmaster@ and abuse@ inboxes
* Setup of Feedback loops for the delegated domain
* Upon request, Adobe will also configure a DMARC record as specified. Your Deliverability Consultant can assist with designing a long-term DMARC policy and plan for your sending domains.
Parameters established by Adobe are only valid from the time that the delegation was completed and then verified by Adobe, and remains functional.  All Adobe Campaign Cloud offers include domain name delegation as standard.

## Billing and implementation conditions

* According to the initial contract and the type of package selected, other delegations in addition to those included as standard beyond this initial delegation may be included,
* Beyond these included delegations, additional delegations will be billed,
* The billing method for these additional delegations comes at an extra monthly cost, as specified in the initial contract.

These delegations will be accepted provided that the CLIENT chooses the associated domain names that are dedicated to deliveries via the Adobe Campaign tool, and that the delegation prerequisites detailed in the relevant document are correctly implemented.

## Discontinuation of services

At any moment, the CLIENT will be able to make a written demand to no longer benefit from the delegation services and to take on the necessary DNS configurations themselves.

If this should happen, Adobe will provide the CLIENT with an estimate detailing the number of service days necessary to return back to non-domain-delegation mode.

Adobe will be relieved of any liability for the engagement of the aforementioned Deliverability Rate if the Customer fails to comply with the commitments set out above.

Termination of the Marketing Cloud Service will automatically lead to the end of domain delegations, and DNS maintenance for those domains by Adobe.

## Monitoring sub-domains using the Control Panel

Once sub-domains are configured for your instance, you can monitor them using the Control Panel.

This allows you to view all the sub-domains that you delegated to Adobe Campaign, as well as request renewal of their SSL certificates.

For more on this, refer to the [dedicated documentation](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html#subdomains-and-certificates).

>[!NOTE]
>
>[Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html) is available to customers using Adobe Managed Services only.