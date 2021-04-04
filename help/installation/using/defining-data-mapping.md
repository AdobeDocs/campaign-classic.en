---
solution: Campaign Classic
product: campaign
title: Accessing an external database
description: Accessing an external database
audience: platform
content-type: reference
topic-tags: connectors
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
---
# Defining data mapping {#defining-data-mapping}

Adobe Campaign lets you define mapping on the data in an external table.

To do this, once the schema of the external table has been created, you need to create a new delivery mapping to use the data in this table as a delivery target.

To do this, apply the following steps:

1. Create a new delivery mapping and choose the targeting dimension, the schema you just created, for example.

   ![](assets/wf_new_mapping_create_fda.png)

1. Indicate the fields where the delivery information is stored (last name, first name, email, address, etc.).

   ![](assets/wf_new_mapping_define_join.png)

1. Specify the parameters for information storage, including the suffix of the extension schemas in order for them to be easily identifiable.

   ![](assets/wf_new_mapping_define_names.png)

   You can choose whether to store exclusions (**excludelog**), with messages (**broadlog**) or in a separate table.

   You can also choose whether to manage tracking for this delivery mapping (**trackinglog**).

1. Then select the extensions to be taken into account. The extension type depends on your platform's parameters and options (view your license contract).

   ![](assets/wf_new_mapping_define_extensions.png)

   Click the **[!UICONTROL Save]** button to launch delivery mapping creation: all linked tables are created automatically based on the selected parameters.
