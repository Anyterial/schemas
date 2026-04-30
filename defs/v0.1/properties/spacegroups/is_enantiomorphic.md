# Is Enantiomorphic (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_enantiomorphic`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_enantiomorphic.md)**  
**Definition name:** `is_enantiomorphic`

**Property name:** Is Enantiomorphic  
**Description:** Boolean flag indicating whether the space-group type belongs to an enantiomorphic pair.  
**Type:** boolean  



**Examples:**

- `false`
- `true`

**Formats:** [[JSON](is_enantiomorphic.json)] [[MD](is_enantiomorphic.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_enantiomorphic",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Is Enantiomorphic",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "boolean",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "is_enantiomorphic",
        "label": "is_enantiomorphic_spacegroups"
    },
    "type": [
        "boolean",
        "null"
    ],
    "description": "Boolean flag indicating whether the space-group type belongs to an enantiomorphic pair.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        false,
        true
    ]
}
```