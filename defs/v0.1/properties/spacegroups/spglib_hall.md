# Spglib Hall symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall.md)**  
**Definition name:** `spglib_hall`

**Property name:** Spglib Hall symbol  
**Description:** The Hall symbol for this setting as spelled by the spglib library.  
**Type:** string  

This is the Hall symbol spglib associates with the Hall numbers in `spglib_hall_numbers`.
It denotes the same setting as `hall` but may differ in spelling or spacing conventions.

**Examples:**

- `"P 1"`
- `"-P 1"`

**Formats:** [[JSON](spglib_hall.json)] [[MD](spglib_hall.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Spglib Hall symbol",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "spglib_hall",
        "label": "spglib_hall_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The Hall symbol for this setting as spelled by the spglib library.\n\nThis is the Hall symbol spglib associates with the Hall numbers in `spglib_hall_numbers`.\nIt denotes the same setting as `hall` but may differ in spelling or spacing conventions.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "P 1",
        "-P 1"
    ]
}
```