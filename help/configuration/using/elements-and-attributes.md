---
title: Elements and attributes
seo-title: Elements and attributes
description: Elements and attributes
seo-description: 
page-status-flag: never-activated
uuid: 72b0128a-a453-4646-93e5-b399914abb76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5e24d94a-f9c1-4642-a881-dfc4b5492f14
index: y
internal: n
snippet: y
---

# Elements and attributes{#elements-and-attributes}

When editing a schema, an approval system based on the source schema (xtk:srcSchema) is available. Some errors can also be spotted when updating the database using the "Database structure update..." wizard.

By default, in Adobe Campaign schemas, all boolean type attributes are "false". To activate them, you need to specify the attribute in the schema and set its value to "true".

## <attribute> element </attribute> {#attribute--element}

### Content model {#content-model}

attribute:==help

### Attributes {#attributes}

_operation (string), advanced (boolean), applicableIf (string), autoIncrement (boolean), belongsTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), edit (string), enum (string), expr (string), feature (string), featureDate (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqltable (string), target (MNTOKEN), template (string), translatedDefault (string), translatedExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

### Parents {#parents}

`<element>`

### Children {#children}

`<help>`

### Description {#description}

`<attribute>` elements let you define a field in the database.

### Use and context of use {#use-and-context-of-use}

`<attribute>` elements must be declared in an `<element>` element.

The sequence in which `<attribute>` elements are defined in an `<srcschema> ` does not affect the field creation sequence in the database. The creation sequence will be alphabetical.

### Attribute description {#attribute-description}

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

    * dedicated: Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]
    * shared: Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]

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
* **sqlDefault (string)**: this attribute enables you to define the default value taken into account for updating the database if the @notNull attribute is activated.
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

  >[!CAUTION]
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


## <compute-string> element </compute-string> {#compute-string--element}

### Content model {#content-model-1}

compute-string:==EMPTY

### Attributes {#attributes-1}

@expr

### Parents {#parents-1}

`<element>`

### Children {#children-1}

None

### Description {#description-1}

The `<compute-string>` element enables you to generate a string based on an XTK expression to display a "built" label in the interface based on several values.

### Use and context of use {#use-and-context-of-use-1}

When no `<compute-string>` is defined, a `<compute-string>` element is entered by default with the values of the primary key in the schema.

### Attribute description {#attribute-description-1}

* **expr (string)**: XTK and/or Xpath expression

### Examples {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Result of the string calculated on a recipient: "John Doe (john.doe@aol.com)":

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## <condition> element </condition> {#condition--element}

### Content model {#content-model-2}

condition:==EMPTY

### Attributes {#attributes-2}

* @boolOperator (string)
* @enabledIf (string)
* @expr (string)

### Parents {#parents-2}

`<sysfilter>`

### Children {#children-2}

None

### Description {#description-2}

This element lets you define a filtering condition.

### Use and context of use {#use-and-context-of-use-2}

One `<sysfiler>`  element can contain several filtering conditions.

### Attribute description {#attribute-description-2}

* **boolOperator (string)**: if several `<conditions>` are defined within the same  `<sysfilter>` element, this attribute lets you combine them. By default, the logical link is between `<condition>` elements is "AND". The "@boolOperator" attribute lets you combine "OR" and "AND" type links.
* **enabledIf (string)**: condition activation test.
* **expr (string)**: an XTK expression.

### Examples {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

## <dbindex> element </dbindex> {#dbindex--element}

### Content model {#content-model-3}

dbindex:==keyfield

### Attributes {#attributes-3}

* @_operation (string)
* @applicableIf (string)
* @label (string)
* @name (MNTOKEN)
* @unique (boolean)

### Parents {#parents-3}

`<element>`

### Children {#children-3}

`<keyfield>`

### Description {#description-3}

This element lets you define an index linked to a table.

### Use and context of use {#use-and-context-of-use-3}

It's possible to define several indexes. One index can reference one or more fields of the table. Index declaration usually follows the definition of the main schema element.

The order of the `<keyfield>` elements defined in a `<dbindex>` is very important. The first `<keyfield>` must be the indexation criterion which the queries are mainly based on.

The name of the index in the database is calculated by concatenating the name of the table and the name of the index. For example: Table name "Sample", Namespace "Cus", index name "MyIndex"-> name of the index field during index creation querying: "CusSample_myIndex".

### Attribute description {#attribute-description-3}

* **_operation (string)**: defines the type of writing in the database.

  This attribute is mainly used when extending out-of-the-box schemas.

  Accessible values are:

    * "none": reconciliation alone. This means that Adobe Campaign will recover the element without updating it or generating an error if it doesn't exist.
    * "insertOrUpdate": update with insertion. This means that Adobe Campaign will update the element or create it if it doesn't exist.
    * "insert": insertion. This means that Adobe Campaign will insert the element without checking whether it exists.
    * "update": update. This means that Adobe Campaign will update the element or generate an error if it doesn't exist.
    * "delete": deletion. This means that Adobe Campaign will recover and delete elements.

* **applicableIf (string)**: condition for taking the index into account - receives an XTK expression.
* **label (string)**: index label.
* **name (MNTOKEN)**: unique index name.
* **unique (boolean)**: if this option is activated (@unique="true"), the attribute guarantees the uniqueness of the index throughout its fields.

### Examples {#examples-3}

Creation of an index on the "id" field. (the "@unique" attribute on the `<dbindex>` element triggers adding of the "UNIQUE" SQL key word when the index is created in the database (query)).

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

Creation of a composite index on the "@mail" and "@phoneNumber" fields:

```    
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```

<!--
## <element> element </element> {#element--element}

### Content model {#content-model-4}

element:==(attribute | compute-string | dbindex | default | element | help | join | key | sysFilter | translatedDefault)

### Attributes {#attributes-4}

_operation (string), advanced (boolean), aggregate (string), applicableIf (string), autopk (boolean), belongsTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAsField (boolean), doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (string), folderModel (string), folderProcess (string), fullLoad (boolean), hierarchical (boolean), hierarchicalPath (string), img (string), inout (string), integrity (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDbIndex (boolean), noKey (boolean), ordered (boolean), overflowtable (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean), revIntegrity (string), revLabel (string), revLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), target (MNTOKEN), template (string), temporaryTable (boolean), translatedDefault (string), translatedExpr (string), type (MNTOKEN), unbound (boolean), user (boolean), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolean)

### Parents {#parents-4}

`<srcschema>`

`<element>`

### Children {#children-4}

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

### Description {#description-4}

There are four types of `<element>  elements in Adobe Campaign: </element>`

* Root `<element>  : defines the name of the SQL table that matches the schema. </element>`
* Structure `<element>  : defines a group of  <element>   or   <attribute>    elements.   </attribute>  </element> </element>`
* Link `<element>  : defines a link. This elements must include the "@type=link" attribute. </element>`
* XML `<element>  : defines a Text type "mData" field. This element must include the "@type=xml" attribute. </element>`

### Attribute description {#attribute-description-4}

* **_operation (string)**: defines the type of writing in the database.

  This attribute is mainly used when extending out-of-the-box schemas.

  Accessible values are:

    * "none": reconciliation alone. This means that Adobe Campaign will recover the element without updating it or generating an error if it doesn't exist.
    * "insertOrUpdate": update with insertion. This means that Adobe Campaign will update the element or create it if it doesn't exist.
    * "insert": insertion. This means that Adobe Campaign will insert the element without checking whether it exists.
    * "update": update. This means that Adobe Campaign will update the element or generate an error if it doesn't exist.
    * "delete": deletion. This means that Adobe Campaign will recover and delete elements.

* **advanced (boolean)**: when this option is activated (@advanced="true"), it lets you hide the attribute on the list of available fields accessible for configuring a list in a form.
* **aggregate (string)**: lets you copy the definition of an `<element>  via another schema. This attribute receives a schema declaration in the form of a "namespace:name". </element>`
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

* **dbEnum (string)**: receives the internal name of a "closed" enumeration. The enumeration values must be defined in the `<srcschema>  . </srcschema>`
* **defOnDuplicate (boolean)**: if this attribute is activated, when a record is duplicated the default value (defined in @default) is automatically reapplied to the record.
* **default (string)**: lets you define element behavior (call to a function, default value). This attribute receives an XTK expression.
* **desc (string)**: lets you insert a description of the element. This description is displayed in the status bar of the interface.
* **displayAsField (boolean)**: if this attribute is activated, a "link" type `<element>  will be displayed as a field in the tree view of the schemas ("Structure" tab). This way, it's possible to display a link as a local field and change it behavior during a query. When the element is found in the SELECT of a query, the value of the link target will be used. When the element is found in the WHERE of a query, the underlying key of the link will be used. </element>`
* **edit (string)**: this attribute specifies the type of input that will be used in the form linked to the schema.
* **enum (string)**: receives the name of the enumeration linked to the field. The enumeration can be inserted into the same schema or into a remote schema. 
* **expr (string)**: this attribute defines a calculated field for which no definition is stored in the table. It receives an Xpath or an XTK (string) expression.
* **externalJoin (boolean)**: external join in a "link" type element.
* **feature (string)**: defines a characteristics field: These fields are used for extending the data in an existing table, but with storage in an annex table. Accepted values are:

    * "shared": the content is stored in a shared table per data type
    * "dedicated": the content is stored in a dedicated table

  SQL characteristics tables are built automatically based on the characteristic type:

    * dedicated: Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]
    * shared: Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]

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
* **revCardinality (string)**: this attribute defines the cardinality of a link between two tables. It is used in a "link" type `<element>  . </element>`

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
* **tableSpace (string)**: this attribute lets you specify a new data storing tablespace for a table (valid on the root `<element>  ). </element>`
* **tableSpaceIndex (string)**: this attribute lets you specify a new index storage tablespace for a table (valid on the root `<element>  ). </element>`
* **target (MNTOKEN)**: receives the name of the target schema when creating a link between tables. This attribute is only active for "link" type elements. 
* **template (string)**: this attribute defines a reference to an `<element automatically="" by="" copied="" current="" definition="" element="" into="" is="" p="" schema.="" schemas.="" several="" shared="" the=""> </element>`
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

## <enumeration> element </enumeration> {#enumeration--element}

### Content model {#content-model-5}

enumeration:==(help| value)

### Attributes {#attributes-5}

* @basetype (string)
* @default (string)
* @desc (string)
* @label (string)
* @name (string)
* @template (string)

### Parents {#parents-5}

`<srcschema>`

### Children {#children-5}

* `<help>`
* `<value>`

### Description {#description-5}

This element enables us to define a value enumeration. An enumeration belongs to the schema which it is defined in, but it is accessible via another schema.

### Use and context of use {#use-and-context-of-use-4}

Enumerations are defined at the start of a schema (before the main element is defined).

### Attribute description {#attribute-description-5}

* **basetype (string)**: type of the values stored in the enumeration.

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
    * DOMDocument
    * DOMElement
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

* **default (string)**: Default value. The default value may also be one of the values defined in the enumeration. 
* **desc (string)**: enumeration description. 
* **label (string)**: enumeration label.
* **name (string)**: internal name of the enumeration. 
* **template (string)**: this attribute defines a reference to an `<enumeration>  element shared by several schemas. The definition is automatically copied into the current schema. </enumeration>`

### Examples {#examples-4}

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

Definition of an enumeration with a default value:

```

 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

## <help> element </help> {#help--element}

### Content model {#content-model-6}

help:==EMPTY

### Attributes {#attributes-6}

None

### Parents {#parents-6}

`<srcschema>  ,  <element>   ,   <attribute>    ,    <enumeration>     ,     <value>      ,      <param />,      <method />     </value>    </enumeration>   </attribute>  </element> </srcschema>`

### Children {#children-6}

None

### Description {#description-6}

This element lets you describe an `<element>  or  <attribute>   element. It may only contain text, and is stored in XML in the database.  </attribute> </element>`

### Attribute description {#attribute-description-6}

This element has no attributes.

### Examples {#examples-5}

`<method name="CheckOperation" static="true">  <helpchecks a="" help="" method="" of="" p="" the="" validity="">  </helpchecks> </method>`

## <join> element </join> {#join--element}

### Content model {#content-model-7}

join:==EMPTY

### Attributes {#attributes-7}

* @dstFilterExpr (string)
* @xpath-dst (string)
* @xpath-src (string)

### Parents {#parents-7}

`<element>`

### Children {#children-7}

None

### Description {#description-7}

Lets you define the fields that create a join between SQL tables.

### Use and context of use {#use-and-context-of-use-5}

A `<join>  element can only be used if the parent  <element>   element is of 'link' type. This means that the parent element must have the "@type=link" attribute declared.  </element> </join>`

It is not necessary to specify the name and namespace of the remote table in the `<join>  element. They need to be specified in the parent  <element>   .  </element> </join>`

By convention, links are defined at the end of the schema.

If the `<join>  element isn't specified when the link type element is defined, the link will automatically be placed on the primary keys of both tables. </join>`

### Attribute description {#attribute-description-7}

* **dstFilterExpr (string)**: this attribute lets you restrict the number of eligible values in the remote table.
* **xpath-dst (string)**: this attribute receives an Xpath (@name attribute of the remote table).
* **xpath-src (string)**: this attribute receives an Xpath (@name attribute in the current schema).

### Examples {#examples-6}

Link between the 'email' field of the current table and the "@compagny-id" field of the remote table:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Filtered link towards the "cus:Country" table based on the content of the "@country" field which must contain the 'EN' value:

`<element label="MyLink" name="StockEN" target="cus:Stock" type="link">  <join dstFilterExpr="@country = 'EN'" xpath-dst="@country" xpath-src="@code" /> </element>`

## <key> element </key> {#key--element}

### Content model {#content-model-8}

key:==keyfield

### Attributes {#attributes-8}

* @allowEmptyPart (boolean)
* @applicableIf (string)
* @internal (boolean)
* @label (string)
* @name (MNTOKEN)
* @noDbIndex (boolean)

### Parents {#parents-8}

`<element>`

### Children {#children-8}

`<keyfield>`

### Description {#description-8}

This element lets you define a key for identifying a record in the table.

A table must have at least one key.

### Use and context of use {#use-and-context-of-use-6}

As a rule, keys are declared after the main element of the schema and the indexes.

A key is known as composite if it includes several fields (i.e. several `<keyfield>  children). Do not use a composite key to define a primary key. </keyfield>`

If the main element of the schema contains the "@autopk=true" attribute, the primary key is unique. We can only have one primary key per schema.

The first 1000 identifiers are reserved, so if a range of values needs to be defined for keys, start at 1000.

### Attribute description {#attribute-description-8}

* **allowEmptyPart (boolean)**: in the case of a composite key, if this attribute is activated, they key is considered valid if at least one of its keys isn't empty. If this is the case, the empty notion value is "0" (boolean or for all types of numerical data). By default, all the keys that make up a composite key need to be entered.
* **applicableIf (string)**: this attribute lets you make the key optional. It defines the condition according to which the key definition will be applied. This attribute receives an XTK expression.
* **internal (boolean)**: if it is activated, this attribute lets Adobe Campaign know that the key is primary.
* **label (string)**: label of the key.
* **name (MNTOKEN)**: internal name of the key.
* **noDbIndex (boolean)**: if it is activated (noDbIndex="true"), the field matching the key will not be indexed.

### Examples {#examples-------}

Declaration of a composite key which authorizes either the "@expr" or the "alias" field to be empty:

```

<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Declaration of a primary key on the "Name" field of STRING type in an `<srcschema>  and the matching SQL query: </srcschema>`

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

## <keyfield> element </keyfield> {#keyfield--element}

### Content model {#content-model-9}

keyfield:==EMPTY

### Attributes {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

### Parents {#parents-9}

`<key>  ,  <dbindex /> </key>`

### Children {#children-9}

None

### Description {#description-9}

This element defines the fields to be integrated into an index or a key.

### Attribute description {#attribute-description-9}

* **xlink (MNTOKEN)**: lets you automatically reference foreign keys defined in the join for a relation table (N-N link).
* **xpath (MNTOKEN)**: definition of an index or a key on an `<attribute>  element. This attribute receives an Xpath which defines the path to the schema attribute that defines the key or the index. </attribute>`

### Examples {#examples-}

Selection of the "sName" field in an index with an Xpath on "@name":

```
<keyfield xpath="@name"/>
```

## <method> element </method> {#method--element}

### Content model {#content-model-10}

method:==( help | parameters)

### Attributes {#attributes-10}

* @_operation (string)
* @access (string)
* @const (boolean)
* @hidden (boolean)
* @label (string)
* @library (string)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolean)

### Parents {#parents-10}

`<methods>  ,  <interface /> </methods>`

### Children {#children-10}

* `<help>`
* `<parameters>`

### Description {#description-10}

This element lets you define a SOAP method.

### Use and context of use {#use-and-context-of-use-7}

SOAP methods enable application processes.

The "@library" is necessary for declaring a new method (non-native): the namespace and the name used for the library are independent from the namespace and name of the schema where the declaration is.

### Attribute description {#attribute-description-10}

* **access (string)**: this attribute defines access control for using the method. If this attribute is missing, identification is mandatory. Available values are: 'anonymous', 'admin' and 'sql'. 
* **const (boolean)**: if it is activated, this attribute means that the declared method will alter the entity
* **label (string)**: label of the method.
* **library (string)**: this method isn't native to the application. This attribute takes the value of the method library where the method definition is found (nms:mylibrary.js).
* **name (MNTOKEN)**: unique method name.
* **static (boolean)**: if this attribute is activated, the method is considered to be autonomous, all parameters must be specified to the method when it is called up.

### Examples {#examples-7}

Definition of the "Subscribe" out of the box method:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>

```

## <methods> element </methods> {#methods--element}

### Content model {#content-model-11}

methods:==method

### Attributes {#attributes-11}

None

### Parents {#parents-11}

`<srcschema>`

### Children {#children-11}

method

### Description {#description-11}

This element lets you define a `<method>  element. It is mandatory for declaring a method. </method>`

### Attribute description {#attribute-description-11}

This element has no attributes.

### Examples {#examples-8}

`<methods async="true" definition="" methods="" more="" of="" one="" or="" p=""> </methods>`

## <param> element {#param--element}

### Content model {#content-model-12}

param:==help

### Attributes {#attributes-12}

* @_operation (string)
* @desc (string)
* @enum (string)
* @inout (string)
* @label (string)
* @localizable (string)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (string)

### Parents {#parents-12}

`<parameters>`

### Children {#children-12}

`<help>`

### Description {#description-12}

This element lets you define a parameter for calling up a SOAP method.

### Attribute description {#attribute-description-12}

* **desc (string)**: description which concerns the `<param>` element.
* **inout (string)**: this attribute defines whether or not the parameter is at the input (in) or output (out) of the SOAP call. If this attribute isn't specified, the default parameter is input ("@inout=in").
* **label (string)**: `<param>` label 
* **localizable (string)**: if it is activated, this attribute tells the collection tool to recover the value of the "@label" attribute for translation (internal use).
* **name (MNTOKEN)**: internal name of the `<param>` 
* **type (string)**: this attribute defines the type of `<param>` element

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
    * DOMDocument
    * DOMElement
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

### Examples {#examples-9}

Definition of the "serviceName" inbound setting of character string type:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

## <parameters> element </parameters> {#parameters--element}

### Content model {#content-model-13}

parameters:==param

### Attributes {#attributes-13}

None

### Parents {#parents-13}

`<method>`

### Children {#children-13}

`<param>`

### Description {#description-13}

This element defines a group of `<parameter>  elements. </parameter>`

### Use and context of use {#use-and-context-of-use-8}

This element is mandatory, even for a single `<param>` child element of the `<method>  element. </method>`

### Attribute description {#attribute-description-13}

None

### Examples {#examples-10}

`<parameters definition="" more="" of="" one="" or="" p="" parameters=""> </parameters>`

## <srcschema> element </srcschema> {#srcschema--element}

### Content model {#content-model-14}

srcSchema:==(attribute | createdBy | data | element | enumeration | help | interface | methods | modifiedBy)

### Attributes {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string), namespace (string), useRecycleBin (boolean), view (boolean), xtkschema (string)

### Parents {#parents-14}

None

### Children {#children-14}

* `<attribute>`
* `<createdby>`
* 

* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

### Description {#description-14}

The `<srcschema>  is the root element of a schema. It is the input point for the definition of the schema. </srcschema>`

### Use and context of use {#use-and-context-of-use-9}

Schema presentation is available in [About schema reference](../../configuration/using/about-schema-reference.md) and [Schema structure](../../configuration/using/schema-structure.md).

### Attribute description {#attribute-description-14}

* **created (datetime)**: this attribute provides information on the date and time of schema creation. It has a "Date Time" form. The values displayed are taken from the server. The time is shown in UTC format. 
* **createdBy-id (long)**: is the identifier of the operator who created the schema. 
* **desc (string)**: schema description
* **entitySchema (string)**: basic schema which syntax and approval are based on (by default for Adobe Campaign: xtk:srcSchema). When you save the current schema, Adobe Campaign will approve its grammar with the schema declared in the @xtkschema attribute.
* **extendedSchema (string)**: receives the name of the out-of-the-box schema which the current schema extension is based on. The form is "namespace:name". 
* **img (string)**: icon linked to the schema (may be defined in the schema creation wizard). 
* **label (string)**: schema label.
* **labelSingular (string)**: label (singular) for display in the interface. 
* **lastModified (datetime)**: this attribute provides information on the date and time of the last modification. It has a "Date Time" form. The values displayed are taken from the server. The time is shown in UTC format. 
* **library (boolean)**: use of the schema as a library and not an entity. This schema may therefore be referenced by other schemas thanks to the "@ref" and "@template" attributes.
* **mappingType (string)**:

    * "sql": database mapping
    * "textFile": text file mapping
    * "xmlFile": XML format text file mapping
    * "binaryFile": binary file mapping

* **modifiedBy-id (long)**: matches the identifier of the operator who changed the schema. 
* **name (string)**: unique schema name.
* **namespace (string)**: namespace of the schema (default: nms, xtk, nl). When creating a new schema for a project, we recommend that you use a dedicated namespace.
* **useRecycleBin (boolean)**: activates the trash feature in the application. Deleted records will be placed in the trash before final deletion. This function is only available in "Delivery" mode.
* **view (boolean)**: if it is activated (@view="true"), the schema will be used as a view. The database structure update wizard will not take the schema into account. This option is mainly used for referencing external tables.
* **xtkschema (string)**: name of the schema which defines schema grammar (xtk:srcSchema by default).

### Examples {#examples-11}

`<srcschema>  element of the "nms:delivery" out of the box schema </srcschema>`

```

<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

## <sysfilter> element </sysfilter> {#sysfilter--element}

### Content model {#content-model-15}

sysFilter:==condition

### Attributes {#attributes-15}

None

### Parents {#parents-15}

`<element>`

### Children {#children-15}

`<condition>`

### Description {#description-15}

This element lets you define a filter.

### Attribute description {#attribute-description-15}

This element has no attributes.

### Examples {#examples-12}

Definition of a filter with a condition on the @name attribute:

```

<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

## <value> element </value> {#value--element}

### Content model {#content-model-16}

value:==help

### Attributes {#attributes-16}

* @applicableIf (string)
* @desc (string)
* @enabledIf (string)
* @img (string)
* @label (string)
* @name (string)
* @value (string)

### Parents {#parents-16}

`<enumeration>`

### Children {#children-16}

`<help>`

### Description {#description-16}

This element lets you define the values stored in an enumeration.

### Attribute description {#attribute-description-16}

* **applicableIf (string)**: this attribute lets you make an enumeration value optional. It receives an XTK expression.
* **desc (string)**: description of the enumeration value.
* **enabledIf (string)**: condition for activating the enumeration value.
* **img (string)**: image linked to the enumeration in the "namespace:image_name" form. The image must be imported onto the application server. 
* **label (string)**: label of the enumeration value. 
* **name (string)**: internal name of the enumeration value. 
* **value (string)**: value of the enumeration value. The type of value is defined based on the type of enumeration. If the enumeration is of character string type, it may only contain character string type values.

### Examples {#examples-13}

```
 
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```

-->