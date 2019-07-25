---
title: Release 18.4.5 - Build 8937
seo-title: Release 18.4.5 - Build 8937
description: Release 18.4.5 - Build 8937
seo-description: 
page-status-flag: never-activated
uuid: 75f06a18-9673-4d6e-81fc-94e89e4a43d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
audience: rn
discoiquuid: 9ec26902-a155-4bc4-8d0e-5e2a37a3f298
index: y
internal: n
snippet: y
---

# Release 18.4.5 - Build 8937{#release-build}

21 November 2018

## Improvements {#improvements}

* Fixed various issues when running workflows using MySQL on FDA. (NEO-11652)
* Fixed an issue which caused a portion of the delivery population to remain in pending state, in specific cases. (NEO-11336) 
* Fixed an intermittent issue with the SMS auto response. (NEO-11811) 
* Fixed an ID exhaustion issue when using seed addresses in a delivery. (NEO-11842)
* Fixed a syntax error when performing a sort in an enrichment workflow activity. (NEO-11394) 
* Fixed an issue which could cause a web server crash when restarting IIS. (NEO-10862) 
* Fixed an issue which could cause the tracking workflow to fail after a build upgrade (FDA - SQL). (NEO-11635) 
* Fixed an issue which could cause workflow list data to be lost. (NEO-11696) 
* Fixed a performance issue when sending push notifications. (NEO-11787)
* Fixed an issue which prevented web tracking from working for "com.au" domains (NEO-4385). 
* Fixed a client freeze issue which could occur when using complex workflows. (NEO-11847)
* Fixed an Oracle error when saving a new delivery after selecting an element of a specific schema (NEO-11682). 
* Fixed an issue when querying a field containing characters with accents (FDA/Teradata). The external account now allows you to change the encoding used to communicate with the Teradata driver. (NEO-11818). 
* Fixed a tracking issue when passing URLs in additional variables in a push notification which could lead to mis-formatted or incorrect data received by the mobile application. (NEO-11468, NEO-11960) 
* Fixed an issue which caused a display issue when using a distribution of values with a 1:N link. (NEO-11820)
* Fixed an issue which prevented bulk load from working on Teradata 16. 
* Increased the buffer size for timestamp on Teradata to avoid binding issues with 15.10 driver. 
* Improved the management of long name indexes which could cause postupgrade issues. 
* Improved shared memory available time during children dead processing (MTA).
* Fixed a potential deadlock in Apache (tracking).

