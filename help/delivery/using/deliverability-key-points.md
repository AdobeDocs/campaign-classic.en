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
---

# Deliverability key points{#deliverability-key-points}

To optimize the deliverability of your Adobe Campaign emails, we recommend using the best practices listed below. Deliverability problems are generally linked to measures of protection against spam implemented by Internet service providers and mail server administrators.

**Email deliverability** refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format.

These characteristics fall into four main categories:
* Data quality
* Message and content
* Sending infrastructure
* Reputation

Together, they form the foundation of a successful email deliverability program.

The **deliverability rate** is the number of sent emails that were successfully delivered to its recipients.

The deliverability rate depends on numerous factors, particularly:
* Correct configuration of your instances
* Your IP address reputation
* Quality of the addresses targeted
* Low complaints and hard bounce rates
* Your message content
* Message authentication (SPF, DKIM, DMARC)
* Sender reputation

Below is a list of the key points to check to ensure good deliverability.

## Check network configuration {#network-configuration}

Spammers try to conceal their real identity and as a consequence make their servers difficult to identify. A legitimate network configuration that does not try to hide the identity of the server is essential to sending emails in large volumes.

## Send to valid addresses {#valid-addresses}

Spammers often use address generators based on lists of frequent names and first names; in addition, they rarely process technical notifications sent back by mail servers. A high rate of invalid addresses is often interpreted as a sign of spam. Double opt-in mechanisms and effective handling of technical bounce messages make it possible to avoid this.

## Reduce complaints and bounce rates {#reduce-complaint-rates}

ISPs usually have a prominent means of reporting a received message as spam. This makes it possible to identify unreliable sources. By rapidly honoring opt-out requests, making regular use of a given list, verifying consent through a double opt-in system, and implementing feedback loops, you can reduce complaint rates.

## Send to honeypot addresses {#honeypot-addresses}

ISPs and other organizations (see the [Project Honey Pot](https://www.projecthoneypot.org/) website) make use of mailboxes that do not correspond to physical persons but are created simply to trick spammers. These so-called "honey pot" addresses are published on the Web in order to be collected by spambots and thus catch illegitimate senders. The use of a double opt-in mechanism precludes this sort of address being added to a list. When using a third-party list, you must be sure of the methods employed by its maintainer.

## Adapt the message content {#message-content}
 
 To a lesser degree, the content of certain messages can lead certain filters to detect it as spam. The use of certain words, the use of exclamation points in the subject line and within the messages are read as tell-tale signs of spam. Spammers are also known to replace text with images to stop offending text from being analyzed automatically by anti-spam filters. In response to this, a message (in HTML format) with a high proportion of images, or images as attachments, may end up being blocked.

## Work on your reputation {#reputation}
 
Spammers make programmed deliveries to maintain their reputation over time. They sometimes need to adapt their marketing plan to meet the best practices imposed by the ISPs and so, after a peak in reputation (ramp-up), they configure regular deliveries.

## Best practices {#best-practices}

Learn best practices related to deliverability with Adobe Campaign. Use the links below to navigate topics and find guidance.

<table>
<tr>
  <td>
    <a href="starting-new-platform.md">
      <img alt="Start" src="assets/do-not-localize/start.svg" width="60px"/>
    </a>
    <div>
      <a href="starting-new-platform.md">
    <strong>Start</strong>
    </a>
    </div>
    <p>
    <em>Starting a new platform</em>
    <p>
  </td>
   <td>
    <a href="control-message-content.md">
      <img alt="Design" src="assets/do-not-localize/design.svg" width="60px"/>
    </a>
    <div>
      <a href="control-message-content.md">
    <strong>Design</strong>
    </a>
    </div>
    <p>
    <em>Control message content</em>
    <p>
  </td>
  <td>
    <a href="improve-reputation.md">
      <img alt="Design" src="assets/do-not-localize/check.svg" width="60px"/>
    </a>
    <div>
      <a href="improve-reputation.md">
    <strong>Send</strong>
    </a>
    </div>
    <p>
    <em>Improve your reputation</em>
    <p>
  </td>
</tr>
<tr>
  <td>
    <a href="technical-recommendations.md">
      <img alt="Optimize" src="assets/do-not-localize/optimize.svg" width="60px"/>
    </a>
    <div>
      <a href="technical-recommendations.md">
    <strong>Optimize</strong>
    </a>
    </div>
    <p>
    <em>Technical recommendations</em>
    <p>
  </td>
   <td>
    <a href="monitoring-deliverability.md">
      <img alt="Check" src="assets/do-not-localize/monitor.svg" width="60px"/>
    </a>
    <div>
      <a href="monitoring-deliverability.md">
    <strong>Monitor</strong>
    </a>
    </div>
    <p>
    <em>Monitoring tools</em>
    <p>
  </td>
  <td>
    <a href="deliverability-faq.md">
      <img alt="Optimize" src="assets/do-not-localize/troubleshoot.svg" width="60px"/>
    </a>
    <div>
      <a href="deliverability-faq.md">
    <strong>Troubleshoot</strong>
    </a>
    </div>
    <p>
    <em>Solve issues</em>
    <p>
  </td>
</tr>
</table>
