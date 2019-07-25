---
title: Release 18.10.4 - Build 8983
seo-title: Release 18.10.4 - Build 8983
description: Release 18.10.4 - Build 8983
seo-description: 
page-status-flag: never-activated
uuid: d663cb48-87a0-4f8a-a286-693699e5bcc4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
audience: rn
discoiquuid: 264a92cc-1bbd-47c1-9965-57ef9fe25e3e
index: y
internal: n
snippet: y
---

# Release 18.10.4 - Build 8983{#release-build}

15 April 2019

## Improvements {#improvements}

* Fixed an issue with the computing process of tracking indicators for transactionnal messages. (NEO-12529, NEO-12581)
* Fixed an issue with the HTTPRequest API which did not wait for all callbacks to finish. (NEO-12628)
* Indexes were added in the coupon temporary tables to optimize delivery sending. (NEO-12437)
* Fixed an issue when analyzing a message which targeted recipients for Japanese (.JP) domains. (NEO-12246)
* In the Analytics integration, the retrieval of AAM segment data with % character is now allowed. (NEO-12025)
* Fixed a Tomcat crash issue when sending push notifications using HTTP2. (NEO-12701)

