---
product: campaign
title: Migrate to the Adobe Analytics 2.0 API
description: Campaign Classic - Adobe Analytics 2.0 API migration guide
feature: Technote, Analytics Integration
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to v7 on-premise and hybrid deployments only"
hide: true
---
# Migrate to the Adobe Analytics 2.0 API {#analytics-2-migration}

Adobe Analytics 1.4 APIs are [reaching end-of-life](https://developer.adobe.com/analytics-apis/docs/1.4/guides/eol){target="_blank"}. The [Web Analytics connector](../../integrations/using/gs-aa.md) that links your Campaign instance to Adobe Analytics relies on these APIs, so you need to upgrade to a build that uses the new Analytics 2.0 APIs to keep the integration running.

>[!CAUTION]
>
>Upgrading re-imports the two built-in technical workflows that power the connector, [!UICONTROL webAnalyticsSendMetrics] and [!UICONTROL webAnalyticsGetWebEvents] (see the [Web Analytics workflows reference](../../workflow/using/web-analytics.md) for what each one does). Any customization you made on top of these workflows is overwritten by the re-import. If you built a custom implementation around them, plan to re-apply and re-test that customization after the upgrade — it will otherwise stop working.

## Are you impacted? {#are-you-impacted}

You are impacted if your instance uses the [!UICONTROL Web Analytics] external account for any of the following:

* Sending email campaign indicators and attributes to Adobe Analytics as metrics.
* Sending classification data to Adobe Analytics.
* The remarketing flow (identifying converted contacts after a campaign).
* A [!UICONTROL Web Analytics] external account you plan to configure for the first time.

Not sure which of these apply to you? Check which of the technical workflows above are active on your instance, and review your [!UICONTROL Web Analytics] external account configuration in [!UICONTROL Administration > Platform > External accounts] (see [Web Analytics external account](../../installation/using/external-accounts.md#web-analytics-external-account)).

## How to migrate {#how-to-migrate}

If you are on an **Adobe-hosted** instance, Adobe handles the SFTP provisioning, IP allow-listing, and key configuration for you as part of the upgrade — you only need to validate your use cases once the new build is live.

If you are on an **on-premise or hybrid** deployment, complete the following steps.

1. [Upgrade your Campaign environment](../../production/using/build-upgrade.md) to a build that includes the Adobe Analytics 2.0 changes. You can confirm which build you are running from [!UICONTROL Help > About...] (see [how to check your Campaign version](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)).
1. Review which of the use cases above apply to your instance, since the remaining steps depend on it.
1. If you only send metrics and classification data (no remarketing flow), ask [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"} to enable the `FEATUREFLAG_USE_ANALYTICS_20_API` flag on your instance. No further configuration is required on your side for this use case.
1. If you also use the remarketing flow, the [!UICONTROL webAnalyticsFindConverted] workflow needs a dedicated SFTP channel to exchange data with Adobe Analytics 2.0. Set this up as follows:
   1. Provision an SFTP server for the instance, following the same [SFTP server best practices](../../platform/using/sftp-server-usage.md) (key-based authentication, dedicated storage) you'd apply to any other external SFTP integration.
   1. Register that server's connection details in Adobe Analytics by running the script delivered with the new build:

      ```
      nlserver javascript -instance:<instance_name> -arg:host=<sftp_host_url>#user=<sftp_user> -file <path_to_the_file>/aaremarketingLocation.js
      ```

   1. Allow-list Adobe Analytics on your SFTP server, since remarketing exports are only ever initiated from a small, fixed set of Adobe IP ranges:
      * [Look up the current Adobe Analytics data collection IP addresses](https://experienceleague.adobe.com/en/docs/core-services/interface/data-collection/ip-addresses){target="_blank"} and add them to your SFTP server's allow list. FTP-based Analytics exports (including data feeds) only originate from IPv4 addresses in the London, Oregon, and Singapore regions.
      * [Retrieve the Adobe Analytics public key](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-18141){target="_blank"} and add it to your SFTP server so Analytics can authenticate.
1. Validate the migration by exercising each use case that applies to your instance (send a test campaign, check that indicators land in Analytics, and confirm remarketing data if applicable) before decommissioning any old connectivity.

## Setting up a new Web Analytics external account {#setting-up-a-new-web-analytics-external-account}

If you are configuring the [!UICONTROL Web Analytics] external account for the first time rather than migrating an existing one, follow the [external account setup steps](../../installation/using/external-accounts.md#web-analytics-external-account) and the [connector getting-started guide](../../integrations/using/gs-aa.md). Because Analytics 2.0 introduces new classification handling, you also need to create the matching [classification sets on the Analytics side](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/create-set){target="_blank"} before data will flow correctly between the two solutions.

## Need help? {#need-help}

If you run into issues during the migration, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.
