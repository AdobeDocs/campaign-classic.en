---
title: Release 18.6 - Build 8947
seo-title: Release 18.6 - Build 8947
description: Release 18.6 - Build 8947
seo-description: 
page-status-flag: never-activated
uuid: c5994d92-969b-40ac-bf35-449341b51406
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 11d03b77-031c-4589-8213-52894777e668
index: y
internal: n
snippet: y
---

# Release 18.6 - Build 8947{#release-build}

25 June 2018

## What's new? {#what-s-new-}

<table> 
 <thead> 
  <tr> 
   <th> Functionality<br /> </th> 
   <th> Description<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Security improvements<br /> </td> 
   <td> A series of security improvements has been added to Campaign Classic. Improvements and fixes are listed below.<br /> </td> 
  </tr> 
  <tr> 
   <td> Support of Windows Server 2016<br /> </td> 
   <td> Adobe Campaign is now compatible with Windows Server 2016. Refer to <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.md">Campaign Classic Compatibility matrix</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Security enhancements {#security-enhancements}

**decryptString**

The **decryptString** function is deprecated. Refer to the [Deprecated and Removed Features](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.md) article.

For new customers, this function is now only used to decrypt the recipient's crypted ID in landing pages. To decrypt passwords stored in an external account, use the new **decryptPassword** function.

For existing customers, the behavior of this function is not changed but we recommend that you use **decryptPassword** instead of **decryptString**. The **XtkSecurity_Unsafe_DecryptString** compatibility option is added by the postupgrade and activated by default, allowing you to keep using the function. If you want to deactivate **decryptString**, deactivate the option.

**decryptPassword**

The **decryptPassword** function has been added. It allows you to decrypt a password stored in an external account. Refer to the [JSAPI](https://helpx.adobe.com/campaign/kb/compatibility-matrix.md) documentation for more information.

**File APIs**

For new installations, folder access via file APIs is limited to the **var**, **sftp** and temporary folders of Adobe Campaign.

For existing customers, file APIs can no longer access the **conf** folder of Adobe Campaign. The **XtkSecurity_Disable_JSFileSandboxing** compatibility option is added by the postupgrade and activated by default, allowing you to keep accessing the other folders. If you want to limit the access to the **var**, **sftp** and temporary folders of Adobe Campaign, deactivate the option.

## Patch {#patch}

* Fixed an issue that could affect SMS transactional message performance. (NEO-9812)

