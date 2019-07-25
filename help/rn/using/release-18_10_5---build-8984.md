---
title: Release 18.10.5 - Build 8984
seo-title: Release 18.10.5 - Build 8984
description: Release 18.10.5 - Build 8984
seo-description: 
page-status-flag: never-activated
uuid: 61e71410-51e3-4055-af40-ef6c9fd041f1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
audience: rn
discoiquuid: d5dc9df3-21af-4c38-be70-253a0835dc0e
index: y
internal: n
snippet: y
---

# Release 18.10.5 - Build 8984{#release-build}

23 April 2019

## Improvements {#improvements}

* Fixed an issue with SQL deadlock which caused delivery analysis to fail in case of simultaneous analysis/sending (when two deliveries were analyzed at the same time). (NEO-13026)
* Removed the 10,000 record limit in Workflow Heatmap to fix a missing data issue. (NEO-12329)
* Fixed an issue when using the "Keep all additional data from the main set" option in an enrichment workflow activity. (NEO-13291)

