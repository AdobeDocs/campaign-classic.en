---
title: Adding seed addresses
seo-title: Adding seed addresses
description: Adding seed addresses
seo-description: 
page-status-flag: never-activated
uuid: 32f85f48-d131-4502-a36a-6777b1560013
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 034e518a-f06a-4f35-8382-2ab031447473
index: y
internal: n
snippet: y
---

# Adding seed addresses{#adding-seed-addresses}

## Seed addresses in a delivery {#seed-addresses-in-a-delivery}

To add specific seed addresses for a delivery, click the **To** link, then select the **Seed addresses** tab.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

There are three possible insertion modes:

1. Entering single seed addresses.

   To do this, click the **Add** button and define the content of the address fields. Repeat for each address. For more on this, refer to [this section](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address).

1. Importing address templates and adapt them to suit your needs.

   To do this, click the **Import seed templates...** link and select the folder which contains the address templates. For more on this, refer to [Creating seed address templates](../../delivery/using/adding-seed-addresses.md#creating-seed-address-templates).

   If necessary, once they are added, you can doucle-click them or click the **Detail...** button to adapt the content of each address.

1. Creating a condition to dynamically select the control addresses to be inserted.

   To do this, click the **Edit the dynamic condition...** link, then enter the seed address selection parameters. For instance, you could include all the seed addresses contained in a specific folder, or seed addresses belonging to a specific department from your organization.

   An example of this is presented in this section: [Use case: selecting seed addresses on criteria](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>This option is used when the recipient table used is not the default **nms:recipient** table and you are using the Inbox Rendering functionality provided with Adobe Campaign's **Deliverability** module.   
>For more on this, refer to [Using an external recipient table](../../delivery/using/using-an-external-recipient-table.md) and the documentation on [Inbox rendering](../../delivery/using/inbox-rendering.md).

For deliveries, you can also customize the way addresses are inserted into the extraction file. By default, they are inserted in the sorting order of the output file, but you can choose to insert them at the end or the beginning of the file, or randomly among the recipients of the main target.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Seed addresses in a campaign {#seed-addresses-in-a-campaign}

To add seed addresses to a target for a campaign, select the operation and click the **Edit** tab.

Click the **Advanced campaign settings...** link and then the **Seed addresses** tab, as shown below:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

The seed addresses inserted from the campaign will be added to the target of each delivery in the campaign.
