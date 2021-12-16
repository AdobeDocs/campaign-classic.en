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

## Containers

In forms, you can use containers for various purposes:

* Organize content within forms
* Define access to input fields
* Nest forms within other forms

[Read more](form-structure.md#containers).

### Organize content

Use containers to organize content within forms:

* You can group fields into sections.
* You can add pages to multipage forms.

To insert a container, use the `<container>` element. [Read more](form-structure.md#containers).

#### Group fields

Use containers to group input fields into organized sections.

To insert a section into a form, use this element: `<container type="frame">`. Optionally, to add a section title, use the `label` attribute.

Syntax: `<container type="frame" label="`*section_title*`"> […] </container>`

  In this example, a container defines the **Creation** section, which comprises the **[!UICONTROL Created by]** and **[!UICONTROL Name]** input fields:

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Add pages to multipage forms

For multipage forms, use a container to create a form page.

This example shows containers for the **General** and **Details** pages of a form:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Define access to fields

Use containers to define what is visible and to define access to fields. You can turn on or off groups of fields.

### Nest forms

Use containers to nest forms within other forms. [Read more](#add-pages-to-multipage-forms).

## References to images

To find images, choose **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** from the menu.

To associate an image with an element in the form, for example, an icon, you can add a reference to an image. Use the `img` attribute, for example, in the `<container>` element.

Syntax: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

This example shows references to the `book.png` and `detail.png` images from the `ncm` namespace:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

These images are used for icons that users click to navigate a multipage form:

![](assets/nested_forms_preview.png)
