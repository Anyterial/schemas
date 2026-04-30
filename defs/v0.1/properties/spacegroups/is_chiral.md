# Is Chiral (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_chiral`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_chiral.md)**  
**Definition name:** `is_chiral`

**Property name:** Is Chiral  
**Description:** Boolean flag indicating whether the space group is chiral.  
**Type:** boolean  



**Examples:**

- `true`
- `false`

**Formats:** [[JSON](is_chiral.json)] [[MD](is_chiral.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_chiral",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Is Chiral",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "boolean",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "is_chiral",
        "label": "is_chiral_spacegroups"
    },
    "type": [
        "boolean",
        "null"
    ],
    "description": "Boolean flag indicating whether the space group is chiral.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        true,
        false
    ]
}
```