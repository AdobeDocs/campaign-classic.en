---
product: campaign
title: Add seed addresses
description: Add seed addresses
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
role: User
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
TQID: https://experienceleague.adobe.com/pVYaTG48-HiK0RwJXgBbIMWa-o-R7jlEpauXNXvGi5E
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer (Campaign)
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages (Campaign)
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging (Campaign)
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design (Campaign)
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing (Campaign)
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability (Campaign)
---
# Add seed addresses{#adding-seed-addresses}

## Seed addresses in a delivery {#seed-addresses-in-a-delivery}

To add specific seed addresses for a delivery, click the **[!UICONTROL To]** link, then select the **[!UICONTROL Seed addresses]** tab.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

There are three possible insertion modes:

1. Entering single seed addresses.

   To do this, click the **[!UICONTROL Add]** button and define the content of the address fields. Repeat for each address.

1. Importing address templates and adapt them to suit your needs.

   To do this, click the **[!UICONTROL Import seed templates...]** link and select the folder which contains the address templates. For more on this, refer to [this section](creating-seed-addresses.md#creating-seed-address-templates).

   If necessary, once they are added, you can double-click them or click the **[!UICONTROL Detail...]** button to adapt the content of each address.

1. Creating a condition to dynamically select the control addresses to be inserted.

   To do this, click the **[!UICONTROL Edit the dynamic condition...]** link, then enter the seed address selection parameters. For instance, you could include all the seed addresses contained in a specific folder, or seed addresses belonging to a specific department from your organization.

   An example of this is presented in this section: [Use case: select seed addresses on criteria](use-case-selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>This option is used when the recipient table used is not the default **nms:recipient** table and you are using the Inbox Rendering functionality provided with Adobe Campaign's **[!UICONTROL Deliverability]** module.
>
>For more on this, refer to [Use an external recipient table](using-an-external-recipient-table.md) and the documentation on [Inbox rendering](inbox-rendering.md).

For deliveries, you can also customize the way addresses are inserted into the extraction file. By default, they are inserted in the sorting order of the output file, but you can choose to insert them at the end or the beginning of the file, or randomly among the recipients of the main target.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Seed addresses in a campaign {#seed-addresses-in-a-campaign}

To add seed addresses to a target for a campaign, select the operation and click the **[!UICONTROL Edit]** tab.

Click the **[!UICONTROL Advanced campaign settings...]** link and then the **[!UICONTROL Seed addresses]** tab, as shown below:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

The seed addresses inserted from the campaign will be added to the target of each delivery in the campaign.
