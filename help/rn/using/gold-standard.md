---
solution: Campaign Classic
product: campaign
title: Gold Standard release
description: Campaign Classic Gold Standard Release notes
audience: rns
content-type: reference
topic-tags: latest-release-notes
---

# Gold Standard releases{#gold-standard}

Gold Standard is Campaign Classic Long-Term support release. As a hosted Gold Standard user, you automatically benefit from the Gold Standard upgrade with the latest stable version without any action. On-premise and Hybrid customers can also benefit from Gold Standard releases.

If you migrate from an old build, we recommend that you upgrade to this version first.

This page lists Gold Standard releases.

For more information on Campaign Gold Standard program, refer [to this article](https://helpx.adobe.com/campaign/kb/gold-standard.html).

## ![](assets/do-not-localize/limited_2.png) Gold Standard 11 release{#gs-11}

_22 December 2020_

>[!CAUTION]
>
>This release comes with a new connection protocol: upgrade is mandatory for both Campaign server and client console to be able to connect to Campaign after March 21st, 2021.

The build 9032&#64;d3b452f includes the following improvements and fixes:

* The connection protocol has been updated to follow the new IMS authentication mechanism. 

* Triggers integration authentication originally based on oAUTH authentication setup to access pipeline has now been changed and moved to Adobe I/O. [Learn more](../../integrations/using/configuring-adobe-io.md)

* Following the end of support for iOS APNs legacy binary protocol, all instances using this protocol are updated to HTTP/2 protocol during postupgrade.

* Fixed a security issue to reinforce protection against Server Side Request Forgery (SSRF) issues. (NEO-27777)

## ![](assets/do-not-localize/green_2.png) Gold Standard 10 release{#gs-10}

_7 July 2020_

The build 9032&#64;efd8a94 includes the following fix:

Fixed an issue which prevented tracking from working when the signature feature was disabled. (NEO-26411)

>[!CAUTION]
>
>We recommend that you upgrade the client console with the one available in this release. Refer to [this page](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) Gold Standard 9 release{#gs-9}

_22 June 2020_

The build 9032&#64;800be2e includes the following fixes:

* The iOS HTTP2 connector has been improved (third-party updates and error management). (NEO-25904, NEO-25903, NEO-25799)

The following fixes are related to the tracking link security mechanism (learn more in the [Security and Privacy checklist](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)):

* Fixed an issue which prevented the tracking of "notification clicks" from working (iOS and Android push notifications). (NEO-25965)
* Fixed an issue which could prevent you from opening/clicking tracking URLs when using certain legacy versions of Outlook.  (NEO-25688)
* Fixed an issue which prevented the tracking of URLs using fragments in personalization parameters (anchor tags with pound-sign) from working. (NEO-25774)
* Fixed an issue with the anti-phishing service. (NEO-25283)
* Fixed a tracking issue when using specific custom tracking formulas. (NEO-25277)

## ![](assets/do-not-localize/red_2.png) Gold Standard 8 release{#gs-8}

_29 April 2020_

The build 9032&#64;3a9dc9c includes the following fixes:

* Improved security on tracking links in email. This is enabled by default for all customers. An additional, enhanced security feature is available which can be enabled by reaching out to Customer Care. More details on the feature and steps for non-hosted customers to enable it can be found in the [Security and Privacy checklist](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

 >[!CAUTION]
 >
 >If you experience issues with push notifications using tracking links, or deliveries using anchor tags, we recommend that you disable the new signature mechanism for tracking links. The procedure is detailed [in this page](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)

* Fixed an issue which could prevent images from being displayed on Line deliveries. (NEO-23207)
* Fixed an issue with the **File Transfer** activity which prevented SFTP key based authentication from working on Debian 9. (NEO-23183) 
* Fixed an issue which could affect push notification when sent at a high frequency. (NEO-20516)
* Fixed an issue in offer response management which could lead to web server crashes. (NEO-19482)
* Fixed an error in LibreOffice management which prevented you from exporting reports. (NEO-20982)
* Fixed an issue which caused an error when upgrading numerous workflows using a survey activity. 
* Improved LibreOffice management to avoid failures on email preview with .odt files. 
* Improved the management of Apache connection to avoid latency on web service.
* Improved the display of version tag (7 digit) in the **About** menu.
* Fixed a regression in list management preventing offers from being published.
* Fixed a regression causing the cleanup workflow to crash. 
* Fixed a minor regression in the cleanup workflow logs.

## ![](assets/do-not-localize/red_2.png) Gold Standard 6 release{#gs-6}

_9 March 2020_

The build 9032&#64;19f73c5 includes the following fix:

* Fixed an issue with external accounts using FTP over SSL. (NEO-20498)

## ![](assets/do-not-localize/red_2.png) Gold Standard 5 release{#gs-5}

_17 December 2019_

The build 9032&#64;d6b8062 includes the following fix:

* Fixed a tracking issue on the following communication channels: mobile (SMS, MMS), push (iOS, Android) and social networks (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/red_2.png) Gold Standard 4 release{#gs-4}

_11 December 2019_

The build 9032&#64;bc4a935 includes the following fix:

* Fixed a performance isssue when sending messages with a MSSQL database. (NEO-17558)

## ![](assets/do-not-localize/red_2.png) Gold Standard 3 release{#gs-3}

_20 November 2019_

The build 9032&#64;3468c7b includes the following fixes:

* Fixed a login issue via IMS authentication. (NEO-17312)
* Fixed an issue when displaying cumulative reports on multiple deliveries. (NEO-18165)
* Fixed an issue that could block or make the web server crash.

## ![](assets/do-not-localize/red_2.png) Gold Standard 2 release{#gs-2}

_19 September 2019_

The build 9032&#64;cee805c includes the following fixes:

* Fixed an issue when using the CRM Connector for Salesforce. (NEO-17712)
* Fixed an index issue which could cause performance issues when sending transactional messages.

## ![](assets/do-not-localize/red_2.png) Release 19.1.4 - Build 9032{#release-19-1-4-build-9032}

_13 August 2019_

The initial 19.1.4 build includes the following fixes:

* Fixed an issue with the scheduler activity generating undesired error messages during wizard configuration. Reverting update from NEO-11662. (NEO-17097)
* Fixed a regression caused by the NEO-12727 which could lead to workflows being stopped when a Test activity was executed twice. (NEO-16835) 
* Fixed an issue which led to an erroneous HTTP code being returned (HTTP 200 OK instead of HTTP 403 Forbidden) when an invalid or expired session token was used in API calls. (NEO-16826) 
* Fixed an issue with the DKIM key which was not embedded into emails anymore, thus causing deliverability issues. (NEO-16804) 
* Fixed various issues with workflow scheduling. Workflows were scheduled to be executed once a day without taking into account the scheduler configuration. (NEO-16619, NEO-16426)
