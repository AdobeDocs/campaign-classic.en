---
title: Release 19.1.3 - Build 9031
seo-title: Release 19.1.3 - Build 9031
description: Release 19.1.3 - Build 9031
seo-description: 
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
---

# Release 19.1.3 - Build 9031{#release-build}

26 July 2019

## Improvements {#improvements}

* Fixed a regression caused by the NEO-12727 which could lead to workflows being stopped when a Test activity was executed twice. (NEO-16835) 
* Fixed an issue which led to an erroneous HTTP code being returned (HTTP 200 OK instead of HTTP 403 Forbidden) when an invalid or expired session token was used in API calls. (NEO-16826) 
* Fixed an issue with the DKIM key which was not embedded into emails anymore, thus causing deliverability issues. (NEO-16804) 
* Fixed various issues with workflow scheduling. Workflows were scheduled to be executed once a day without taking into account the scheduler configuration. (NEO-16619, NEO-16426)
