# N Linear Parts (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_linear_parts`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_linear_parts.md)**  
**Definition name:** `n_linear_parts`

**Property name:** N Linear Parts  
**Description:** Number of distinct linear matrix parts represented in a normalizer or transform table.  
**Type:** integer  



**Examples:**

- `2`
- `4`

**Formats:** [[JSON](n_linear_parts.json)] [[MD](n_linear_parts.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_linear_parts",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "N Linear Parts",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_linear_parts",
        "label": "n_linear_parts_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of distinct linear matrix parts represented in a normalizer or transform table.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        2,
        4
    ]
}
```