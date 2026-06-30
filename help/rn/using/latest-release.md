---
product: campaign
title: Latest Release
description: Latest Campaign Classic v7 Release Notes
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
TQID: https://experienceleague.adobe.com/Xq9y8r6xU-hypq1Eeo9ijaiGng7qqkWVqiCXW5fYx2c
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
feature_v2: []
subfeature_v2:
  - id: e5e477db-ebc7-4368-ab0f-4d8fc2aed405
    internal-label: Release notes
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Adobe Analytics integration
---
# Latest release {#latest-release}

This page lists new capabilities, improvements and fixes coming with the **latest Campaign Classic v7 Release**. Every new build comes with a status which is materialized by a color. Learn more about Campaign Classic v7 build statuses in [this page](rn-overview.md).

## Release 7.4.3 {#release-7-4-3}

### Build 9397 {#build-9397}

[!BADGE General Availability]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="General Availability"}

_June 30, 2026_

#### Security improvements {#security-7-4-3-9397}

This build includes security fixes. It is the recommended General Availability build and supersedes the previous Campaign Classic v7 builds.

#### Other changes {#changes-7-4-3-9397}

`webForm.jsp` now ignores client-supplied `ctx` parameters by default (controlled by the `disableCtxInWebForm` option, which defaults to `true`).

If your webForm requests currently pass a `ctx` parameter, you can temporarily re-enable this behavior by adding the following to the `<web>` element of your `config-<instance>.xml` file. Plan to phase out this usage over time.

```
<web>
  ...
  <jsp disableCtxInWebForm="false" />
  ...
</web>
```

### Build 9396 {#build-9396}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_June 9, 2026_

This build includes security fixes.

### Build 9394 {#build-9394}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

>[!CAUTION]
>
> Client Console upgrade is mandatory.

_Mar 31, 2026_

#### Security improvements {#security-7-4-3}

* To maintain optimal security, stability, and compliance, Debian has been upgraded to version 13 and PostgreSQL to version 17. Refer to the [compatibility matrix](compatibility-matrix.md).

#### Fixes {#fixes-7-4-3}

>[!NOTE]
>
> Fixes listed below have been progressively rolled out across successive 7.4.3 builds. Navigate to the **[!UICONTROL Help > About...]** [menu](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) to check that you have the latest 9394@28aaec9 build. Contact your Adobe representative for more information.

* Fixed an issue where the barcode component allowed an unbounded height parameter, which could lead to a security vulnerability. (NEO-89984)
* Fixed an issue where enumeration fields in lists created via workflows were missing temporary name attributes, causing incorrect or blank enum labels to be displayed in the interface. (NEO-91158)
* Fixed an issue where delivery preparation failed with personalization errors when using targetData fields in workflows with deduplication activities. (NEO-87693)
* Fixed an issue where concatenating single-character string fields with other strings failed in PostgreSQL 15 due to type casting requirements. (NEO-88028)
* Fixed an issue where tracking logs for collaborative campaigns in Distributed Marketing were not being written to the database due to a mismatch between parent and child delivery IDs. (NEO-86836)
* Fixed an issue where delivery logs showed messages as canceled even though they were successfully sent, particularly affecting deliveries with wave scheduling. (NEO-78933)
* Fixed an issue where the database cleanup workflow was not efficiently purging data, which could impact performance. (NEO-76439)

<!-- BUILD 7.0.9394.28aaec9 -->

* Fixed an issue where delivery statistics were not fully recomputed for some deliveries, particularly affecting the success indicators. (NEO-88106) <!-- moved from original 7.4.3 GA Fixes section -->
* Fixed an issue where the Client Console could crash when opening certain workflows referencing a missing upstream targeting schema. (NEO-28727)
* Fixed an issue where the Client Console version could not be identified after a failed startup, because the version file was missing from the install package. (NEO-94798)

<!--
other fixes - ommitted from release notes

Internal/non-customer-facing:

* Fixed an internal DevOps build race condition when copying the `teradata_timezones.txt` file during build packaging. (NEO-66532) — internal only; the Jira description states "No impact for customers: either it builds (99.9% of the time) or it does not."
* Fixed an internal CI/CD issue where AWS CodeBuild jobs could fail randomly on EC2 Docker containers when copying files during build. (NEO-90823) — internal CI/CD infrastructure only

Customer-specific hotfixes:

* Fixed an issue where coupon assignment could fail during delivery message preparation due to a SQL syntax error when looking up coupon codes. (NEO-92857) — Verizon only
* Fixed an issue where the error count and status in the `nms:address` table were not consistently updated on the marketing server after recurring soft bounces, causing recipients to not be quarantined as expected even though they were correctly flagged on the mid-sourcing server. (NEO-94422) — Walgreens only
-->

