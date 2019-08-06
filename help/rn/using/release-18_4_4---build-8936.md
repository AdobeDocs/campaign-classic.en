---
title: Release 18.4.4 - Build 8936
seo-title: Release 18.4.4 - Build 8936
description: Release 18.4.4 - Build 8936
seo-description: 
page-status-flag: never-activated
uuid: e40007e8-5664-467a-aece-22e0b2bed8d8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
audience: rn
discoiquuid: 01cfabd9-0074-4907-badb-e968b5065428
index: y
internal: n
snippet: y
---

# Release 18.4.4 - Build 8936{#release-build}

1 August 2018

## Improvements {#improvements}

* Email archiving logs have been enhanced, which makes it easier and clearer to check which emails have been successfully delivered or have failed through BCC archiving. (NEO-10675)
* Fixed an issue which led to the display of load balancer IPs instead of customer IPs in the tracking broadlogs. (NEO-11295)
* Fixed an error with LATIN1 encoding when using an FDA Connection to a PostgreSQL database. (NEO-11299)
* Fixed an issue that occured when using the **Prepare the personalization data with a workflow** delivery option. (NEO-11047, NEO-11301)
* Fixed a random issue causing the properties of a delivery to be wrongly overwritten. (NEO-11015)
* Fixed an issue when using calculated fields in a **Survey answers** workflow activity. (NEO-11382)
* Fixed an issue when using data stored in XML in a **Survey answers** workflow activity. (NEO-10816)
* Fixed an issue when performing the server upgrade with build 8935.
* Fixed an issue which displayed useless errors in the postupgrade log when a **Survey answers** workflow activity was not fully configured.
* FDA Teradata: fixed an issue with auto-incremented fields and indexes in SQL tables.

