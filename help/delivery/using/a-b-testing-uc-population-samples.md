---
product: campaign
title: Configure population samples
description: Learn how to perform A/B testing through a dedicated use case
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
TQID: https://experienceleague.adobe.com/HWbHtS5F-je1GiNdr25dD17W-MpJ-K3xp-T8kKC-c10
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
subfeature_v2:
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: e739ee2b-6228-412e-878f-45de0791417d
    internal-label: Use cases
---
# AB testing: Configure population samples {#step-2--configuring-population-samples}

## Configure the Query activity {#configuring-the-query-activity}

* Double-click the **[!UICONTROL Query]** activity.

  ![](assets/use_case_abtesting_createrecipients_001.png)

* Click the **[!UICONTROL Edit query]** link and select the recipients you want to target.

  ![](assets/use_case_abtesting_createrecipients_002.png)

* Link the **[!UICONTROL Query]** activity to the **[!UICONTROL Split]** activity.

  ![](assets/use_case_abtesting_createrecipients_003.png)

## Configure the Split activity {#configuring-the-split-activity}

This activity lets you create several populations: the one that receives delivery A, the one that receives delivery B, and the remaining population. Using random selection lets you target just part of the population of each delivery.

1. Creating population A:

    * Double-click the **[!UICONTROL Split]** activity.
    
      ![](assets/use_case_abtesting_createrecipients_004.png)

    * In the existing tab, change the label to population A.
    
      ![](assets/use_case_abtesting_createrecipients_005.png)

    * Select the **[!UICONTROL Limit the selected records]** option.
    
      ![](assets/use_case_abtesting_createrecipients_006.png)

    * Click the **[!UICONTROL Edit]** link, select **[!UICONTROL Activate random sampling]**, and click **[!UICONTROL Next]**.
    
      ![](assets/use_case_abtesting_createrecipients_007.png)

    * Set the threshold to 10%, then click **[!UICONTROL Finish]**.
    
      ![](assets/use_case_abtesting_createrecipients_008.png)

1. Creating population B:

    * Click **[!UICONTROL Add]** to create a new tab for population B.
    
      ![](assets/use_case_abtesting_createrecipients_009.png)

    * Limit the population to 10% as previously.
    
      ![](assets/use_case_abtesting_createrecipients_010.png)

1. Creating the remaining population:

    * Go to the **[!UICONTROL General]** tab.
    
      ![](assets/use_case_abtesting_createrecipients_011.png)

    * Select **[!UICONTROL Generate complement]**.
    
      ![](assets/use_case_abtesting_createrecipients_012.png)

    * Change the label to specify that this population includes neither A nor B, and click **[!UICONTROL OK]** to close the activity.
    
      ![](assets/use_case_abtesting_createrecipients_013.png)

You can now create the two delivery templates. [Learn more](a-b-testing-uc-delivery-templates.md)).
