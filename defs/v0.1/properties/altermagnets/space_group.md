# Screening space group (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/space_group`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/space_group.md)**  
**Definition name:** `space_group`

**Property name:** Screening space group  
**Description:** The space-group display string recorded by the altermagnet screening workflow, served verbatim.  
**Type:** string  
**Implementation requirements:**  
- **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.  

- **Query:** MUST be queryable using the OPTIMADE filter language equality and inequality operators. Other filter language features do not need to be available.  
- **Response:**  

A null value means no space group is recorded for this material.

**Examples:**

- `"P6_3/mmc"`
- `"P4_2/mnm"`

**Formats:** [[JSON](space_group.json)] [[MD](space_group.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/space_group",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Screening space group",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "space_group",
        "label": "space_group_altermagnets"
    },
    "x-optimade-unit": "inapplicable",
    "x-optimade-requirements": {
        "support": "may",
        "query-support": "equality only",
        "response-level": "may"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The space-group display string recorded by the altermagnet screening workflow, served verbatim.\n\nA null value means no space group is recorded for this material.",
    "examples": [
        "P6_3/mmc",
        "P4_2/mnm"
    ]
}
```