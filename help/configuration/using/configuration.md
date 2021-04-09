---
solution: Campaign Classic
product: campaign
title: Configuration
description: Configuration
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
---
# Configure Campaign Explorer navigation tree{#configuration}

As an expert user, you can add folders in the explorer tree and customize it. 

Learn more about Campaign explorer and navigation hierarchy [in this section](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

The types of folders used by the navigation list are described in an XML document that obeys the grammar of the **xtk:navtree** schema.

The XML document is structured as follows:

```
<navtree name="name" namespace="name_space">
  <!-- Global commands -->
  <commands>
      ...
  </commands>
  
  <!-- Structured space for adding a folder -->
  <model name="<name>" label="<Label>">
    <!-- Folder type -->
    <nodeModel>
      ...
    </nodeModel>
<model name="<name>" label="<Sub model>">
      ...
    </model>
  </model> 
</navtree>
```

The XML document contains the **`<navtree>`** root element with the **name** and **namespace** attributes to specify the document name and namespace. The name and namespace make up the document identification key.

The global commands of the application are declared in the document from the **`<commands>`** element.

The declaration of file types is structured in the document with the following elements: **`<model>`** and **`<nodemodel>`**.

## Global commands {#global-commands}

A global command lets you launch an action. This action can be an input form or a SOAP call.

Global commands are accessible from the main **[!UICONTROL Tools]** menu.

The command configuration structure is as follows:

```
<commands>
  <!-- Description of a command -->
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
  <!-- Separator -->
  <command label="-" name="<name>"/>
  <!-- Command structure -->
  <command name="<name>" label="<Label>">
    <command...
  </command>
</commands>
```

The description of a global command is entered in the **`<command>`** element with the following properties:

* **name**: internal name of the command: the name must be entered and unique
* **label**: label of the command.
* **desc**: description visible from the status bar of the main screen.
* **form**: form to be launched: the value to be entered is the identification key of the input form (e.g. "cus:recipient")
* **rights**: list of named rights (separated by a comma) allowing access to this command. The list of available rights is accessible from the **[!UICONTROL Administration > Access management > Named rights]** folder.
* **promptLabel**: displays a confirmation box before execution of the command.

A **`<command>`** element can contain **`<command>`** sub-elements. In this case, the parent element lets you display a sub-menu made up of these child elements.

The commands are displayed in the same order as they are declared in the XML document.

A command separator lets you display a separation bar between commands. It is identified by the **'-'** value contained in the command label.

The optional presence of the **`<soapcall>`** tag with its input parameters defines the call of a SOAP method to be executed. For further information on the SOAP API, refer to [Campaign JSAPI documentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

The form context can be updated on initialization from the **`<enter>`** tag. For further information on this tag, refer to the documentation on input forms.

**Example**:

* Declaration of a global command to launch the "xtk:import" form:

  ```
  <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  A keyboard shortcut is declared on the 'I' character by the presence of **&** in the command label.

* Example of a sub-menu with a separator:

  ![](assets/d_ncs_integration_navigation_exemple1.png)

  ```
  <command label="Administration" name="admin">
    <command name="cmd1" label="Example 1" form="cus:example1"/>
    <command name="sep" label="-"/>
    <command name="cmd1" label="Example 2" form="cus:example2">
      <enter>
        <set xpath="@type" expr="1"/>
      </enter>
    </command>
  </command>
  ```

* Execution of a SOAP method:

  ```
  <command name="cmd3" label="Example 3" promptLabel="Do you really want to execute the command?">
    <soapCall name="Execute" service="xtk:sql"/>
  </command>
  ```

## Folder type {#folder-type}

A folder type lets you give access to the data of a schema. The view associated with the folder consists of a list and an input form.

The folder type configuration structure is as follows:

```
<!-- Structured location to add the folder -->
<model name="name" label="Labelled">
  <!-- Type of folder -->
  <nodeModel name="<name>" label="<Labelled>" img="<image>">
    <view name="<name>" schema="<schema>" type="<listdet|list|form|editForm>">
      <columns>
        <node xpath="<field1>"/>
        ...
    </columns>
    </view> 
  </nodeModel>
  <model name="<name>" label="<Sous modèle>">
    ...
  </model>
</model>
```

The folder type declaration must be entered under a **`<model>`** element. This element lets you define a hierarchical organization visible from the **[!UICONTROL Add new folder]** menu. A **`<model>`** element must contain **`<nodemodel>`** elements and other **`<model>`** elements.

The **name** and **label** attributes populate the internal name of the element and the label displayed in the **[!UICONTROL Add new folder]** menu.

The **`<nodemodel>`** element contains the description of the folder type with the following properties:

* **name**: internal name
* **label**: label used in the **[!UICONTROL Add new folder]** menu and as a default label when inserting a folder.
* **img**: default image on folder insertion.
* **hiddenCommands**: list of commands (separated by a comma) to be masked. Possible values: "adbnew", "adbsave", "adbcancel" and "adbdup".
* **newFolderShortCuts**: list of shortcuts on models (**`<nodemodel>`** separated by a comma) in folder creation. 
* **insertRight**, **editRight**, **deleteRight**: rights for inserting, editing and deleting folders.

The **`<view>`** element under the **`<nodemodel>`** element contains the configuration of the list associated with the view. The schema of the list is entered in the **schema** attribute of the **`<view>`** element.

To edit the records of the list, the input form with the same name as the list schema is implicitly used. The **type** attribute on the **`<view>`** element affects the display of the form. Possible values are:

* **listdet**: displays the form at the bottom of the list.
* **list**: displays the list alone. The form is launched by double-clicking or via the "Open" in the menu on selecting the list.
* **form**: displays a read-only form.
* **editForm**: displays a form in edit mode.

>[!NOTE]
>
>The name of the input form can be overloaded by entering the **form** attribute in the **`<view>`** element.

The default configuration of the list columns is entered via the **`<columns>`** element. A column is declared on a **`<node>`** element containing the **xpath** attribute with the field to be referenced in its schema as its value.

**Example**: declaration of a folder type on the "nms:recipient" schema.

```
<model label="Profiles and targets" name="nmsProfiles">
  <nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
             img="nms:folder.png" insertRight="folderInsert" label="Recipients"
             name="nmsFolder">
    <view name="listdet" schema="nms:recipient" type="listdet">
      <columns>
        <node xpath="@firstName"/>
        <node xpath="@lastName"/>
        <node xpath="@email"/>
        <node xpath="@account"/>
      </columns>
    </view>
  </nodeModel>
  <nodeModel name="nmsGroup" label="Groups"...
</model>
```

The corresponding folder insertion menu:

![](assets/d_ncs_integration_navigation_exemple2.png)

Filtering and sorting can be applied when the list is being loaded:

```
<view name="listdet" schema="nms:recipient" type="listdet">
  <columns>
    ...
  </columns>

  <orderBy>
    <node expr="@lastName" desc="true"/>
</orderBy>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
</view>  
```

### Shortcut commands {#shortcut-commands}

A shortcut command lets you launch an action on selecting the list. The action can be an input form or a SOAP call.

Commands are accessible from the **[!UICONTROL Action]** menu of the list or the associated menu button.

The command configuration structure is as follows:

```
<nodeModel...
  ...
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
</nodeModel>
```

The description of a command is entered on the **`<command>`** element with the following properties:

* **name**: internal name of the command: the name must be entered and unique.
* **label**: label of the command.
* **desc**: description visible from the status bar of the main screen.
* **form**: form to be launched: the value to be entered is the identification key of the input form (e.g. "cus:recipient").
* **rights**: list of named rights (separated by a comma) allowing access to this command. The list of available rights is accessible from the **[!UICONTROL Administration > Access management > Named rights]** folder.
* **promptLabel**: displays a confirmation box before execution of the command
* **monoSelection**: forces mono-selection (multiple selection by default).
* **refreshView**: forces reloading of the list after execution of the command.
* **enabledIf**: activates the command depending on the expression entered.
* **img**: enters an image allowing access to the command from the list toolbar.

A **`<command>`** element can contain **`<command>`** sub-elements. In this case, the parent element lets you display a sub-menu made up of these child elements.

The commands are displayed in the same order as they are declared in the XML document.

A command separator lets you display a separation bar between commands. It is identified by the **'-'** value contained in the command label.

The optional presence of the **`<soapcall>`** tag with its input parameters defines the call of a SOAP method to be executed. For further information about SOAP APIs, refer to [Campaign JSAPI documentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

The form context can be updated on initialization via the **`<enter>`** tag. For further information about this tag, refer to the input form documentation.

**Example**:

```
<command desc="Cancel execution of the job" enabledIf="EV(@status, 'running')"
         img="nms:difstop.bmp" label="Cancel..." name="cancelJob" 
         promptLabel="Do you really want to cancel this job?" refreshView="true">
  <soapCall name="Cancel" service="xtk:jobInterface"/>
</command>
<command label="-" name="sep1"/>
<command desc="Execute selected template" form="cus:form" lmonoSelection="true" name="executeModel"
         rights="import,export,aggregate">
  <enter>
    <set expr="0" xpath="@status"/>
  </enter>
</command>

```

### Linked folder {#linked-folder}

There are two types of folder management operations:

1. The folder is a view: the list displays all records associated with the schema, with the possibility of system filtering entered in the folder properties.
1. The folder is linked: the records in the list are implicitly filtered on the folder link.

For a linked folder, the **folderLink** attribute on the **`<nodemodel>`** element must be populated. This attribute contains the name of the link on the folder configured in the data schema.

Example of declaration of a linked folder in the data schema:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

The configuration of the **`<nodemodel>`** on the link of the folder named "folder" is as follows:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
