---
solution: Campaign Classic
product: campaign
title: Get started with personalized links tracking
description: Learn how to write links in emails that can be personalized and support tracking in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
---
# Get started with personalized links tracking {#tracking-personalized-links}

The links in email content that contain personalization need specific syntax to be tracked. 

Using JavaScript in email content (HTML or Text) allows you to generate and send dynamic content to the recipients, with two limitations:

* The script cannot access the database directly (SQL function and API functions are not available),
* Adobe Campaign must be able to detect URLs so that links can be tracked. [Learn more](detecting-tracking-urls.md)

You can add specific pre-processing instructions to script the URL and track it. [Learn more](pre-processing-instructions.md)

For tracking detection, Adobe Campaign embeds [Tidy](http://www.html-tidy.org/) to parse the HTML source and detect the pattern. It lists all the URLs of the content so that they can be tracked individually. Adobe Campaign uses Tidy again to replace the URL (`http://myurl.com`) with a URL pointing to the Adobe Campaign redirection server.

For example, in the initial content: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` is replaced for one particular recipient with: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Where:

* "h" means HTML content (or "t" for text content).
* 617791 is the message ID / broadLog ID (hexadecimal).
* 71ffa3 is the NmsDelivery ID (hexadecimal).
* 71ffa8 is the NmsTrackingUrl ID (hexadecimal).
* p1, p2, and so on, are all the parameters to substitute in the URL.
