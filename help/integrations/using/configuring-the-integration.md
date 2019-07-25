---
title: Configuring the integration
seo-title: Configuring the integration
description: Configuring the integration
seo-description: 
page-status-flag: never-activated
uuid: b4f78b14-b5c3-483f-bd73-582874c4b7d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
topic-tags: adobe-experience-manager
content-type: reference
discoiquuid: 280df4dd-d90e-4cd9-bedd-6f49d10b6781
index: y
internal: n
snippet: y
---

# Configuring the integration{#configuring-the-integration}

## Configuring in Adobe Campaign {#configuring-in-adobe-campaign}

To use these two solutions together, you must configure them to connect to one another.

Follow the steps below to start the configuration in Adobe Campaign:

1. [Install the AEM integration package in Adobe Campaign](../../integrations/using/configuring-the-integration.md#install-the-aem-integration-package-in-adobe-campaign)
1. [Configure the external account](../../integrations/using/configuring-the-integration.md#configure-the-external-account)
1. [Configure AEM resources filtering](../../integrations/using/configuring-the-integration.md#configure-aem-resources-filtering)

For advanced configurations such as managing personalization fields and blocks. Refer to Adobe Experience Manager [documentation](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html).

### Install the AEM integration package in Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

You first need to install the **AEM integration** package.

1. From your Adobe Campaign instance, select **Tools** from the upper toolbar.
1. Select **Tools > Advanced > Import package...**.

   ![](assets/aem_config_1.png)

1. Select **Install a standard package**.
1. Check **AEM integration** then click the **Next** button.

   ![](assets/aem_config_2.png)

1. In the next window, click the **Start** button to start the installation of your package. Close the window once the installation is finished.

### Configure the security zone for AEM operator {#configure-the-security-zone-for-aem-operator}

The **AEM integration** package sets the **aemserver** operator in Campaign. This operator will be used to connect the Adobe Experience Manager server to Adobe Campaign.

You need to configure a security zone for this operator to connect to Adobe Campaign via Adobe Experience Manager.

>[!CAUTION]
>
>We strongly recommend creating a security zone dedicated to AEM to avoid any security problems. For more on this, refer to the Installation [guide](../../installation/using/configuring-campaign-server.md#defining-security-zones).

If your Campaign instance is hosted by Adobe, contact Adobe Support team. If you are using Campaign on-premise, follow the steps below:

1. Open the **serverConf.xml** configuration file.
1. Access the **allowUserPassword** attribute of the selected security zone and set it to **true**.

   This will allow Adobe Experience Manager to connect Adobe Campaign via login/password.

### Configure the external account {#configure-the-external-account}

The **AEM integration** package created the external account for Adobe Experience Cloud. You need now to configure it to connect with your Adobe Experience Manager instance.

To confugure the AEM external account, follow the steps below:

1. Click the **Explorer** button.

   ![](assets/aem_config_3.png)

1. Select **Administration > Platform > External accounts**.
1. From the **External account** list, select **AEM instance**.
1. Enter the parameters for your AEM authoring instance:

    * **Server**
    * **Account**
    * **Password**

   >[!NOTE]
   >
   >Make sure that your **Server** address does not end with a a trailing slash.

   ![](assets/aem_config_4.png)

1. Check the **Enabled** box.
1. Click the **Save** button.

### Configure AEM resources filtering {#configure-aem-resources-filtering}

The **AEMResourceTypeFilter **option is used to filter types of Experience Manager resources that can be used in Adobe Campaign. This allows Adobe Campaign to retrieve Experience Manager contents that are specifically designed to be used in Adobe Campaign only.

To check if the **AEMResourceTypeFilter** option is configured:

1. Click the **Explorer** button.
1. Select **Administration > Platform > Options**.
1. From the **Options** list, select **AEMResourceTypeFilter**.
1. In the **Value (text)** field, the path should be as follows:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   Or in some case:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Configuring in Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Follow the steps below to start the configuration in Adobe Experience Manager:

1. Configure the **replication** to replicate from the AEM authoring instance to the AEM publishing instance.

   To learn how to configure replication, refer to Adobe Experience Manager [documentation](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/replication.html).

1. Install the integration **FeaturePack** on your authoring instance then replicate the installation on your publishing instance. (For AEM versions 5.6.1 and 6.0 only).

   To learn how to install FeaturePack, refer to Adobe Experience Manager [documentation](https://helpx.adobe.com/experience-manager/aem-previous-versions.html).

1. Connect Adobe Experience Manager to Adobe Campaign by configuring a dedicated **Cloud Service**.

   To learn how to connect both solutions via Cloud Services, refer to Adobe Experience Manager .

1. Configure the **Externalizer service**.

   To learn how to configure it, refer to Adobe Experience Manager [documentation](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/externalizer.html).

