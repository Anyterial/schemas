# Spglib Hall (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall.md)**  
**Definition name:** `spglib_hall`

**Property name:** Spglib Hall  
**Description:** Hall setting selected by spglib for the space-group type or setting, represented as a normalized Hall key.  
**Type:** string  



**Examples:**

- `"P 1"`
- `"-P 1"`

**Formats:** [[JSON](spglib_hall.json)] [[MD](spglib_hall.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Spglib Hall",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
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
    "description": "Hall setting selected by spglib for the space-group type or setting, represented as a normalized Hall key.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "P 1",
        "-P 1"
    ]
}
```