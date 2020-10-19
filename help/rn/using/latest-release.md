---
title: Latest Release
description: Latest Campaign Classic Release
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
---

# Latest Release{#latest-release}

# Release 20.3{#release-20-3}

## ![](assets/do-not-localize/orange_2.png) Release 20.3.1 - Build XXX {#release-20-3-1-build-XXX}

_October 27, 2020_

**What's new?**

<table> 
<thead> 
<tr> 
<th><strong>IMS client console compatibility upgrade</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>To prevent incompatibility with some internet security GPO rules restrictions, Campaign client console logon screen has been replaced by a built-in standard Windows form.
</p>
<p>Windows 7 is no longer supported with Adobe Campaign CLassic. <a href=../../rn/using/deprecated-features.md>Read more</a>
</p>
<p>For more information, refer to the detailed documentation.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>iOS push notification improvements</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>You can now choose between two authentication modes for iOS in Campaign Classic:</p>
<ul> 
<li><p>Certificate-based authentication using p12 key.</p></li> 
<li><p>Token-based authentication using p8 certificate.</p></li>
</ul>
<p>For more information, refer to the <a href=../../delivery/using/configuring-the-mobile-application.md>detailed documentation</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Push - Android improvementss</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Android push notifications have been improved to support FCM HTTP/V1 API for Android push channel authentication. </p>
<p>With the new supported API version, you can now send FCM Notification Message which provides enhanced rich push messaging capabilities.</p>
<p>For more information, refer to the <a href=../../delivery/using/configuring-the-mobile-application-android.md>detailed documentation</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Compatibility updates and deprecated features**

The following systems are now supported with Campaign:
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

Learn more in the [Deprecated and removed features](../../rn/using/deprecated-features.md) page.

Starting 20.3, the demdex domain used to import and export audiences to the Adobe Experience Cloud is deprecated. If you are using the demdex domain for your import/export external accounts, you need to adapt your implementation accordingly. [Learn more](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)

**Improvements**

* In delivery properties, the **[!UICONTROL Archive emails]** option has been renamed **[!UICONTROL Email BCC]** for a better user experience.

