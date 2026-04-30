# Centering translations as xyz strings (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations_xyz.md)**  
**Definition name:** `centering_translations_xyz`

**Property name:** Centering translations as xyz strings  
**Description:** Centering translations of the conventional cell, represented as `x,y,z`-style coordinate shifts. The zero translation is listed first.  
**Type:** list  



**Examples:**

- `["0,0,0"]`
- `["0,0,0", "1/2,1/2,0"]`

**Formats:** [[JSON](centering_translations_xyz.json)] [[MD](centering_translations_xyz.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations_xyz",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Centering translations as xyz strings",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "centering_translations_xyz",
        "label": "centering_translations_xyz_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "Centering translations of the conventional cell, represented as `x,y,z`-style coordinate shifts. The zero translation is listed first.",
    "x-optimade-unit": "inapplicable",
    "items": {
        "x-optimade-type": "string",
        "x-optimade-unit": "inapplicable",
        "type": [
            "string"
        ]
    },
    "examples": [
        [
            "0,0,0"
        ],
        [
            "0,0,0",
            "1/2,1/2,0"
        ]
    ]
}
```