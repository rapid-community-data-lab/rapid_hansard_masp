# MASP Templates

This repository contains templates for creating schemas and profiles for use with [ro-crate-masp](https://github.com/Language-Research-Technology/ro-crate-masp) (RO-Crate Machine Actionable Schemas and Profiles).

## Scope and Audience

This is for people tasked with describing data, including librarians and archivists, software developers and data managers. It assumes a basic knowledge of what Schemas and Profiles are, and of linked-data fundamentals and experience in working with metadata.

## Principles

The purpose of creating metadata and schemas and profiles is usually interoperability - between tools, and over time as software changes.

Schema development can occur in different ways, depending on the needs, capabilities and starting-points of a project.

For large projects, where schemas are being chosen, extended and developed, this is necessarily a collaborative activity that needs to involve domain experts and metadata / modelling specialists working together, balancing between exact modelling of a domain versus adopting broader schemas, which involves weighing up interoperability and sustainability - there is no one size fits all solution.

Core principles and practices:
1. Consider schemas first, or at least which terms need to be gathered together to describe a domain, and from there proceed to profile development.
2. Re-use terms from existing schemas where possible. For example RO-Crate is built on [Schema.org](https://schema.org/) metadata. Other schemas for language-related collections include [Dublin Core](https://www.dublincore.org/specifications/) and the [Bibliographic Ontology](http://purl.org/ontology/bibo) schema.
3. Look for discipline domain schemas already in use:
    1. Prefer RDF-based ontologies - and transform to MASP format (there’s an OWL schema to MASP converter; make new ones and contribute to the community as necessary)
    2. If there’s a discipline standard that is not RDF based, adapt it to MASP by defining new terms based on the model inherent in the standard.
    3. If there are no publicly available schemas or other starting points, develop a schema from scratch. This should be considered the last resort, only adopt this approach if there is no prior-art to which you can at least link to schema terms, in the interests of building on established community practice.

The steps below are intended to help you with 3.3 for schemas.

## How to Use

Make a fork of this repository for your schema and/or profile.

### Install Dependencies

```
npm install
```

### Schema Generation

To create a schema from the template, follow the instructions in the [Schema User Guide](./schema-user-guide.md).

Coming soon - profile generation.
<!-- ### Profile Generation

To create a profile from the template, follow the instructions in the [Profile User Guide](./profile-user-guide.md). -->