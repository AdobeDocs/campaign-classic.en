---
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
---
# element element {#element--element}

## Content model {#content-model-4}

element:==(attribute | compute-string | dbindex | default | element | help | join | key | sysFilter | translatedDefault)

## Attributes {#attributes-4}

_operation (string), advanced (boolean), aggregate (string), applicableIf (string), autopk (boolean), belongsTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAsField (boolean), doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (string), folderModel (string), folderProcess (string), fullLoad (boolean), hierarchical (boolean), hierarchicalPath (string), img (string), inout (string), integrity (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDbIndex (boolean), noKey (boolean), ordered (boolean), overflowtable (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean), revIntegrity (string), revLabel (string), revLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), target (MNTOKEN), template (string), temporaryTable (boolean), translatedDefault (string), translatedExpr (string), type (MNTOKEN), unbound (boolean), user (boolean), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolean)

## Parents {#parents-4}

`<srcschema>`

`<element>`

## Children {#children-4}

* `<attribute>`
* `<compute-string>`
* `<dbindex>`
* `<default>`
* `<element>`
* `<help>`
* `<join>`
* `<key>`
* `<sysfilter>`
* `<translateddefault>`

## Description {#description-4}

There are four types of `<element>`  elements in Adobe Campaign:

* Root `<element>`  : defines the name of the SQL table that matches the schema.
* Structure `<element>`  : defines a group of  `<element>`   or   `<attribute>`    elements.
* Link `<element>`  : defines a link. This elements must include the "@type=link" attribute.
* XML `<element>`  : defines a Text type "mData" field. This element must include the "@type=xml" attribute.

## Attribute description {#attribute-description-4}

* **_operation (string)**: defines the type of writing in the database.

  This attribute is mainly used when extending out-of-the-box schemas.

  Accessible values are:

  * "none": reconciliation alone. This means that Adobe Campaign will recover the element without updating it or generating an error if it doesn't exist.
  * "insertOrUpdate": update with insertion. This means that Adobe Campaign will update the element or create it if it doesn't exist.
  * "insert": insertion. This means that Adobe Campaign will insert the element without checking whether it exists.
  * "update": update. This means that Adobe Campaign will update the element or generate an error if it doesn't exist.
  * "delete": deletion. This means that Adobe Campaign will recover and delete elements.

* **advanced (boolean)**: when this option is activated (@advanced="true"), it lets you hide the attribute on the list of available fields accessible for configuring a list in a form.
* **aggregate (string)**: lets you copy the definition of an `<element>`  via another schema. This attribute receives a schema declaration in the form of a "namespace:name".
* **applicableIf (string)**: condition for applying the index. This attribute receives an XTK expression.
* **autopk (boolean)**: if this option is activated (autopk="true"), a unique key will be automatically defined. This option may only be used on the main element of the schema. Warning, Adobe Campaign only guarantees that the key generated is unique. It is not guaranteed that the key values are consecutive and incremental.
* **dataPolicy (string)**: enables you to specify approval constraints on values allowed in the SQL field. The values for this attribute are:

  * "none": no value
  * "smartCase": first letters upper case
  * "lowerCase": all lower case 
  * "upperCase": all upper case
  * "email": email adress
  * "phone": telephone number
  * "identifier": identifier name
  * "resIdentifier": file name

* **dbEnum (string)**: receives the internal name of a "closed" enumeration. The enumeration values must be defined in the `<srcschema>`.
* **defOnDuplicate (boolean)**: if this attribute is activated, when a record is duplicated the default value (defined in @default) is automatically reapplied to the record.
* **default (string)**: lets you define element behavior (call to a function, default value). This attribute receives an XTK expression.
* **desc (string)**: lets you insert a description of the element. This description is displayed in the status bar of the interface.
* **displayAsField (boolean)**: if this attribute is activated, a "link" type `<element>`  will be displayed as a field in the tree view of the schemas ("Structure" tab). This way, it's possible to display a link as a local field and change it behavior during a query. When the element is found in the SELECT of a query, the value of the link target will be used. When the element is found in the WHERE of a query, the underlying key of the link will be used. 
* **edit (string)**: this attribute specifies the type of input that will be used in the form linked to the schema.
* **enum (string)**: receives the name of the enumeration linked to the field. The enumeration can be inserted into the same schema or into a remote schema. 
* **expr (string)**: this attribute defines a calculated field for which no definition is stored in the table. It receives an Xpath or an XTK (string) expression.
* **externalJoin (boolean)**: external join in a "link" type element.
* **feature (string)**: defines a characteristics field: These fields are used for extending the data in an existing table, but with storage in an annex table. Accepted values are:

  * "shared": the content is stored in a shared table per data type
  * "dedicated": the content is stored in a dedicated table

  SQL characteristics tables are built automatically based on the characteristic type:

  * dedicated: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
  * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  There are two types of characteristics fields: simple fields where a single value is authorized on the characteristic, and multiple choice fields, where the characteristic is linked to a collection element which may contain several values.

  When a characteristic is defined in a schema, this schema must have a main key based on a single field (composite keys are not authorized).

* **featureDate (boolean)**: attribute linked to the "@feature" characteristics field. If its value is "true", it lets you find out when the value was last updated.
* **filterPath (string)**: this attribute receives an Xpath and lets you define a filter on a field.
* **folderLink (string)**: this attribute receives the name of the link that lets you recover the files containing entities. 
* **folderModel (string)**: defines the type of folder which enables entity storage. This attribute is only defined if "@folderLink" is present.
* **folderProcess (string)**: defines the link where entity model instances are stored. This attribute is only defined if "@folderLink" is present.
* **fullLoad (boolean)**: this attribute forces the display of all records in a table during field selection in a form. 
* **img (string)**: receives the path of an image linked to an element. The value of this attribute is of "namespace:image name" type. For example: img="cus:myImage.jpg". Physically, the image must be imported to the application server. 
* **integrity (string)**: referential integrity of the occurrence of the source table towards the target table.

  Accessible values are:

  * "define": Adobe Campaign does not delete the entity if it is referenced via the link
  * "normal": deleting the source occurrence initializes the keys of the link on the target occurrence (default mode), this type of integrity initializes all foreign keys
  * "own": deleting the source occurrence triggers the deletion of the target occurrence
  * "owncopy": similar to "own" (in case of deletion) or duplicates occurrences (in case of duplication)
  * "neutral": does not do anything

* **label (string)**: element label. 
* **labelSingular (string)**: label (singular form) of the element used in some parts of the interface. 
* **length (string)**: max. number of characters authorized for a value of the "string" type SQL field.
* **localizable (boolean)**: if it is activated, this attribute tells the collection tool to recover the value of the "@label" attribute for translation (internal use).
* **name (MNTOKEN)**: internal name of the element which matches the name of the table. The value of the "@name" attribute must be short, preferably in English, and comply with naming constraints linked to XML.

  When the schema is written to the database, prefixes are automatically added to the field name by Adobe Campaign.

  * "i": prefix for the 'integer' type.
  * "d": prefix for the 'double' type.
  * "s": prefix for the character string type.
  * "ts": prefix for the 'date' type.

  To define the name of the table in an autonomous way, you need to use the "@sqltable" attribute in the definition of the main schema element.

* **noDbIndex (boolean)**: lets you specify that the element will not be indexed.
* **ordered (boolean)**: if the attribute is activated (ordered="true"), Adobe Campaign keeps the element declaration sequence in an XML collection element.
* **pkSequence (string)**: receives the name of the sequence to be used for calculating an auto-incremental key. This attribute may only be used if an auto-incremental key is defined on the root element of the schema. 
* **pkgStatus (string)**: during package exports, values will be taken into account as a function of the value of this attribute:

  * "always": the element will always be present
  * "never": the element will never be present
  * "default (or nothing)": the element is exported unless it is the default element or if it isn't an internal field and would not be compatible with other instances

* **ref (string)**: this attribute defines a reference to an >element> element shared by several schemas (definition factoring). The definition isn't copied into the current schema.
* **required (boolean)**: if this attribute is activated (@required="true"), the field is highlighted in the interface. The label of the field will be red in forms. 
* **revAdvanced (boolean)**: when activated, this attribute specifies that the opposite link is an "advanced" link. 
* **revCardinality (string)**: this attribute defines the cardinality of a link between two tables. It is used in a "link" type `<element>`.

  Possible values are:

  * "single" : Simple 1-1 type link
  * "unbound": 1-N type collection link

  By default, if the attribute isn't specified during link creation, cardinality will be 1-N.

* **revDesc (string)**: this attribute receives a description linked to the opposite link.
* **revExternalJoin (boolean)**: when activated, this attribute lets you force the external join on the opposite link. 
* **revIntegrity (string)**: this attribute defines the integrity on the target schema. The same values as the "@integrity" attribute are authorized. By default, Adobe Campaign gives the "normal" value to this attribute. 
* **revLabel (string)**: label of the opposite link.
* **revLink (string)**: name of the opposite link. If the value is "_NONE_", no opposite link will be created in the destination schema.
* **revTarget (string)**: target of the opposite link.
* **sql (boolean)**: if this attribute is activated (@sql="true"), it forces storage of the SQL element, even if the element has the xml="true" property.
* **sqlname (string)**: name of the field during table creation. If "@sqlname" isn't specified, the value of the "@name" attribute is used by default. When writing the schema to the table, prefixes are added automatically depending on the type of field. 
* **sqltable (string)**: for the main element of the schema, this attribute overloads the name of the SQL table generated by default. If "@sqltable" isn't specified, the default name will be structured like this: namespace (first letter upper case) followed by the value of the SrcSchema "@name".
* **tableSpace (string)**: this attribute lets you specify a new data storing tablespace for a table (valid on the root `<element>`).
* **tableSpaceIndex (string)**: this attribute lets you specify a new index storage tablespace for a table (valid on the root `<element>`).
* **target (MNTOKEN)**: receives the name of the target schema when creating a link between tables. This attribute is only active for "link" type elements. 
* **template (string)**: this attribute defines a reference to an `<element>` element shared by several schemas. The definition is automatically copied into the current schema.
* **translatedDefault (string)**: if a "@default" attribute is found, the "@translatedDefault" will enable you to redefine an expression to match the one defined in @default, to be collected by the translation tool (internal use).
* **translatedExpr (string)**: if a "@expr" attribute is found, the "@translatedExpr" attribute lets you redefine an expression matching the one defined in "@expr", and which will be collected by the translation tool (internal use). 
* **type (MNTOKEN)**: defines the type of data stored in the element.

  List of available types:

    * ANY
    * bin
    * blob
    * boolean
    * byte
    * CDATA
    * datetime
    * datetimetz
    * datetimenotz
    * date
    * double
    * enum
    * float
    * html
    * int64
    * link
    * long
    * memo
    * MNTOKEN
    * percent
    * primarykey
    * short
    * string
    * time
    * timespan
    * uuid

* **unbound (boolean)**: if the attribute is activated (unbound="true"), the link is declared as a collection element for a 1-N cardinality. 
* **userEnum (string)**: receives the internal name of an "open" enumeration. Enumeration values can be defined by the user in the interface.
* **xml (boolean)**: if this option is activated, all values defined in the element are stored in XML in a TEXT type "mData" field. This means that there will be no filtering or sorting on these fields. 
* **xmlChildren (boolean)**: forces storage for each child ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
