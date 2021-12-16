---
product: campaign
title: Edit forms
description: Edit forms
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
---

# Edit forms{#editing-forms}

![](../../assets/common.svg)

## Overview

Marketers and operators use input forms to create, modify, and preview records. Forms show a visual representation of information.

You can create and modify input forms:

* You can modify the factory input forms that are delivered by default. The factory input forms are based on the factory data schemas.
* You can create custom input forms, based on data schemas that you define.

Forms are entities of `xtk:form` type. You can view the input form structure in the `xtk:form` schema. To view this schema, choose **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** from the menu. Read more about [form structure](form-structure.md).

To access input forms, choose **[!UICONTROL Administration] > [!UICONTROL Configuration] > [!UICONTROL Input forms]** from the menu:

![](assets/d_ncs_integration_form_arbo.png)

To design forms, edit the XML content in the XML editor:

![](assets/d_ncs_integration_form_edit.png)

[Read more](form-structure.md#formatting).

To preview a form, click the **[!UICONTROL Preview]** tab:

![](assets/d_ncs_integration_form_preview.png)

## Form types

You can create different types of input forms. The form type determines how users navigate the form:

* Console screen 

  This is the default form type. The form comprises a single page.

  ![](assets/console_screen_form.png)

* Content Management

  Use this form type for content management. See this [use case](../../delivery/using/use-case--creating-content-management.md).

  ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Wizard

  This form comprises multiple floating screens that are ordered in a specific sequences. Users navigate from one screen to the next. [Read more](form-structure.md#wizards).

* Iconbox

  This form comprises multiple pages. To navigate the form, users select icons at the left of the form.

  ![](assets/iconbox_form_preview.png)

* Notebook

  This form comprises multiple pages. To navigate the form, users select tabs at the top of the form.

  ![](assets/notebook_form_preview.png)

* Vertical pane

  This form shows a navigation tree.

* Horizontal pane

  This form shows a list of items.

