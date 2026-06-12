# Number of conjugacy classes (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_conjugacy_classes`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_conjugacy_classes.md)**  
**Definition name:** `n_conjugacy_classes`

**Property name:** Number of conjugacy classes  
**Description:** Number of conjugacy classes in the crystallographic point group.  
**Type:** integer  

This value MUST equal the length of the `conjugacy_classes` list of the point-group entry.

**Examples:**

- `1`
- `2`

**Formats:** [[JSON](n_conjugacy_classes.json)] [[MD](n_conjugacy_classes.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_conjugacy_classes",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Number of conjugacy classes",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_conjugacy_classes",
        "label": "n_conjugacy_classes_pointgroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of conjugacy classes in the crystallographic point group.\n\nThis value MUST equal the length of the `conjugacy_classes` list of the point-group entry.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        1,
        2
    ]
}
```