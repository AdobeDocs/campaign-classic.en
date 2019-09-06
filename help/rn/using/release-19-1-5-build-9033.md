---
title: Release 19.1.5 - Build 9033
seo-title: Release 19.1.5 - Build 9033
description: Release 19.1.5 - Build 9033
seo-description: 
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

# Release 19.1.5 - Build 9033{#release-build}

13 August 2019

## Improvements {#improvements}

* Fixed an issue with the SQL statement 'SELECT COUNT' which was executed on the default database rather than the FDA database during Data extraction in Data Management activity.(NEO-14551)
* To improve customer infrastructure capabilities, an SFTP proxy declaration is now available in the server configuration file.(NEO-12546)
* Fixed a Client console crash when "adding a linked table" in the Data Loading (RDBMS) workflow activity with no table name.(NEO-12213)
* Fixed an issue with the midEmetter package installation through command line. (NEO-12728)
* A new authentication option has been added to support OAuth credentials within the AC connector with Microsoft Dynamics.(NEO-11982)
* Fixing issue with UUID (Unique Universal Identifier) cause enrichment activity to fail withHive FDA.(NEO-12273)
