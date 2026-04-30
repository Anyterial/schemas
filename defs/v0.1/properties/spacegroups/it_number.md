# International Tables Space-Group Number (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number.md)**  
**Definition name:** `it_number`

**Property name:** International Tables Space-Group Number  
**Description:** The International Tables space-group number.  
**Type:** integer  

This integer identifies the space-group type numbered 1 through 230 in International Tables for Crystallography. Multiple Hall settings can share the same `it_number`.

**Examples:**

- `1`
- `5`

**Formats:** [[JSON](it_number.json)] [[MD](it_number.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "International Tables Space-Group Number",
    "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
    "x-optimade-type": "integer",
    "x-compatibility": [
        "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_it_number"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "it_number",
        "label": "it_number_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "The International Tables space-group number.\n\nThis integer identifies the space-group type numbered 1 through 230 in International Tables for Crystallography. Multiple Hall settings can share the same `it_number`.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        1,
        5
    ]
}
```