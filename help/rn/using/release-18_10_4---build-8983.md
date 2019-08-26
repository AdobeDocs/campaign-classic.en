---
title: Release 18.10.4 - Build 8983
seo-title: Release 18.10.4 - Build 8983
description: Release 18.10.4 - Build 8983
seo-description: 
page-status-flag: never-activated
uuid: 3470725b-3efc-4644-8c55-58edab7341f6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 84f4094f-730d-4c03-96a0-b4fd0ee1f2ec
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

