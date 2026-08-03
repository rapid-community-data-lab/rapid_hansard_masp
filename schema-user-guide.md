# User Guide for Schema Creation

This is a user guide for creating new schemas with `ro-crate-masp`. In your forked repository, follow the guide to:
- [Edit Schema Spreadsheet](#edit-schema-spreadsheet)
- [Edit Schema Text](#edit-schema-text)
- [Generate Schema Documentation](#generate-schema-documentation)

## Edit Schema Spreadsheet

The spreadsheet `schema/schema-crate/ro-crate-metadata.xlsx` is a template for describing the metadata of a schema. This includes information about the schema's structure and relationships, and allows you to describe terms including Classes, Properties, Defined Terms and Item Instances. It contains the following sheets:

- `RootDataset`: Contains the root dataset entity for the schema.
- `@context`: Contains the `@context` entity for the schema.
- `@type=File`: Contains the `File` entity for the schema.
- `Organization`: Contains the `Organization` entity for the schema.
- `@type=CreativeWork`: Contains the `CreativeWork` entity for the schema.
- `ResourceDescriptor`: Contains the `ResourceDescriptor` entity for the schema.
- `Classes`: Contains the `Class` entities for the schema.
- `Properties`: Contains the `Property` entities for the schema.
- `DefinedTermSets`: Contains the `DefinedTermSet` entities for the schema.
- `DefinedTerms`: Contains the `DefinedTerm` entities for the schema.
- `ItemLists`: Contains the `ItemList` entities for the schema.
- `ItemInstances`: Contains the `ItemInstance` entities for the schema.

NOTE: Quotation marks around entities in the spreadsheet, e.g. `"template:ClassExample"`, indicate that the value is referencing the `@id` of another entity in the schema.

NOTE: Blue cells in the spreadsheet indicate where you need to update the value for your schema manually. Other cells in most cases don't need to be edited.

### RootDataset

The `RootDataset` sheet describes the top level of the schema. It contains the following rows:

Row | Example | Description
--- | --- | ---
@id | `./` | The unique identifier for the schema. `./` is the default identifier, indicating a relative path to your current directory.
@type | `Dataset` | The type of the entity. This should always be `Dataset`.
name | `Template RO-Crate Schema` | The name of the schema in a human-readable format.
description | `This is a template for an RO-Crate schema.` | A description of the schema and its use.
author | `"https://ror.org/00rqy9422"` | The `@id` of the `Organization` entity that is the author of the schema. The template populates this with the same value as the `@id` column in the `Organization` sheet.
license | `GPL-3.0` | The license for the schema.
conformsTo | `["https://language-research-technology.github.io/ro-crate-masp/profiles/ro-crate-masp/profile-crate/#profile", "https://github.com/Language-Research-Technology/ro-crate-schema-tools/blob/main/profiles/sossplus-profile.md"]` | The `@id`s of the `Profile` entities that the schema conforms to. The template populates this with the same values as the `@id` column in the `@type=CreativeWork` sheet.
hasResource | `[#hasSpecializedSchema]` | The `@id` of the `ResourceDescriptor` entity that lists the specialized schema terms defined in the schema. The template populates this with the same value as the `@id` column in the `ResourceDescriptor` sheet.
hasPart | `["schema-documentation.md", "index.html"]` | The `@id`s of the `File` entities that are part of the schema. This should be the same values as the `@id` column in the `@type=File` sheet.

### @context

The `@context` sheet describes the context of the schema. It contains the following rows:

Column | Example | Description
--- | --- | ---
name | `template` | The prefix for the schema descriptor. This should be a unique prefix for your schema, e.g. `ldac`.
@id | `https://w3id.org/template/terms#` | The unique identifier for the schema descriptor. This should be a persistent, managed unique ID in URL format (if available), e.g. `https://w3id.org/ldac/terms#`.

### @type=File

@id | @type | name | description |
--- | --- | --- | --- |
`schema-documentation.md` | `File` | `schema-documentation.md` |  |
`index.html` | `File` | `index.html` |  |

### Organization

Column | Example | Description
--- | --- | ---
@id | `https://ror.org/00rqy9422` | The unique identifier for the organisation. This should be a persistent, managed unique ID in URL format (if available), for example, an [ROR](https://ror.org/), or a hash-based ID, e.g. `#UniversityOfQueensland`.
@type | `Organization` | The type of the entity. This should always be `Organization`.
name | `The University of Queensland` | The name of the organisation in a human-readable format.

### @type=CreativeWork

@id | @type | name | url
--- | --- | --- | ---
`https://language-research-technology.github.io/ro-crate-masp/profiles/ro-crate-masp/profile-crate/#profile` | `[CreativeWork, Profile]` | `RO-Crate MASP Profile` | `https://language-research-technology.github.io/ro-crate-masp/profiles/ro-crate-masp/profile-crate/`

### ResourceDescriptor

The `ResourceDescriptor` sheet contains the entity that all other specialized schema terms (Classes, Properties, DefinedTermSets, DefinedTerms, ItemLists, ItemInstances) are listed under. It contains the following columns:

Column | Example | Description
--- | --- | ---
@id | `#hasSpecializedSchema` | The identifier for the `ResourceDescriptor` entity.
@type | `ResourceDescriptor` | The type of the entity. This should always be `ResourceDescriptor`.
name | `Specialized Schema Terms` | The name of the `ResourceDescriptor` entity in a human-readable format.
hasRole | `"http://www.w3.org/ns/dx/prof/role/schema"` | The role of the `ResourceDescriptor` entity. This should always be `"http://www.w3.org/ns/dx/prof/role/schema"`.


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

### ItemInstances

The `ItemInstances` sheet contains a list of item instances that are part of an `ItemList` in the schema. Each item instance is represented as a row in the sheet, with the following columns:

Column | Example | Description
--- | --- | ---
@id | `template:ItemInstanceExample` | The unique identifier for the item instance. The template populates this with the prefix in `@context` and the item instance name from the `.id` column.
.id | `ItemInstanceExample` | The identifier for the item instance without the schema descriptor prefix. Use PascalCase for the item instance name. This is used to generate the `@id` for the item instance in the schema.
@type | `template:ItemListClassExample` | The type of the entity. This should be a class that is a specialization of `ItemList`. The `template:` prefix should be updated to your schema descriptor, e.g. `ldac:`. Use PascalCase for the class name.
name | `Item Instance Example` | The name of the item instance in a human-readable format.
description | `This is an example of an item instance and its format.` | A description of the item instance and how it should be used.
rdfs:label | `template:ItemInstanceExample` | The label for the item instance. The template populates this with the same value as the `@id` column.
isReverse_itemListElement | `#itemListExample` | The `@id` of the `ItemList` entity that this item instance is an element of. This should be the same value as the `@id` column in the `ItemLists` sheet.
isReverse_hasPart | `#hasSpecializedSchema` | The `@id` of the `ResourceDescriptor` entity that lists the specialized schema terms defined in the schema. This should be the same value as the `@id` column in the `ResourceDescriptor` sheet.

## Edit Schema Text

The `schema/schema-text.md` file allows you to provide more context and description of the schema, as well as defining the sections that will be populated in the output `schema/schema-crate/schema-documentation.md` file. At a minimum, it should include a brief description of the schema, the material it is based on if applicable, and `${rules.all}`.

Complete list of the rules available to populate the document:
 - `${rules.all}`: Generate documentation for each Class and their expected Properties. This option will also create an _All Properties_ section with a summary of each property in the schema.
 - `${rules.allClasses}`: Generate documentation for each Class and their expected Properties. This option will also create an _All Properties_ section with a summary of each property in the schema.
 - `$rules.allPropertyValues`: TODO
 - `${rules.allDefinedTermSets}`: Generate documentation for each entity with the type [DefinedTermSet](https://schema.org/DefinedTermSet) and their expected Defined Terms.
 - `${rules.allItemLists}`: Generate documentation for each entity with the type [ItemList](https://schema.org/ItemList) and their expected Item Instances.

 ## Generate Schema Documentation

 Current process below, to update.

Convert the spreadsheet to JSON-LD:
```
rocxl schema/schema-crate -a
```

Generate documentation for the schema:
```
npm run build:schema
```