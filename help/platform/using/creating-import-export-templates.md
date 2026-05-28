---
product: campaign
title: Creating import and export templates
description: Learn how to create import and export templates in Campaign
feature: Templates
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1180e664-5ead-4d5d-b1c3-6fe397c1f3a2
TQID: https://experienceleague.adobe.com/KV2jYphvbknvGlfCH0k7QPdfPCAWgwg-X67ICvPmADo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences (Campaign)
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles (Campaign)
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences (Campaign)
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor (Campaign)
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management (Campaign)
---
# Create import and export templates {#creating-import-export-templates}

 

Import and export templates are stored in the **[!UICONTROL Resources > Templates > Job templates]** directory of the Adobe Campaign tree.

By default, three import templates and one export template are present in this directory. They must not be modified.

* The native template **[!UICONTROL Import denylist]** is already configured to import a list of email addresses which were added to the denylist.

* The **[!UICONTROL New text import]** and **[!UICONTROL New text export]** templates let you configure an import or export from scratch.

![](assets/s_ncs_user_export_wizard_template_create.png)

You can duplicate existing templates to create your own templates, or create a new template via the **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]** menu.

The process to configure a template is then the same than the one presented in these sections: 

* [Configure an import job](../../platform/using/executing-import-jobs.md)
* [Configure an export job](../../platform/using/executing-export-jobs.md)
