# User Guide for Schema Creation

Schemas specify a metadata vocabulary of classes, properties and other terms, and may include additional specifications and requirements for particular terms. For an example of a schema, see the [Language Data Commons Schema](https://w3id.org/ldac/terms) for language resources.

This is a user guide for creating new schemas with `ro-crate-masp`. In your forked repository, follow the guide to:
- [Edit Schema Spreadsheet](#edit-schema-spreadsheet)
- [Edit Schema Text](#edit-schema-text)
- [Generate Schema Documentation](#generate-schema-documentation)

## Edit Schema Spreadsheet

The spreadsheet `schema/schema-crate/additional-ro-crate-metadata.xlsx` is a template for describing the metadata of a schema. This includes information about the schema's structure and relationships, and allows you to describe terms including Classes, Properties, Defined Terms and Item List Elements. It contains the following sheets:

- [RootDataset](#rootdataset): Contains the root dataset entity for the schema.
- [@context](#@context): Contains the `@context` entity for the schema.
- [Organization](#organization): Contains the [Organization](http://schema.org/Organization) entity for the schema.
- [CreativeWork](#creativework): Contains the [CreativeWork](http://schema.org/CreativeWork) entities for the schema.
- [ResourceDescriptor](#resourcedescriptor): Contains the [ResourceDescriptor](http://www.w3.org/ns/dx/prof/ResourceDescriptor) entity for the schema.
- [Schema](#schema): Contains the [Schema](http://schema.org/Schema) entity.
- [Classes](#classes): Contains the [Class](http://schema.org/Class) entities for the schema.
- [Properties](#properties): Contains the [Property](http://schema.org/Property) entities for the schema.
- [DefinedTermSets](#definedtermsets): Contains the [DefinedTermSet](http://schema.org/DefinedTermSet) entities for the schema, if applicable.
- [DefinedTerms](#definedterms): Contains the [DefinedTerm](http://schema.org/DefinedTerm) entities for the schema, if applicable.
- [ItemLists](#itemlists): Contains the [ItemList](http://schema.org/ItemList) entities for the schema, if applicable.
- [ItemListElements](#itemlistelements): Contains the [ItemListElement](http://schema.org/itemListElement) entities for the schema, if applicable.

> NOTE: Quotation marks around entities in the spreadsheet, e.g. `"template:ClassExample"`, indicate that the value is referencing the `@id` of another entity in the schema.

> NOTE: Blue cells in the spreadsheet indicate where you need to update the value for your schema manually. Other cells in most cases don't need to be edited.

### RootDataset

The `RootDataset` sheet describes the top level of the schema. It contains the following rows:

Row | Example | Description
--- | --- | ---
@id | `./` | The unique identifier for the schema. `./` is the default identifier, indicating a relative path to your current directory.
@type | `Dataset` | The type of the entity. This should always be `Dataset`.
name | `Template RO-Crate Schema` | The name of the schema in a human-readable format.
description | `This is a template for an RO-Crate schema.` | A description of the schema and its use.
author | `"https://ror.org/00rqy9422"` | The `@id` of the `Organization` entity that is the author of the schema. The template populates this with the same value as the `@id` column in the `Organization` sheet.
license | `"https://www.apache.org/licenses/LICENSE-2.0.html"` | The license for the schema. The template populates this with the same value as the `@id` column in the `CreativeWork` sheet.
conformsTo | `"https://w3id.org/ro/ro-crate-masp/profile"` | The `@id`s of the `Profile` entities that the schema conforms to. The template populates this with the same values as the `@id` column in the `CreativeWork` sheet.
hasResource | `"#hasSpecializedSchema"` | The `@id` of the `ResourceDescriptor` entity that lists the specialized schema terms defined in the schema. The template populates this with the same value as the `@id` column in the `ResourceDescriptor` sheet.

### @context

The `@context` sheet describes the namespace and unique identifier of the schema. It contains the following rows:

Column | Example | Description
--- | --- | ---
name | `template` | The namespace for the schema descriptor. In the other metadata sheets, this namespace is prefixed to the terms. This should be a unique namespace for your schema, e.g. `ldac`.
@id | `arcp://name,template/terms#` | The unique identifier for the schema descriptor. This should be a persistent, managed unique ID in URL format (if available), e.g. `https://w3id.org/ldac/terms#`. The default uses an `arcp` URI, which can be used for schemas that don't have a persistent, managed unique ID or won't be published.

### Organization

The `Organization` sheet contains any organisations that are referenced in the schema (e.g. in the `author` section on the `RootDataset` sheet). It contains the following columns:

Column | Example | Description
--- | --- | ---
@id | `https://ror.org/00rqy9422` | The unique identifier for the organisation, which is used to populate the `author` property in the `RootDataset` sheet. This should be a persistent, managed unique ID in URL format (if available), for example, an [ROR](https://ror.org/), or a hash-based ID, e.g. `#UniversityOfQueensland`.
@type | `Organization` | The type of the entity. This should always be `Organization`.
name | `The University of Queensland` | The name of the organisation in a human-readable format.

### CreativeWork

The `CreativeWork` sheet contains any documents that are referenced in the schema (e.g. in the `conformsTo` and `license` sections on the `RootDataset` sheet). At a minimum, it should list the MASP profile that the schema conforms to, and the license information. It contains the following columns:

**MASP Profile Example:**

Column | Example | Description
--- | --- | ---
@id | `https://w3id.org/ro/ro-crate-masp/profile` | The unique identifier for the MASP profile which this schema conforms to.
@type | `[CreativeWork, Profile]` | The type of the entity. This should always be `[CreativeWork, Profile]`.
name | `RO-Crate MASP Profile` | The name of the profile in a human-readable format.

**License Example:**

Column | Example | Description
--- | --- | ---
@id | `https://www.apache.org/licenses/LICENSE-2.0.html` | The unique identifier for the license. This should be a persistent, managed unique ID in URL format (if available), e.g. `https://www.apache.org/licenses/LICENSE-2.0.html`.
@type | `CreativeWork` | The type of the entity. This should always be `CreativeWork`.
name | `Apache License, Version 2.0` | The name of the license in a human-readable format.

### ResourceDescriptor

The `ResourceDescriptor` sheet contains the entity that all other specialized schema terms (Classes, Properties, DefinedTermSets, DefinedTerms, ItemLists, ItemListElements) are part of. It contains the following columns:

Column | Example | Description
--- | --- | ---
@id | `#hasSpecializedSchema` | The identifier for the `ResourceDescriptor` entity.
@type | `ResourceDescriptor` | The type of the entity. This should always be `ResourceDescriptor`.
name | `Specialized Schema Terms` | The name of the `ResourceDescriptor` entity in a human-readable format.
hasRole | `"http://www.w3.org/ns/dx/prof/role/schema"` | The role of the `ResourceDescriptor` entity. This should always be `"http://www.w3.org/ns/dx/prof/role/schema"`.

### Schema

The `Schema` sheet contains the entity that describes the schema itself. It contains the following columns:

Column | Example | Description
--- | --- | ---
@id | http://www.w3.org/ns/dx/prof/role/schema | The identifier for the `Schema` entity.
@type | `Schema` | The type of the entity. This should always be `Schema`.
name | `Schema` | The name of the `Schema` entity in a human-readable format.
description | `Machine-readable structural descriptions of data defined by the profile` | A description of the `Schema` entity and how it should be used.

### Classes

The `Classes` sheet contains the specialized schema classes defined in the schema. Each class is represented as a row in the sheet, with the following columns:

Column | Example | Description
--- | --- | ---
@id | `template:ClassExample` | The unique identifier for the class. The template populates this with the prefix in `@context` and the class name from the `.id` column.
.id | `ClassExample` | The identifier for the class without the schema descriptor prefix. Use PascalCase for the class name. This is used to generate the `@id` for the class in the schema.
@type | `rdfs:Class` | The type of the entity. This should always be `rdfs:Class`.
name | `Class Example` | The name of the class in a human-readable format.
description | `This is an example of a class and its format.` | A description of the class and how it should be used.
rdfs:label | `template:ClassExample` | The label for the class. The template populates this with the same value as the `@id` column.
isReverse_hasPart | `#hasSpecializedSchema` | The `@id` of the `ResourceDescriptor` entity that lists the specialized schema terms defined in the schema. This should be the same value as the `@id` column in the `ResourceDescriptor` sheet.

### Properties

The `Properties` sheet contains the specialized schema properties defined in the schema. Each property is represented as a row in the sheet, with the following columns:

Column | Example | Description
--- | --- | ---
@id | `template:propertyExample` | The unique identifier for the property. The template populates this with the prefix in `@context` and the property name from the `.id` column.
.id | `propertyExample` | The identifier for the property without the schema descriptor prefix. Use camelCase for the property name. This is used to generate the `@id` for the property in the schema.
@type | `rdf:Property` | The type of the entity. This should always be `rdf:Property`.
name | `Property Example` | The name of the property in a human-readable format.
description | `This is an example of a property and its format.` | A description of the property and how it should be used.
domainIncludes | `"template:ClassExample"` | The class that this property can be used with.
rangeIncludes | `"@id": "http://schema.org/Text"` | The type of values that this property can have.
rdfs:label | `template:propertyExample` | The label for the property. The template populates this with the same value as the `@id` column.
isReverse_hasPart | `#hasSpecializedSchema` | The `@id` of the `ResourceDescriptor` entity that lists the specialized schema terms defined in the schema. This should be the same value as the `@id` column in the `ResourceDescriptor` sheet.

### DefinedTermSets

The `DefinedTermSets` sheet contains the specialized schema defined term sets defined in the schema. Each defined term set is represented as a row in the sheet, with the following columns:

Column | Example | Description
--- | --- | ---
@id | `template:DefinedTermSetExample` | The unique identifier for the defined term set. The template populates this with the prefix in `@context` and the defined term set name from the `.id` column.
.id | `DefinedTermSetExample` | The identifier for the defined term set without the schema descriptor prefix. Use PascalCase for the defined term set name. This is used to generate the `@id` for the defined term set in the schema.
@type | `DefinedTermSet` | The type of the entity. This should always be `DefinedTermSet`.
name | `Defined Term Set Example` | The name of the defined term set in a human-readable format.
description | `This is an example of a defined term set and its format.` | A description of the defined term set and how it should be used.
rdfs:label | `template:DefinedTermSetExample` | The label for the defined term set. The template populates this with the same value as the `@id` column.
rdfs:comment | `This is an example of a defined term set and its format.` | A comment describing the defined term set.
isReverse_hasPart | `#hasSpecializedSchema` | The `@id` of the `ResourceDescriptor` entity that lists the specialized schema terms defined in the schema. This should be the same value as the `@id` column in the `ResourceDescriptor` sheet.

### DefinedTerms

The `DefinedTerms` sheet contains the specialized schema defined terms defined in the schema. Each defined term is represented as a row in the sheet, with the following columns:

Column | Example | Description
--- | --- | ---
@id | `template:DefinedTermExample` | The unique identifier for the defined term. The template populates this with the prefix in `@context` and the defined term name from the `.id` column.
.id | `DefinedTermExample` | The identifier for the defined term without the schema descriptor prefix. Use PascalCase for the defined term name. This is used to generate the `@id` for the defined term in the schema.
@type | `DefinedTerm` | The type of the entity. This should always be `DefinedTerm`.
name | `Defined Term Example` | The name of the defined term in a human-readable format.
description | `This is an example of a defined term and its format.` | A description of the defined term and how it should be used.
rdfs:label | `template:DefinedTermExample` | The label for the defined term. The template populates this with the same value as the `@id` column.
inDefinedTermSet | `"template:DefinedTermSetExample"` | The defined term set that this defined term belongs to. The `template:` prefix should be updated to your schema descriptor, e.g. `ldac:`. Use PascalCase for the defined term set name.
isReverse_hasPart | `#hasSpecializedSchema` | The `@id` of the `ResourceDescriptor` entity that lists the specialized schema terms defined in the schema. This should be the same value as the `@id` column in the `ResourceDescriptor` sheet.

### ItemLists

The `ItemLists` sheet contains a list of item lists that are part of the schema. Each item list is represented as a row in the sheet, with the following columns:

Column | Example | Description
--- | --- | ---
@id | `#itemListExample` | The unique identifier for the item list. The template populates this with the prefix `#` and the item list name from the `.id` column.
.id | `itemListExample` | The identifier for the item list without the schema descriptor prefix. Use camelCase for the item list name. This is used to generate the `@id` for the item list in the schema.
@type | `ItemList` | The type of the entity. This should always be `ItemList`.
name | `Item List Example` | The name of the item list in a human-readable format.
description | `This is an example of an item list and its format.` | A description of the item list and how it should be used.

### ItemListElements

The `ItemListElements` sheet contains a list of item elements that are part of an `ItemList` in the schema. Each item element is represented as a row in the sheet, with the following columns:

Column | Example | Description
--- | --- | ---
@id | `template:ItemListElementExample` | The unique identifier for the item element. The template populates this with the prefix in `@context` and the item element name from the `.id` column.
.id | `ItemListElementExample` | The identifier for the item element without the schema descriptor prefix. Use PascalCase for the item element name. This is used to generate the `@id` for the item element in the schema.
@type | `template:ItemListClassExample` | The type of the entity. This should be a class that is a specialization of `ItemList`. The `template:` prefix should be updated to your schema descriptor, e.g. `ldac:`. Use PascalCase for the class name.
name | `Item List Element Example` | The name of the item element in a human-readable format.
description | `This is an example of an item element and its format.` | A description of the item element and how it should be used.
rdfs:label | `template:ItemListElementExample` | The label for the item element. The template populates this with the same value as the `@id` column.
isReverse_itemListElement | `#itemListExample` | The `@id` of the `ItemList` entity that this item element is part of. This should be the same value as the `@id` column in the `ItemLists` sheet.
isReverse_hasPart | `#hasSpecializedSchema` | The `@id` of the `ResourceDescriptor` entity that lists the specialized schema terms defined in the schema. This should be the same value as the `@id` column in the `ResourceDescriptor` sheet.

## Edit Schema Text

The `schema/schema-text.md` file allows you to provide more context and description of the schema, as well as defining the sections that will be populated in the output `schema/schema-crate/schema-documentation.md` file. At a minimum, it should include a brief description of the schema, the material it is based on if applicable, and `${rules.all}`.

Complete list of the rules available to populate the document:
 - `${rules.all}`: Generate documentation for each Class and their expected Properties. This option will also create an _All Properties_ section with a summary of each property in the schema.
 - `${rules.allClasses}`: Generate documentation for each Class and their expected Properties. This option will also create an _All Properties_ section with a summary of each property in the schema.
 - `${rules.allPropertyValues}`: Specific values such as strings, expected as a value for a property, for example, a particular file must have an @id of README.md.
 - `${rules.allDefinedTermSets}`: Generate documentation for each entity with the type [DefinedTermSet](https://schema.org/DefinedTermSet) and their expected Defined Terms.
 - `${rules.allItemLists}`: Generate documentation for each entity with the type [ItemList](https://schema.org/ItemList) and their expected Item List Elements.

## Generate Schema Documentation

Once your spreadsheet and `schema-text.md` file are updated, follow the steps below to generate the schema documentation.

Convert the spreadsheet to JSON-LD (JSON Linked Data) format:
```
rocxl schema/schema-crate -a
```

This will generate the `schema/schema-crate/ro-crate-metadata.json` file, as well as the `schema/schema-crate/ro-crate-preview.html` file that can be opened in a web browser to preview the schema.

Generate documentation for the schema:
```
npm run build:schema
```

This will generate the `schema/schema-crate/schema-documentation.md` file, which contains the documentation for the schema based on the spreadsheet and `schema-text.md` file. It also generates the `schema/schema-crate/index.html` file that can be opened in a web browser to view the documentation.

> If you need to make further edits to the schema, update the spreadsheet and/or `schema-text.md` file, then re-run the commands above to regenerate the updated documentation.