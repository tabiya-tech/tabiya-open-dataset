
# Tabiya ESCO v1.1.1 CSV Documentation

This data set is based on the original ESCO v.1.1.1.

There are 8 CSV files in this dataset. Each file contains a different type of data. The files are:
- [Skill Groups](#skill-groups-dataset-documentation)
- [Skills](#Skills-Dataset-Documentation)
- [Skills Hierarchy](#skills-hierarchy-dataset-documentation)
- [Skill to Skill Relation](#Skill-Skill-Relations-Dataset-Documentation)
- [ISCO Groups](#ISCO-groups-dataset-documentation)
- [Occupations](#occupations-dataset-documentation)
- [Occupations Hierarchy](#occupations-hierarchy-dataset-documentation) 
- [Occupation to Skill Relation](#Occupation-to-Skill-Relations-Dataset-Documentation)

## General notes on the fields of the CSV files

### UUID History

A UUID history is a list of all the UUIDs that have been assigned to an entity during its lifecycle, e.g. when the entity is created, imported, exported or copied into our platform.

It is an identifier that can be used for tracking objects not only across their lifecycle, but also across systems. 

The UUID history is ordered from newest to oldest UUID.

The entities in this dataset have been assigned an initial UUID. When an entity is imported into our platform, a new UUID will be issued and added at the top of UUID history.   

The UUID used by the platform are based on the [Universally Unique Identifier v4](https://datatracker.ietf.org/doc/html/rfc4122) standard. 

The UUID History is stored in the field `UUIDHISTORY` 

> The maximum number of UUIDs in the history for an object is constrained to `10000`.

### Origin Uri

The Origin Uri is a [URI](https://datatracker.ietf.org/doc/html/rfc3986) that points to the location where an entity was originally defined. For this dataset, the origin uri links back to the ESCO website.

The Origin Uri is stored in the field `ORIGINURI`

> The maximum length for the Origin Uri is `4096` characters.

### List Properties in the CSV files

List properties are stored in the CSV files as strings separated by a `\n` character. Currently, we do not support values that contain a new line.

### ID

The `ID` field is a unique identifier for each entity in the dataset. It is used for referencing within the CSV dataset, for example, in the relations between entities.

This field is not meant to be used as an identifier outside the scope of the CSV files, for that purpose you should use the first entry in the UUID History. see [here](#uuid-history)

### Occupation Types

The Tabiya Open Taxonomy defines three different occupation types. They are:
- `ESCO`: An occupation that originates from the ESCO framework.
- `LOCALIZED`: An ESCO occupation that has been localized in a particular locale.
- `LOCAL`: An occupation that does not originate from the ESCO framework and is defined only in a particular locale.

> Since this is the original ESCO dataset it contains only `ESCO` occupations.
---
## Skills Dataset Documentation

### File Description
- **File Name**: `skills.csv`
- **Number of Rows**: 13897
- **Number of Columns**: 10

### Link to file 
[skills.csv](csv/skills.csv)

### Fields Description
- [`ORIGINURI`](#origin-uri): A URI that points to the location where an entity was originally defined. See [here](#origin-uri) for the format .
- [`ID`](#id): A unique identifier for each skill, used for referencing within the CSV dataset. See [here](#id) for details.
- [`UUIDHISTORY`](#uuid-history): A list of valid UUID_V4 strings. See [here](#uuid-history) for details.
- `SKILLTYPE`: Derived from the ESCO skill type. 
  - Possible values: `skill/competence`,`knowledge`,`language`,`attitude`,
- `REUSELEVEL`:  Derived from the ESCO skill reuse level. 
  - Possible values: `sector-specific`,`occupation-specific`,`cross-sector`,`transversal`.
- `PREFERREDLABEL`: The preferred label from the ESCO object.
- `ALTLABELS`: The list of alternative labels from the ESCO object. See [here](#list-properties-in-the-CSV-files) for the format.
  - Maximum length per label: `256` characters.
  - Maximum number of labels: `100`.
- `DESCRIPTION`: The description from the ESCO object. 
  -  Maximum length:`4000` characters.
- `DEFINITION`: The definition from the ESCO object. 
  -  Maximum length:`4000` characters.
- `SCOPENOTE`: The scope note from the ESCO object. 
  -  Maximum length:`4000` characters.

## Skill Groups Dataset Documentation

## File Description
- **File Name**: `skillGroups.csv`
- **Number of Rows**: 641
- **Number of Columns**: 8

### Link to file
[skillGroups.csv](csv/skillGroups.csv)

### Fields Description
- [`ORIGINURI`](#origin-uri): A URI that points to the location where an entity was originally defined. See [here](#origin-uri) for the format .
- [`ID`](#id): A unique identifier for each skill-group, used for referencing within the CSV dataset. See [here](#id) for details.
- [`UUIDHISTORY`](#uuid-history): A list of valid UUID_V4 strings. See [here](#uuid-history) for details.
- `CODE`: SkillGroup code as defined by ESCO. It has the general format `SX.X.X`, where `X` is a number.
- `PREFERREDLABEL`: The preferred label from the ESCO object.
- `ALTLABELS`: The list of alternative labels from the ESCO object. See [here](#list-properties-in-the-CSV-files) for the format.
  - Maximum length per label: `256` characters.
  - Maximum number of labels: `100`.
- `DESCRIPTION`: The description from the ESCO object. 
  -  Maximum length:`4000` characters.
- `SCOPENOTE`: The scope note from the ESCO object. 
  -  Maximum length:`4000` characters.

## Occupations Dataset Documentation

### File Description
- **File Name**: `occupations.csv`
- **Number of Rows**: 3007
- **Number of Columns**: 12

### Link to file
[occupations.csv](csv/occupations.csv)

### Fields Description
- [`ORIGINURI`](#origin-uri): A URI that points to the location where an entity was originally defined. See [here](#origin-uri) for the format .
- [`ID`](#id): A unique identifier for each occupation, used for referencing within the CSV dataset. See [here](#id) for details.
- [`UUIDHISTORY`](#uuid-history): A list of valid UUID_V4 strings. See [here](#uuid-history) for details.
- `ISCOGROUPCODE`: A four digit identification code for the isco group that the occupation belongs to.
- `CODE`: An occupation code is a code assigned to a particular occupation by a classification system. It has the general format `XXXX.XX.XX...`, where `X` is a number. (eg `2654.1.7`)
- `PREFERREDLABEL`: The preferred label from the ESCO object.
- `ALTLABELS`: The list of alternative labels from the ESCO object. See [here](#list-properties-in-the-CSV-files) for the format.
  - Maximum length per label: `256` characters.
  - Maximum number of labels: `100`.
- `DESCRIPTION`: The description from the ESCO object. 
  -  Maximum length:`4000` characters.
- `DEFINITION`: The definition from the ESCO object. 
  -  Maximum length:`4000` characters.
- `SCOPENOTE`: The scope note from the ESCO object. 
  -  Maximum length:`4000` characters.
- `REGULATEDPROFESSIONNOTE`: A link to Describes whether the occupation is regulated or not. Can be [unregulated](http://data.europa.eu/esco/regulated-professions/unregulated) or [regulated](http://data.europa.eu/esco/regulated-professions/regulated).
- `OCCUPATIONTYPE`: The occupation type in the tabiya platform. Will always be `ESCO` for this dataset.

## ISCO Groups Dataset Documentation

### File Description
- **File Name**: `ISCOGroups.csv`
- **Number of Rows**: 619
- **Number of Columns**: 7

### Link to file
[ISCOGroups.csv](csv/ISCOGroups.csv)

### Fields Description
- [`ORIGINURI`](#origin-uri): A URI that points to the location where an entity was originally defined. See [here](#origin-uri) for the format .
- [`ID`](#id): A unique identifier for each ISCO group, used for referencing within the CSV dataset. See [here](#id) for details.
- [`UUIDHISTORY`](#uuid-history): A list of valid UUID_V4 strings. See [here](#uuid-history) for details.
- `CODE`: A four digit identification code for the ISCO group. Looks like `XXXX` where `X` is a number.
- `PREFERREDLABEL`: The preferred label from the ESCO object.
- `ALTLABELS`: The list of alternative labels from the ESCO object. See [here](#list-properties-in-the-CSV-files) for the format.
  - Maximum length per label: `256` characters.
  - Maximum number of labels: `100`.
- `DESCRIPTION`: The description from the ESCO object. 
  -  Maximum length:`4000` characters.

## Skill-Skill Relations Dataset Documentation

### File Description
- **File Name**: `skill_skill_relations.csv`
- **Number of Rows**: 6899
- **Number of Columns**: 3

### Link to file
[skill_skill_relations.csv](csv/skill_skill_relations.csv)

### Fields Description
- `REQUIRINGID`: The [`ID`](#id) of the skill that requires another skill.
- `RELATIONTYPE`: The type assigned to the relation in the ESCO model. Can be `essential` or `optional`.
- `REQUIREDID`: The  [`ID`](#id) of the skill that is required by another skill.


## Occupation-to-Skill Relations Dataset Documentation

### File Description
- **File Name**: `occupation_skill_relations.csv`
- **Number of Rows**: 123789
- **Number of Columns**: 4

### Link to file
[occupation_skill_relations.csv](csv/occupation_skill_relations.csv)

### Fields Description
- `OCCUPATIONTYPE`: The type of the occupation. Will always be `ESCO` for this dataset.
- `OCCUPATIONID`: The  [`ID`](#id) of the occupation.
- `RELATIONTYPE`: The type assigned to the relation in the ESCO model. Can be `essential` or `optional`.
- `SKILLID`: The  [`ID`](#id) of the skill.


## Skills Hierarchy Dataset Documentation

### File Description
- **File Name**: `skills_hierarchy.csv`
- **Number of Rows**: 20650
- **Number of Columns**: 4

### Link to file
[skills_hierarchy.csv](csv/skills_hierarchy.csv)

### Fields Description
- `PARENTOBJECTTYPE`: The type of the parent object. Can be Skill or SkillGroup.
- `PARENTID`: The  [`ID`](#id) of the parent object.
- `CHILDID`: The  [`ID`](#id) of the child object.
- `CHILDOBJECTTYPE`: The type of the child object. Can be Skill or SkillGroup.

> Caveat: A skill cannot be the parent of a skill group.

## Occupations Hierarchy Dataset Documentation

### Overview
This file, part of the 'tabiya-open-dataset', outlines the hierarchical structure of various occupations. It is vital for understanding the organizational and functional relationships between different job roles, which is crucial for job classification and career path planning.

### File Description
- **File Name**: `occupations_hierarchy.csv`
- **Number of Rows**: 3617
- **Number of Columns**: 4

### Link to file
[occupations_hierarchy.csv](csv/occupations_hierarchy.csv)

### Fields Description
- `PARENTOBJECTTYPE`: The type of the parent object. Can be Occupation or ISCOGroup.
- `PARENTID`: The  [`ID`](#id) of the parent object.
- `CHILDID`: The  [`ID`](#id) of the child object.
- `CHILDOBJECTTYPE`: The type of the child object. Can be Occupation or ISCOGroup.

> Caveat: An occupation cannot be the parent of an ISCO group.
