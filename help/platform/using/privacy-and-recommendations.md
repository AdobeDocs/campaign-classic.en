---
title: Privacy and recommendations
seo-title: Privacy and recommendations
description: Privacy and recommendations
seo-description: 
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
index: y
internal: n
snippet: y
---

# Privacy and recommendations{#privacy-and-recommendations}

## About privacy and consent {#about-privacy-and-consent}

Adobe Campaign is a powerful tool for collecting and processing extremely large amounts of data, including personal information. We encourage all users of Adobe Campaign to work within legislation (DPA, CAN-SPAM, European Directive on Privacy and Electronic Communications, European GDPR, CCPA, etc.), make responsible and ethical use of personal information and refrain from sending unsolicited e-mail, push notifications and SMS messages ("spam"). We strongly believe in the principles of permission marketing in fostering customer lifetime value and loyalty, and we therefore strictly forbid the use of Adobe Campaign in sending unsolicited messages.

For more on this, refer to [Adobe Experience Cloud privacy](https://www.adobe.com/privacy/marketing-cloud.html).

Take the time to go through the [Security and Privacy checklist](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html) to learn the key elements to check regarding security and privacy.

## Privacy management {#privacy-management}

GDPR (General Data Protection Regulation) is the European Union’s (EU) privacy law that harmonizes and modernizes data protection requirements. GDPR applies to Adobe Campaign customers who hold data for Data Subjects residing in the EU.

CCPA (California Consumer Privacy Act) provides California residents new rights in regards to their personal information and imposes data protection responsibilities on certain entities whom conduct business in California.

In addition to consent management, data retention settings, and rights management, we provide, in our role as Data Processor, additional capabilities, to help facilitate your readiness as Data Controller for certain Privacy requests.

In this [article](https://helpx.adobe.com/campaign/kb/acc-privacy.html), you will learn how Adobe Campaign helps you manage the different Privacy key features: Right to Access, Right to be Forgotten, consent, data retention and user roles. You will also find best best practices, to help you with your Privacy compliance when using our service.

## Cookies and tracking capabilities {#cookies-and-tracking-capabilities}

Thanks to its tracking functionalities, Adobe Campaign enables you to track the browsing of your delivery recipients on a website. To do this, Adobe Campaign uses session cookies and permanent cookies.

European directive 2009/136/CE on "Privacy and Electronic Communications" and European General Data Protection Regulation (GDPR) state that companies require the agreement of website users before installing any cookies. You must inform users that your sites are equipped with web tracking tools via an authorization request (that comes up over the page, for example) with a checkbox to authorize the installation of cookies, or add a banner at the top of the first page they land on, etc. Pop-up windows should be avoided as they are often blocked by browsers.

The configuration of the user tracking management is available for the Web Applications and Landing Pages with an Opt-out banner. Refer to [this page](../../web/using/web-application-tracking-opt-out.md).

Adobe Campaign uses two types of cookies:

1. A session cookie (nlid): it contains the identifier of the email sent to the contact (broadlogId) and the identifier of the message template (deliveryId). It is added when the contact clicks a URL included in an email sent by Adobe Campaign and enables you to track their behavior on the web. This session cookie is erased automatically when the browser is closed. The contact can configure their browser to refuse cookies.
1. A permanent cookie (uuid230): it enables you to identify the users who interact with Adobe Campaign when they visit a website. It is used by Adobe Campaign to count the number of clicks and estimate of the transfer rate during a marketing campaign. It is placed when the contact clicks in an email, fills in a form in Adobe Campaign or during the call to the inbound interaction engine. The user can configure their browser to delete it or refuse it.

## Database integrity {#database-integrity}

Adobe Campaign has an abundance of features. It therefore uses a complex database structure. The database contains many tables, fields, links, and indexes. Certain intermediate tables are not displayed in the interface. The software automatically creates, deletes or modifies certain links, fields and indexes. Only Adobe Campaign interfaces (graphical interface, import program, server module, web module, delivery servers, add field, database extension, etc.) can modify the contents of the database while preserving its integrity.

**Never modify the database contents or structure using any tool other than this software**. Such modifications would be very likely to corrupt the database, resulting in: accidental modification or loss of links, creation of ghost records or links, serious error messages, etc., and rendering the guarantee and technical support contract provided by Adobe Campaign null and void.

In the Adobe Campaign system, all the data is stored in the database. Proper operation of the entire Adobe Campaign system depends on the availability of this data for: web modules for subscription, administration, and unsubscription, administration screens, delivery queues, delivery optimization mechanisms, etc.

## Apache Tomcat {#apache-tomcat}

Adobe Campaign includes Apache Tomcat, developed by the Apache Software Foundation ( [https://www.apache.org/](https://www.apache.org/)).
