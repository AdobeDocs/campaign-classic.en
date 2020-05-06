---
title: Latest Release
description: Latest Release
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
---

# Latest Release{#latest-release}

[Build upgrade](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) &#124; [Control Panel releases](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) &#124; [Documentation updates](../../rn/using/documentation-updates.md) &#124; [Previous releases](../../rn/using/release--19-2.md) &#124; [Deprecated features](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>General Availability</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Release Candidate</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>No longer available</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>Deprecated</strong></td> 
  </tr> 
   <tr> 
   <td>Latest stable build available. Build validated in production.<br>&nbsp;</td>
   <td>Build validated by Adobe. Waiting for production proofing.<br>&nbsp;</td>
   <td>Newer build available with bug fixes. Update is required.<br>&nbsp;</td>
   <td>Contains known regressions. Update is mandatory.<br>&nbsp;</td>
  </tr> 
 </tbody> 
</table>

The **last stable build** is 9032 (3a9dc9c). Click [here](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/do-not-localize/blue_2.png) Release 20.2- Build XXXX {#release-20-2-build-XXXX} 

June 8, 2020_

**What's new?**

<table> 
<thead> 
<tr> 
<th> <strong>XXXX</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>XXX</p>
<p>For more information, refer to the <a href="../../xxx">detailed documentation</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead> 
<tr> 
<th> <strong>XXX</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>XXX</p>
<p>For more information, refer to the <a href="../../xxx">detailed documentation</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Security enhancements**

* XX

**Improvements**

* Shared memory version has been increased from 18 to 50 characters. However we recommend that you do not use more than 40 characters for the name of the instance added to the domain name. This evolution should be transparent for users. If you get an error, refer to the **Technical evolution** section below.

**Other changes**

* XXX

**Technical evolutions**

Regarding the shared memory version improvement, you should not have to do anything.

For on-premise customers, you may need to delete shared memory after the upgrade (see instructions on this [page](../configuration/additional-parameters.md#redirection-server-configuration)) ONLY if you encounter the following error:

```
SRV-810031 Bad version for the shared memory block 'NlServerContext6.0'. Current version is 106, expected version 107. Please restart all services (nlserver and web server)...
```

**Patches**

* XXX