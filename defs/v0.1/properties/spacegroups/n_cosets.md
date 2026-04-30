# N Cosets (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_cosets.md)**  
**Definition name:** `n_cosets`

**Property name:** N Cosets  
**Description:** Number of affine normalizer coset representatives stored for the setting.  
**Type:** integer  



**Examples:**

- `63`
- `31`

**Formats:** [[JSON](n_cosets.json)] [[MD](n_cosets.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_cosets",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "N Cosets",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_cosets",
        "label": "n_cosets_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of affine normalizer coset representatives stored for the setting.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        63,
        31
    ]
}
```