---
product: campaign
title: Create seed addresses
description: Learn how to create and use seed addresses
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
role: User, Developer
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
TQID: https://experienceleague.adobe.com/ya4m8nG7m3DUj-buOZMnd2Nzfx1J6lmIiOuo1VcHjwU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
---
# Create seed addresses{#creating-seed-addresses}

Seed addresses are not managed via standard profiles and targets, but in a dedicated node of the Adobe Campaign hierarchy **[!UICONTROL Resources > Campaign management > Seed addresses]**.

You can create sub-folders in order to organize the seed addresses. To do this, right-click the **[!UICONTROL Seed addresses]** node and select **[!UICONTROL Create a new 'Seed addresses' folder]**. Name the sub-folder and then press **[!UICONTROL Enter]** to validate. You can now create or copy seed addresses to this sub-folder. For more on this, refer to [Define addresses](#defining-addresses).

Adobe Campaign also lets you create seed address templates which are imported into deliveries or campaigns and adapted based on the specific needs of the concerned deliveries and campaigns. Refer to [Create seed address templates](#creating-seed-address-templates).

## Define addresses {#defining-addresses}

To create seed addresses, follow the steps below:

1. Click the **[!UICONTROL New]** button above the list of seed addresses.
1. Enter the data linked to the address in the matching fields from the **[!UICONTROL Recipient]** tab. The available fields correspond to the standard fields in the profiles of the delivery recipients (nms:recipient table): name, first name, email, etc.

   >[!NOTE]
   >
   >The label of the address is automatically filled in with the last name and first name you defined.
   >
   >You do not need to enter all fields of each tab when creating a seed address. Missing personalization elements are entered randomly during delivery analysis.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. In the **[!UICONTROL Address fields]** tab, enter the values that will be inserted in the delivery logs during the analysis phase (in the **[!UICONTROL nms:broadLog]** table).

1. In the **[!UICONTROL Additional data]** tab, enter the personalization data used for the deliveries created in the Data management workflows and which you want to assign a specific value to.

   >[!NOTE]
   >
   >Make sure that additional target data has been defined with an alias starting with '@' in the **[!UICONTROL Enrichment]** activity. Otherwise, you will not be able to use them properly with your seed addresses in your delivery activity.

## Creating seed address templates {#creating-seed-address-templates}

To create address templates which will be imported and may be modified for each delivery, the process is the same as when defining a new seed address. The only difference is that seed address templates addresses must be stored in a 'Template' type folder.

To define a template folder, apply the following process:

1. Create a new **[!UICONTROL Seed addresses]** type folder, right-click the folder then select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Click the **[!UICONTROL Restriction]** tab and add the following filtering condition: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Addresses stored in this folder may now be used as address templates. You can import them into deliveries or campaigns and adapt them based on the specific needs of the concerned deliveries and campaigns (see [Add seed addresses](adding-seed-addresses.md)).
