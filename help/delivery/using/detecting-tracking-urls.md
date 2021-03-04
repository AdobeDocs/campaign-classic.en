---
solution: Campaign Classic
product: campaign
title: Detecting tracking URLs
description: Learn more about recommended pattern to track URLs.
audience: delivery
content-type: reference
topic-tags: tracking-messages
---

# Detecting tracking URLs

## Example of non-detection

`<%= getURL("http://mynewsletter.com") %>` works and sends the actual content of the web page via email to the recipients. But none of the links are tracked. The reason for this is that the MTA executes `"<%=getURL(..."` for each email before sending. It can be different for each recipient, so Adobe Campaign cannot know the URLs for tracking and assign them a tag ID.

When the page to download is the same for all recipients, the best practice is to do the following:

`<%@ include url="http://mynewsletter.com" %>`

In that case, the page is downloaded during the analysis, before the tracking detection. It allows Adobe Campaign to discover the links, assign a tag ID, and track them.

## Recommended Pattern

After processing `<%@` instructions, the URL to be tracked has the following syntax: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>All other patterns are not supported by Adobe and should be avoided to prevent potential security gaps.

## Warnings on http://<%=myURL%> pattern

The `<a href="http://<%=myURL%>">` syntax is not secure and not recommended because:

* Tidy can incorrectly patch some of the links, which can happen randomly. The typical symptom is a piece of HTML that is visible in the email proofs but not in the preview.
* Escaping of the URL is problematic, some characters in the URL can cause problems.
* You cannot have a parameter named ID conflicting with parameter in the redirection URL.
* Interest of tracking is then limited to statistics on the delivery, as Adobe Campaign indifferently tracks all possible values of "myURL".

Refer to [this page](https://helpx.adobe.com/campaign/kb/acc-security.html#privacy) to learn more.

