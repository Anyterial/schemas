# Is Centric (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_centric`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_centric.md)**  
**Definition name:** `is_centric`

**Property name:** Is Centric  
**Description:** Boolean flag indicating whether the cctbx space group is centric.  
**Type:** boolean  



**Examples:**

- `false`
- `true`

**Formats:** [[JSON](is_centric.json)] [[MD](is_centric.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_centric",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Is Centric",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "boolean",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "is_centric",
        "label": "is_centric_spacegroups"
    },
    "type": [
        "boolean",
        "null"
    ],
    "description": "Boolean flag indicating whether the cctbx space group is centric.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        false,
        true
    ]
}
```