# It Number Enantiomorphic (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number_enantiomorphic`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number_enantiomorphic.md)**  
**Definition name:** `it_number_enantiomorphic`

**Property name:** It Number Enantiomorphic  
**Description:** International Tables number of the enantiomorphic partner space group, when one exists. The value is null for space groups without a distinct enantiomorphic partner.  
**Type:** integer  



**Examples:**

- `78`
- `76`

**Formats:** [[JSON](it_number_enantiomorphic.json)] [[MD](it_number_enantiomorphic.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number_enantiomorphic",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "It Number Enantiomorphic",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "it_number_enantiomorphic",
        "label": "it_number_enantiomorphic_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "International Tables number of the enantiomorphic partner space group, when one exists. The value is null for space groups without a distinct enantiomorphic partner.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        78,
        76
    ]
}
```