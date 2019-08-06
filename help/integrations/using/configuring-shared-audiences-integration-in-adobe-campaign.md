---
title: Configuring shared audiences integration in Adobe Campaign
seo-title: Configuring shared audiences integration in Adobe Campaign
description: Configuring shared audiences integration in Adobe Campaign
seo-description: 
page-status-flag: never-activated
uuid: d86bbaf0-9167-4a7f-885c-e7d6ad64d8af
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 694e85dc-0c61-40db-b0df-9a9f3bbea796
index: y
internal: n
snippet: y
---

# Configuring shared audiences integration in Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

Once you have submitted this request, Adobe will proceed to the provisioning of the integration for you and contact you to provide details and information that you have to finalize the configuration:

1. [Step 1: Configure or check the external accounts in Adobe Campaign](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Step 2: Configure the Data Source](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-2--configure-the-data-source)
1. [Step 3: Configure Campaign Tracking server](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-3--configure-campaign-tracking-server)
1. [Step 4: Configure the Visitor ID Service](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-4--configure-the-visitor-id-service)

## Step 1: Configure or check the external accounts in Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

First, we need to configure or check the external accounts in Adobe Campaign as follows:

1. Click the **Explorer** icon.
1. Go to **Administration > Platform > External accounts**. The mentioned SFTP accounts should have been configured by Adobe and the necessary information should have been communicated to you.

    * **importSharedAudience**: SFTP account dedicated to importing audiences.
    * **exportSharedAudience**: SFTP account dedicated to exporting audiences.

   ![](assets/aam_config_1.png)

1. Fill in the **Server** field: **ftp-out.demdex.com** domain for the import external account and **ftp-in.demdex.com** domain for the export external account.

   Remember that an export from Campaign is an import for Audience Manager or People core service.

   >[!NOTE]
   >
   >You can change the external account's **Type** from SFTP to S3 if needed.

   ![](assets/aam_config_2.png)

1. Add the **Account** and **Password** provided by Adobe.

Your external accounts are now configured.

## Step 2: Configure the Data Source {#step-2--configure-the-data-source}

The **Recipient - Visitor ID** is created inside Audience Manager. This is an out-of-the-box data source configured by default for Visitor ID. Segments created from Campaign will be part of this data source.

To configure the **Recipient - Visitor ID** data source:

1. From the **Explorer** node, select **Administration > Platform > AMC Data sources**.
1. Select **Recipient - Visitor ID**.
1. Enter the **Data Source ID** and **AAM Destination ID** provided by Adobe.

   ![](assets/aam_config_3.png)

## Step 3: Configure Campaign Tracking server {#step-3--configure-campaign-tracking-server}

For the configuration of the integration with People Core service or Audience manager, we also need to configure Campaign Tracking server.

You need to make sure the Campaign Tracking Server is registered on the domain (CNAME). You can find more information about domain name delegation in [this article](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html).

## Step 4: Configure the Visitor ID Service {#step-4--configure-the-visitor-id-service}

In the case that your Visitor ID service has never been configured on your web properties or websites, refer to the following [document](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-aam-analytics.html) to learn how to configure your service or the following .

Your configuration and provisioning are finalized, the integration can now be used to import and export audiences or segments.
