---
product: campaign
title: Edit forms
description: Edit forms
feature: Configuration
role: Data Engineer, Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
---

# Edit forms{#editing-forms}

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

  Use this form type for content management. See this [use case](../../delivery/using/use-case-creating-content-management.md).

  ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistant

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


## Create a simple form {#create-simple-form}

To create a form, follow these steps:

1. From the menu, choose **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
1. Click the **[!UICONTROL New]** button at the top right of the list.

    ![](assets/input-form-create-1.png)

1. Specify the form properties:

   * Specify the form name and the namespace.
      
      The form name and the namespace can match the related data schema.  This example shows a form for the `cus:order` data schema:

      ```xml
      <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
        […]
      </form>
      ```

     Alternatively, you can explicitly specify the data schema in the `entity-schema` attribute.
    
     ```xml
     <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
       […]
     </form>
     ```

   * Specify the label to be displayed on the form.
   * Optionally, specify the form type. If you do not specify a form type, the console screen type is used by default.

      ![](assets/input-form-create-2.png)

       If you are designing a multipage form, you can omit the form type in the `<form>` element and specify the type in a container.

1. Click **[!UICONTROL Save]**.

1. Insert the form elements.
   
   For example, to insert an input field, use the `<input>` element. Set the `xpath` attribute to the field reference as an XPath expression. [Read more](schema-structure.md#referencing-with-xpath).

   This example shows input fields based on the `nms:recipient` schema.

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. If the form is based on a specific schema type, you can look up the fields for this schema:

   1. Click **[!UICONTROL Insert]** > **[!UICONTROL Document fields]**.

      ![](assets/input-form-create-4.png)

   1. Select the field and click **[!UICONTROL OK]**.
    
      ![](assets/input-form-create-5.png)

1. Optionally, specify the field editor.

   A default field editor is associated with each data type:
   * For a date-type field, the form shows an input calendar.
   * For an enumeration-type field, the form shows a selection list.

   You can use these field editor types:
  
   | Field editor | Form attribute |
   | --- | --- |
   | Radio button | `type="radiobutton"` |
   | Checkbox | `type="checkbox"` |
   | Edit tree | `type="tree"` |

    Read more about [memory list controls](form-structure.md#memory-list-controls).

1. Optionally, define access to the fields:

   | Element | Attribute | Description |
   | --- | --- | --- |
   | `<input>` | `read-only="true"` | Provides read-only access to a field |
   | `<container>` | `type="visibleGroup" visibleIf="`*edit-expr*`"` | Conditionally displays a group of fields |
   | `<container>` | `type="enabledGroup" enabledIf="`*edit-expr*`"` | Conditionally enables a group of fields |

   Example:
   
   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. Optionally, use containers to group fields into sections.

   ```xml
   <container type="frame" label="Name">
      <input xpath="@firstName"/>
      <input xpath="@lastName"/>
   </container>
   <container type="frame" label="Contact details">
      <input xpath="@email"/>
      <input xpath="@phone"/>
   </container>
   ```

   ![](assets/input-form-create-3.png)

## Create a multipage form {#create-multipage-form}

You can create multipage forms. You can also nest forms within other forms.

### Create an `iconbox` form

Use the `iconbox` form type to show icons at the left of the form, which take users to different pages in the form.

![](assets/iconbox_form_preview.png)

To change the type of an existing form to `iconbox`, follow these steps:

1. Change the `type` attribute of the `<form>` element to `iconbox`: 
   
   ```xml
   <form […] type="iconbox">
   ```

1. Set a container for each form page:

   1. Add a `<container>` element as a child of the `<form>` element.
   1. To define a label and an image for the icon, use the `label` and `img` attributes.

      ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="iconbox" xtkschema="xtk:form">
          <container img="xtk:properties.png" label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container img="nms:msgfolder.png" label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container img="nms:supplier.png" label="Services">
              […]
          </container>
      </form>
      ```

     Alternatively, remove the `type="frame"` attribute from the existing `<container>` elements.

### Create a notebook form

Use the `notebook` form type to show tabs at the top of the form, which take users to different pages.

![](assets/notebook_form_preview.png)

To change the type of an existing form to `notebook`, follow these steps:

1. Change the `type` attribute of the `<form>` element to `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. Add a container for each form page:

    1. Add a `<container>` element as a child of the `<form>` element.
    1. To define the label and the image for the icon, use the `label` and `img` attributes.

    ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="notebook" xtkschema="xtk:form">
          <container label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container label="Services">
              […]
          </container>
      </form>
    ```

   Alternatively, remove the `type="frame"` attribute from the existing `<container>` elements.

### Nest forms

You can nest forms within other forms. For example, you can nest notebook forms within iconbox forms.

The level of nesting controls navigation. Users can drill down to subforms. 

To nest a form within another form, insert a `<container>` element and set the `type` attribute to the form type. For the top-level form, you can set the form type in an outer container or in the `<form>` element.

### Example

This example shows a complex form:

* The top-level form is an iconbox form. This form comprises two containers labelled **General** and **Details**.

  As a result, the outer form shows the **General** and **Details** pages at the top level. To access these pages, users click the icons at the left of the form.

* The subform is an notebook form that is nested within the **General** container. The subform comprises two containers that are labelled **Name** and **Contact**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

  As a result, the **General** page of the outer form shows the **Name** and **Contact** tabs.

![](assets/nested_forms_preview.png)

To nest a form within another form, insert a `<container>` element and set the `type` attribute to the form type. For the top-level form, you can set the form type in an outer container or in the `<form>` element.

### Example

This example shows a complex form:

* The top-level form is an iconbox form. This form comprises two containers labelled **General** and **Details**.

  As a result, the outer form shows the **General** and **Details** pages at the top level. To access these pages, users click the icons at the left of the form.

* The subform is an notebook form that is nested within the **General** container. The subform comprises two containers that are labelled **Name** and **Contact**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

  As a result, the **General** page of the outer form shows the **Name** and **Contact** tabs.

![](assets/nested_forms_preview.png)



## Modify a factory input form {#modify-factory-form}

To modify a factory form, follow these steps:

1. Modify the factory input form:

   1. From the menu, choose **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
   1. Select an input form and modify it.

    You can extend factory data schemas, but you cannot extend factory input forms. We recommend that you modify factory input forms directly without recreating them. During software upgrades, your modifications in the factory input forms are merged with the upgrades. If the automatic merge fails, you can resolve the conflicts. [Read more](../../production/using/upgrading.md#resolving-conflicts).

    For example, if you extend a factory schema with an additional field, you can add this field to the related factory form.

## Validate forms {#validate-forms}

You can include validation controls in forms.

### Grant read-only access to fields

To grant read-only access to a field, use the `readOnly="true"` attribute. For example, you might want to show the primary key of a record, but with read-only access. [Read more](form-structure.md#non-editable-fields).

In this example, the primary key (`iRecipientId`) of the `nms:recipient` schema is displayed in read-only access:

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### Check mandatory fields 

You can check mandatory information:

* Use the `required="true"` attribute for the required fields.
* Use the `<leave>` node to check these fields and show error messages.

In this example, the email address is required, and an error message is displayed if the user has not provided this information:

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

Read more about [expression fields](form-structure.md#expression-field) and [form context](form-structure.md#context-of-forms).

### Validate values

You can use JavaScript SOAP calls to validate form data from the Console. Use these calls for complex validation, for example, to check a value against a list of authorized values. [Read more](form-structure.md#soap-methods).

1. Create a validation function in a JS file.

   Example:

    ```js
    function nms_recipient_checkValue(value)
    {
      logInfo("checking value " + value)
      if (…)
      {
        logError("Value " + value + " is not valid")
      }
      return 1
    }
    ```

    In this example, the function is named `checkValue`. This function is used to check the `recipient` data type in the `nms` namespace. The value that is being checked is logged. If the value is not valid, then an error message is logged. If the value is valid, then the value 1 is returned.

    You can use the returned value to modify the form.

1. In the form, add the `<soapCall>` element to the `<leave>` element.

    In this example, a SOAP call is used to validate the `@valueToCheck` string:

    ```xml
    <form name="recipient" (…)>
    (…)
      <leave>
        <soapCall name="checkValue" service="nms:recipient">
          <param exprIn="@valueToCheck" type="string"/>
        </soapCall>
      </leave>
    </form>
    ```

   In this example, the `checkValue` method and the `nms:recipient` service are used:

   * The service is the namespace and the data type.
   * The method is the function name. The name is case-sensitive.
      
    The call is performed synchronously.

    All exceptions are displayed. If you use the `<leave>` element, then users cannot save the form until the entered information is validated.

This example shows how you can make service calls from within forms:

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

In this example, the input is an ID, which is a primary key. When users fill the form for this ID, a SOAP call is made with this ID as the input parameter. The output is a boolean that is written to this field: `/tmp/@count`. You can use this boolean inside the form. Read more about [form context](form-structure.md#context-of-forms).
