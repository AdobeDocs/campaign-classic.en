---
solution: Campaign Classic
product: campaign
title: Configuring population samples
description: Learn how to perform A/B testing through a dedicated use case.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
---
# Configuring population samples {#step-2--configuring-population-samples}

## Configuring the Query activity {#configuring-the-query-activity}

* Double-click the **[!UICONTROL Query]** activity.

  ![](assets/use_case_abtesting_createrecipients_001.png)

* Click the **[!UICONTROL Edit query]** link and select the recipients you want to target.

  ![](assets/use_case_abtesting_createrecipients_002.png)

* Link the **[!UICONTROL Query]** activity to the **[!UICONTROL Split]** activity.

  ![](assets/use_case_abtesting_createrecipients_003.png)

## Configuring the Split activity {#configuring-the-split-activity}

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

You can now create the two delivery templates (see [Step 3: Create two delivery templates](../../delivery/using/a-b-testing-uc-delivery-templates.md)).
