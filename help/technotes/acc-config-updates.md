---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: yes
hidefromtoc: yes
---

# Adobe Campaign configuration updates - March 2021 {#acc-config-updates}

You must keep your infrastructure and settings updated with latest builds and product fixes. These fixes are mandatory to ensure service continuity and security. In addition, you need to adapt your implementation to align with third-party changes.

As a hosted customer, Adobe will inform you of required build upgrades at regular intervals. You need to upgrade in accordance with the recommendations to ensure compliance.

As an on-premise/hybrid customer, for security reasons, you must upgrade to one of the versions listed in this page. In addition, a few manual tasks must be performed to make sure that your environment is safe and ready for upcoming changes from Adobe or third-party systems.

>[!NOTE]
>
>For any question about these changes, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Security updates

Latest Campaign versions come with a security fix which reinforce protection against Server Side Request Forgery (SSRF) issues. Learn more [in this page](https://helpx.adobe.com/security/products/campaign/apsb21-04.html).

**Are you impacted?**

If your environment is on a lower build than the ones listed below, you are impacted:

* Gold Standard 11. [Learn more](../rn/using/gold-standard.md)
* Campaign 21.1.1 release. [Learn more](../rn/using/latest-release.md)
* Campaign 20.3.3 release. [Learn more](../rn/using/release--20-3.md)
* Campaign 20.2.4 release. [Learn more](../rn/using/release--20-2.md)
* Campaign 20.1.4 release. [Learn more](../rn/using/release--20-1.md)
* Campaign 19.2.4 release. [Learn more](../rn/using/release--19-2.md)
* Campaign 19.1.8 release. [Learn more](../rn/using/release--19-1.md)

**How to update?**

You need to upgrade to one of the newer builds listed above.

* As a hybrid customer, Adobe will upgrade the mid-sourcing instance to the new version and you are highly recommended to upgrade their marketing instance too.

    The new build is compatible with at least Campaign Classic 17.9 release, but to prevent any security gap, Adobe strongly recommends upgrading all instances to a new build.  

* As an on-premise customer, you are requested to upgrade marketing and mid-sourcing instances to a newer build. 

>[!CAUTION]
>
>If you cannot upgrade for now, **you must contact Adobe Customer Care team to apply manually a security fix on your instances**.
>

## Campaign Client Console update

Latest Gold Standard 11 build fixes a regression which prevented the usage of some components of the Clien Console, such as the date picker and images management in deliveries. Console upgrade is mandatory.

[Learn more](../rn/using/gold-standard.md).

>[!NOTE]
>
>The new Client Console for other versions will be available soon.

## Adobe Identity Management System (IMS) update

Adobe Identity Service (IMS) will stop supporting old Internet Explorer versions starting **June 30, 2021**. [Learn more](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html). 

Campaign Client Console has been updated to ensure compatibility with Adobe IMS in the following Campaign versions:

**Are you impacted?**

If you are connecting to Campaign [via an Adobe ID](../integrations/using/about-adobe-id.md), through Adobe Identity Service (IMS), upgrade to one of the new versions listed below is mandatory:

* Gold Standard 11. [Learn more](../rn/using/gold-standard.md)
* Campaign 21.1.1 release. [Learn more](../rn/using/latest-release.md)
* Campaign 20.3.3 release. [Learn more](../rn/using/release--20-3.md)
* Campaign 20.2.4 release. [Learn more](../rn/using/release--20-2.md)
* Campaign 20.1.4 release. [Learn more](../rn/using/release--20-1.md)
* Campaign 19.2.4 release. [Learn more](../rn/using/release--19-2.md)
* Campaign 19.1.8 release. [Learn more](../rn/using/release--19-1.md)

These releases come with a new connection protocol: upgrade is mandatory for both Campaign server and Client Console to be able to connect to Campaign after **June 30, 2021**.

**How to update?**

As a hosted customer, no action is needed: Adobe has already upgraded your instance(s) to a newer version.

As an on-premise/hybrid customer, you need to upgrade to one of the newer versions to benefit from the new Client Console and ensure a seamless transition **before June 30, 2021**.

Once all instances are upgraded, the Client Console needs to be upgraded to this version as well.

* Learn how to access [Adobe Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Learn how to install Campaign Client Console](../installation/using/installing-the-client-console.md).

## Integration with Experience Cloud Triggers

The legacy oAuth authentication service has reached end-of-life. Triggers integration authentication, originally based on oAuth authentication setup to access pipeline, has moved to Adobe I/O. It will be retired on **April 30, 2021**. [Learn more](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email). 

**Are you impacted?**

If your instances are running on an **older version than Campaign 19.1.8, 20.2.4, Gold Standard 11**, then you are using an older version of Triggers integration through oAuth authentication: **you need to upgrade to a newer version and move to Adobe I/O**. 

Upgrade to one of the new versions listed below is mandatory:

* Gold Standard 11. [Learn more](../rn/using/gold-standard.md)
* Campaign 21.1.1 release. [Learn more](../rn/using/latest-release.md)
* Campaign 20.3.3 release. [Learn more](../rn/using/release--20-3.md)
* Campaign 20.2.4 release. [Learn more](../rn/using/release--20-2.md)
* Campaign 19.1.8 release. [Learn more](../rn/using/release--19-1.md)

**How to update?**

Once the instances are upgraded to a newer version, all customers need to follow the [procedure move to the new authentication mode](../integrations/using/configuring-adobe-io.md). This requires to generate the new Adobe I/O token and use it in the implementation.    

In addition, for hybrid environments, customers need to ensure that pipeline is configured on mid-sourcing instance. [Learn more](../integrations/using/configuring-pipeline.md).

[Learn how to migrate to Adobe I/O](../integrations/using/configuring-adobe-io.md). 

## APNs updates

### HTTP/2-based APNs provider API

The Apple Push Notification service (APNs) will no longer support the legacy binary protocol as of **March 31, 2021**. [Read more](https://developer.apple.com/news/?id=c88acm2b).

**Are your impacted?**

If your instances are running on an **older version than Campaign 21.1,** and send push notifications with the legacy Apple binary protocol, you need to update to the HTTP/2-based APNs provider API. 

**How to update?**

As a hosted customer, no action is needed: Adobe has already updated your instance(s) to the HTTP/2-based API.

As an on-premise/hosted customer, you need to update your configuration. [Learn how to migrate to HTTP/2](https://helpx.adobe.com/campaign/kb/migrate-to-apns-http2.html)

### APNs root certificate updates

On March 29 2021, an Apple Push Notification service (APNs) infrastructure update will impact Adobe Campaign Classic iOS channel. An OS configuration change is **mandatory** to avoid iOS push channel outage.

Learn more about APNs changes [in this page](https://developer.apple.com/news/?id=7gx0a2lp).

**Are you impacted?**

If you are using Campaign to send push notifications on iOS devices, you are impacted.

**How to update?**

As a hosted customer, no action is needed: Adobe has already incorporated the new root certificate to your environment.

As an on-premise/hybrid customer, you need to update your configuration to ensure a seamless transition **before March 29 2021**.

[Learn how to incorporate the new certificate](ios-certificate-update.md).


## Useful links

* [Upgrade your environment](../production/using/build-upgrade.md)
* [Build upgrade FAQ](../platform/using/faq-build-upgrade.md)
* [Download Campaign Classic build](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Make the new Client Console available to users](../installation/using/client-console-availability-for-windows.md)
