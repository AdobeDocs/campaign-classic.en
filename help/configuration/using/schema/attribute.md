---
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
---
# attribute element {#attribute--element}

![](../../assets/v7-only.svg)

## Content model {#content-model}

attribute:==help

## Attributes {#attributes}

_operation (string), advanced (boolean), applicableIf (string), autoIncrement (boolean), belongsTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), edit (string), enum (string), expr (string), feature (string), featureDate (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqltable (string), target (MNTOKEN), template (string), translatedDefault (string), translatedExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

## Parents {#parents}

`<element>`

## Children {#children}

`<help>`

## Description {#description}

`<attribute>` elements let you define a field in the database.

## Use and context of use {#use-and-context-of-use}

`<attribute>` elements must be declared in an `<element>` element.

The sequence in which `<attribute>` elements are defined in an `<srcschema>` does not affect the field creation sequence in the database. The creation sequence will be alphabetical.

## Attribute description {#attribute-description}

* **_operation (string)**: defines the type of writing in the database.

  This attribute is mainly used when extending out-of-the-box schemas.

  Accessible values are:

  * "none": reconciliation alone. This means that Adobe Campaign will recover the element without updating it or generating an error if it doesn't exist.
  * "insertOrUpdate": update with insertion. This means that Adobe Campaign will update the element or create it if it doesn't exist.
  * "insert": insertion. This means that Adobe Campaign will insert the element without checking whether it exists.
  * "update": update. This means that Adobe Campaign will update the element or generate an error if it doesn't exist.
  * "delete": deletion. This means that Adobe Campaign will recover and delete elements.

* **advanced (boolean)**: when this option is activated (@advanced="true"), it lets you hide the attribute on the list of available fields accessible for configuring a list in a form.
* **applicableIf (string)**: this attribute lets you make fields optional. The `<attribute>` element will be taken into account when updating the database when the constraint is complied with. "applicableIf" receives an XTK expression.
* **autoIncrement (boolean)**: if this option is activated, the field becomes a counter. This enables you to increment a value (mostly IDs). (external use)
* **belongsTo (string)**: takes the name and namespace of the table that shares the field, and populates the schema where the attribute is declared. (used only in a `<schema>`).
* **dataPolicy (string)**: enables you to specify approval constraints on values allowed in the SQL or XML field. The values for this attribute are:

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
* **default (string)**: lets you define the value of the default field (call to a function, default value). This attribute receives an XTK expression. 
* **desc (string)**: lets you insert a description of the attribute. This description is displayed in the status bar of the interface.
* **edit (string)**: this attribute specifies the type of input which will be used in the form linked to the schema.
* **enum (string)**: receives the name of the enumeration linked to the field. The enumeration can be inserted into the same schema or into a remote schema.
* **expr (string)**: defines a field precalculation expression. This attribute receives an Xpath or an XTK expression.
* **feature (string)**: defines a characteristics field: These fields are used for extending the data in an existing table, but with storage in an annex table. Accepted values are:

    * "shared": the content is stored in a shared table per data type
    * "dedicated": the content is stored in a dedicated table

  SQL characteristics tables are built automatically based on the characteristic type:

    * dedicated: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
    * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  There are two types of characteristics fields: simple oà¹ fields where a single value is authorized on the characteristic, and oà¹ multiple choice fields, where the characteristic is linked to a collection element which may contain several values.

  When a characteristic is defined in a schema, this schema must have a main key based on a single field (composite keys are not authorized).

* **featureDate (boolean)**: attribute linked to the "@feature" characteristics field. If its value is "true", it lets you find out when the value was last updated.
* **img (string)**: lets you define a path for an image linked to a field (namespace + image name)(example: img="cus:mypicture.jpg"). Physically, the image must be imported to the application server.
* **label (string)**: label linked to the field, mostly destined to the user in the interface. It lets you avoid naming constraints.
* **length (string)**: max. number of characters for a value of the "string" type SQL field. If the "@length" attribute isn't specified, Adobe Campaign automatically creates a field for 255 characters.
* **localizable (boolean)**: if it is activated, this attribute tells the collection tool to recover the value of the "@label" attribute for translation (internal use).
* **name (MNTOKEN)**: name of the attribute that will match the name of the field in the table. The value of the "@name" attribute must be short, preferably in english, and comply with XML naming constraints.

  When the schema is written to the database, prefixes are automatically added to the field name by Adobe Campaign:

  * "i": prefix for the 'integer' type.
  * "d": prefix for the 'double' type.
  * "s": prefix for the character string type.
  * "ts": prefix for the 'date' type.

  To fully define the name of the field in the table, use the "@sqlname" option when defining an attribute.

* **notNull (boolean)**: lets you redefine Adobe Campaign's behavior regarding the management of NULL records in the database. By default, numeric fields are not null and string and date type fields can be null. 
* **pkgStatus (string)**: during package exports, values are taken into account depending on the value of the "@pkgStatus":

  * "always": always present
  * "never": never present
  * "default (or nothing)": the value is exported except if it's the default value or if it isn't an internal field which would not be compatible with other instances.

* **ref (string)**: this attribute defines a reference to an `<attribute>` element shared by several schemas (definition factoring). The definition isn't copied into the current schema.
* **required (boolean)**: if this attribute is activated (@required="true"), the field is highlighted in the interface. The label of the field will be red in forms.
* **sql (boolean)**: if this attribute is activated (@sql="true"), it forces storage of the SQL attribute, even when the element which contains the attribute has the xml="true" property.
* **sqlDefault (string)**: this attribute enables you to define the default value taken into account for updating the database if the @notNull attribute is activated. If this attribute is added after the attribute creation, the schema behaviour will not change even for the new records. To change the schema and update the value for new records, you need to delete and create again the attribute.
* **sqlname (string)**: of the field during table creation. If @sqlname isn't specified, the value of the "@name" attribute is used by default. When the schema is written in the database, prefixes are added automatically depending on the type of field.
* **template (string)**: this attribute defines a reference to an `<attribute>` element shared by several schemas. The definition is automatically copied into the current schema.
* **translatedDefault (string)**: if a "@default" attribute is found, the "@translatedDefault" will enable you to redefine an expression to match the one defined in @default, to be collected by the translation tool (internal use).
* **translatedExpr (string)**: if an "@expr" attribute is present, the "@translatedExpr" attibute enables you to redefine an expression to match the one defined in @expr, to be collected by the translation tool (internal use).
* **type (MNTOKEN)**: field type.

  Field types are generic. Depending on the type of database installed, Adobe Campaign changes the defined type into a value specific to the database installed during structure update.

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

  If the "@type" attribute is left empty, Adobe Campaign will link a string of characters (STRING) with a length of 100 to the field by default.

  If the field is of STRING type and the name of the field isn't specified by the presence of the "@sqlname" attribute, the name of the field in the database will automatically be preceded by an 's'. This operating mode will be similar with INTEGER (i), DOUBLE (d) and DATES (ts) type fields.

* **userEnum (string)**: receives the internal name of an "open" enumeration. The values of the enumeration can be defined by the user in the interface. 
* **visibleIf (string)**: defines a condition in the form of an XTK expression to show or hide the attribute.

  >[!IMPORTANT]
  >
  >The attribute is hidden but its data can still be accessed.

* **xml (boolean)**: if this option is activated, the values of the field don't have a linked SQL field. Adobe Campaign creates a Text type "mData" field for record storage. This means there is not filtering or sorting on these fields.

### Examples {#examples}

Example of enumeration values whose values are stored in the database:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

Declaration of an XML field with "@datapolicy":

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

Example with an "@applicableIf": the "contains" attribute will only be created if the number of countries is greater than 20.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Example with "@feature" of "shared" type:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Example with "@feature" of "dedicated" type:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
