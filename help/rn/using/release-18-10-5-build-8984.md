---
title: Release 18.10.5 - Build 8984
seo-title: Release 18.10.5 - Build 8984
description: Release 18.10.5 - Build 8984
seo-description: 
page-status-flag: never-activated
uuid: a9b93ed8-dab4-4e5a-81e1-b95082619ce9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
audience: rn
discoiquuid: db68717d-e9bd-4ff3-870f-a2c755f5fc54
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

