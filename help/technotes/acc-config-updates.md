---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: yes
hidefromtoc: yes
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
---
# Adobe Campaign configuration updates - March 2021 {#acc-config-updates}

Infrastructure and settings should be regularly updated with the latest builds and product fixes. These fixes are necessary to ensure continuity of service and security. In addition, upgrades will be required to align with third-party changes.

As a **Hosted or Managed Services customer**, Adobe will inform you of build upgrades at regular intervals. You will be required to upgrade in accordance with the recommendations to ensure compliance.

As an **On-premise or Hybrid customer**, you should upgrade your implementation at regular intervals in line with the latest released builds. 

For security reasons, you must now upgrade to one of the versions listed below. In addition to the standard upgrade steps, a few manual tasks must be performed to make sure that your environment is safe and ready for upcoming changes from Adobe or third-party systems.

>[!NOTE]
>
>For any questions about these changes, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Security updates {#acc-security-updates}

The latest Campaign versions come with a security fix which reinforces protection against Server Side Request Forgery (SSRF) issues. Learn more [in this page](https://helpx.adobe.com/security/products/campaign/apsb21-04.html).

**Are you impacted?**

If your environment is on a lower build than the ones listed below, you are impacted:

* Gold Standard 11. [Learn more](../rn/using/gold-standard.md)
* Campaign 21.1.1 release. [Learn more](../rn/using/latest-release.md)
* Campaign 20.3.3 release. [Learn more](../rn/using/release--20-3.md)
* Campaign 20.2.4 release. [Learn more](../rn/using/release--20-2.md)
* Campaign 20.1.4 release. [Learn more](../rn/using/release--20-1.md)
* Campaign 19.2.4 release. [Learn more](../rn/using/release--19-2.md)
* Campaign 19.1.8 release. [Learn more](../rn/using/release--19-1.md)

Learn how to check your version [in this section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**How to update?**

You need to upgrade to one of the newer builds listed above.

* As a hybrid customer, Adobe will inform you of the scheduled upgrade dates for your mid-sourcing instances. Adobe strongly recommends that you upgrade your marketing instance too.

    The new build is backwards compatible to Campaign Classic 17.9 release, but Adobe strongly recommends an upgrade on  all instances to address security vulnerabilities 

* As an on-premise customer, you are requested to upgrade marketing and mid-sourcing instances to the latest build. 

>[!CAUTION]
>
>If you cannot upgrade within the recommended timeframe, **you should contact Adobe Customer Care team to apply a short-term manual security fix on your instances**.
>

## Campaign Classic Client Console update  {#acc-cc-updates}

The **now available** console versions below should be installed to resolve a recently identified regression. This regression prevented the use of some components of the Client Console, such as the date picker and images management in deliveries. **Console upgrade** is mandatory. 

* Latest Gold Standard 11 build 9032&#64;10c2709. [Learn more](../rn/using/gold-standard.md)
* Campaign 20.1.4 release. [Learn more](../rn/using/release--20-1.md)
* Campaign 19.2.4 release. [Learn more](../rn/using/release--19-2.md)
* Campaign 19.1.8 release. [Learn more](../rn/using/release--19-1.md)

## Adobe Identity Management System (IMS) update

Adobe Identity Service (IMS) will stop supporting old Internet Explorer versions from **June 30, 2021**. [Learn more](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html). 

An upgrade of the Campaign Client Console is required to ensure compatibility with Adobe IMS.

**Are you impacted?**

If you are connecting to Campaign [via an Adobe ID](../integrations/using/about-adobe-id.md), through Adobe Identity Management Service (IMS), upgrade to one of the new versions listed below is mandatory:

* Gold Standard 11. [Learn more](../rn/using/gold-standard.md)
* Campaign 21.1.1 release. [Learn more](../rn/using/latest-release.md)
* Campaign 20.3.3 release. [Learn more](../rn/using/release--20-3.md)
* Campaign 20.2.4 release. [Learn more](../rn/using/release--20-2.md)
* Campaign 20.1.4 release. [Learn more](../rn/using/release--20-1.md)
* Campaign 19.2.4 release. [Learn more](../rn/using/release--19-2.md)
* Campaign 19.1.8 release. [Learn more](../rn/using/release--19-1.md)

These releases come with a new connection protocol: upgrade is mandatory for both Campaign server and Client Console to be able to connect to Campaign after **June 30, 2021**.

Learn how to check your version [in this section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**How to update?**

As a hosted customer, Adobe will be working with you to upgrade your instance(s) to the newer version shortly.

As an on-premise/hybrid customer, you need to upgrade to one of the newer versions to benefit from the new Client Console and ensure a seamless transition **before June 30, 2021**.

Once all instances are upgraded, the Client Console needs to be upgraded to this version as well.

* Learn how to access [Adobe Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Learn how to install Campaign Client Console](../installation/using/installing-the-client-console.md).

## Integration with Experience Cloud Triggers {#acc-triggers-updates}

The legacy oAuth authentication service has reached end-of-life. Triggers integration authentication, originally based on oAUTH authentication setup to access pipeline, has moved to Adobe I/O. It will be retired on **November 30, 2021**. [Learn more](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email). 

**Are you impacted?**

If your instances are running on an **older version than Campaign 19.1.8, 20.2.4, Gold Standard 11**, then you are using an older version of Triggers integration through oAuth authentication: **you need to upgrade to a newer version and move to Adobe I/O**. 

Upgrade to one of the new versions listed below is mandatory:

* Gold Standard 11. [Learn more](../rn/using/gold-standard.md)
* Campaign 21.1.1 release. [Learn more](../rn/using/latest-release.md)
* Campaign 20.2.5 release. [Learn more](../rn/using/release--20-2.md)
* Campaign 19.1.8 release. [Learn more](../rn/using/release--19-1.md)

Learn how to check your version [in this section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**How to update?**

Once the instances are upgraded to a newer version, all customers need to follow the [procedure move to the new authentication mode](../integrations/using/configuring-adobe-io.md). This requires you to generate the new Adobe I/O token and use it in the implementation.    

In addition, for hybrid environments, customers need to ensure that pipeline is configured on mid-sourcing instance. [Learn more](../integrations/using/configuring-pipeline.md).

[Learn how to migrate to Adobe I/O](../integrations/using/configuring-adobe-io.md). 

## APNs updates {#acc-apns-updates}

### HTTP/2-based APNs provider API

Since **March 31, 2021**, the Apple Push Notification service (APNs) no longer supports the legacy binary protocol. [Read more](https://developer.apple.com/news/?id=c88acm2b).

**Are your impacted?**

If your instances are running on an **older version than Campaign 21.1,** and you send push notifications with the legacy Apple binary protocol, you need to update to the HTTP/2-based APNs provider API. 

Learn how to check your version [in this section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**How to update?**

As a hosted customer, If you have upgraded to the new build,  Adobe has already updated your instance(s) to the HTTP/2-based API.

As an on-premise/hybrid customer, you need to update your configuration. [Learn how to migrate to HTTP/2](https://helpx.adobe.com/campaign/kb/migrate-to-apns-http2.html)

### APNs root certificate updates

On March 29 2021, an Apple Push Notification service (APNs) infrastructure update impacted Adobe Campaign Classic iOS channel. An OS configuration change is **mandatory** to avoid iOS push channel outage.

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
