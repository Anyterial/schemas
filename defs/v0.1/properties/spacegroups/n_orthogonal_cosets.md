# N Orthogonal Cosets (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_orthogonal_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_orthogonal_cosets.md)**  
**Definition name:** `n_orthogonal_cosets`

**Property name:** N Orthogonal Cosets  
**Description:** Number of orthogonal affine normalizer coset representatives stored for the setting.  
**Type:** integer  



**Examples:**

- `47`
- `23`

**Formats:** [[JSON](n_orthogonal_cosets.json)] [[MD](n_orthogonal_cosets.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_orthogonal_cosets",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "N Orthogonal Cosets",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_orthogonal_cosets",
        "label": "n_orthogonal_cosets_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of orthogonal affine normalizer coset representatives stored for the setting.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        47,
        23
    ]
}
```