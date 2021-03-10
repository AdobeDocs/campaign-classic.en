---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: yes
hidefromtoc: yes
---

# Adobe Campaign configuration updates - March 2021 {#acc-config-updates}

You need to keep your infrastructure and settings updated with latest builds and product fixes. These fixes are mandatory to ensure service continuity and security. 

Campaign users need to upgrade to one of the latest versions below:

* Gold Standard 11. [Learn more](../rn/using/gold-standard.md)
* Campaign 21.1.1 release. [Learn more](../rn/using/latest-release.md)
* Campaign 20.3.3 release. [Learn more](../rn/using/release--20.3.md)
* Campaign 20.2.4 release. [Learn more](../rn/using/release--20.2.md)
* Campaign 20.1.4 release. [Learn more](../rn/using/release--20.1.md)
* Campaign 19.2.4 release. [Learn more](../rn/using/release--19.2.md)
* Campaign 19.1.8 release. [Learn more](../rn/using/release--19.1.md)

These builds ensure the continuity of certain Campaign services: Experience Cloud Triggers integration, APNs authentication and the new connection protocol which impacts Adobe Identity Management Service (IMS) authentication mechanism.  

As a hosted customer, no action is needed: Adobe owns the build upgrade and configuration updates for you. 

As an on-premise/hybrid customer, you need to upgrade to one of the version listed above. In addition, you need to perform a few manual tasks to make sure your environment is safe and ready for upcoming changes from Adobe or third-party systems.

## Security updates

Latest Campaign versions come with a security fix which reinforce protection against Server Side Request Forgery (SSRF) issues. Learn more [in this page](https://helpx.adobe.com/security/products/campaign/apsb21-04.html).

### Are you impacted?

If your environment is on a lower build than Campaign 21.1, you are impacted.

## How to update?

You need to upgrade to one of the newer builds listed above.

* As an hybrid customer, Adobe will upgrade the mid-sourcing instance to the new version and you are highly recommended to upgrade their marketing instance too.
The new build is compatible with at least Campaign Classic 17.9 release, but to prevent any security gap, Adobe strongly recommends to upgrade all instances to a new build.  

* As an on-premise customer, you are requested to upgrade marketing and mid-sourcing instances to a new build. 

>[!CAUTION]
>
>If you cannot upgrade for now, **you must contact Adobe Customer Care team to apply manualy a security fix on your instances**.
>

## Campaign Client Console update

Latest Gold Standard 11 build fixes a regression which prevented the usage of some components of the console, such as the date picker and images management in deliveries. Console upgrade is mandatory.

[Learn more](../rn/using/gold-standard.md).

## Connect to Campaign through IMS

Adobe Identity Service (IMS) will stop supporting old Internet Explorer versions starting March 31 2021. [Learn more](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html). Campaign Console has been updated to ensure compatibility with IMS.

### Are you impacted?

If you are connecting to Campaign [via an Adobe ID](../integrations/using/about-adobe-id.md), through Adobe Identity Service (IMS), upgrade to one of the new versions listed above is mandatory for both Campaign server and client console to be able to connect to Campaign after **March 31, 2021**.

### How to update?

As a hosted customer, no action is needed: Adobe has already upgraded your instance(s) to a newer version.

As an on-premise/hybrid customer, you need to upgrade to one of the newer versions to benefit from the new Client Console and ensure a seamless transition **before March 31, 2021**.

## Integration with Experience Cloud Triggers

The legacy oAuth authentication service has reached end-of-life, it will be retired on April 30, 2021. [Learn more](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411). 

### Are you impacted?

If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O**. 

### How to update?

[Learn how to migrate to Adobe I/O](../integrations/using/configuring-adobe-io.md). 

## HTTP/2-based APNs provider API

The Apple Push Notification service (APNs) will no longer support the legacy binary protocol as of March 31, 2021. [Read more](https://developer.apple.com/news/?id=c88acm2b).

### Are your impacted?

If your instances are running on an older version than Campaign 21.1, and send push notifications with the legacy Apple binary protocol, you need to update to the HTTP/2-based APNs provider API. 

### How to update?

As a hosted customer, no action is needed: Adobe has already updated your instance(s) to the HTTP/2-based API.

As an on-premise/hosted customer, you need to update your configuration. [Learn how to migrate to HTTP/2](https://helpx.adobe.com/campaign/kb/migrate-to-apns-http2.html)

## APNs root certificate updates

On March 29 2021, an Apple Push Notification service (APNs) infrastructure update will impact Adobe Campaign Classic iOS channel. An OS configuration change is **mandatory** to avoid iOS push channel outage.

Learn more about APNs changes [in this page](https://developer.apple.com/news/?id=7gx0a2lp).

### Are you impacted?

If you are using Campaign to send push notifications on iOS devices, you are impacted.

### How to update?

As a hosted customer, no action is needed: Adobe has already incorporated the new root certificate to your environment.

As an on-premise/hybrid customer, you need to update your configuration to ensure a seamless transition **before March 29 2021**.

[Learn how to incorporate the new certificate](ios-certificate-update.md)
