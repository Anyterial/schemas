# Number of orthogonal cosets (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_orthogonal_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_orthogonal_cosets.md)**  
**Definition name:** `n_orthogonal_cosets`

**Property name:** Number of orthogonal cosets  
**Description:** Number of orthogonal affine normalizer coset representatives stored for the setting.  
**Type:** integer  

This value MUST equal the length of the `orthogonal_affine_normalizer_cosets` list of the containing record.

**Examples:**

- `47`
- `23`

**Formats:** [[JSON](n_orthogonal_cosets.json)] [[MD](n_orthogonal_cosets.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_orthogonal_cosets",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Number of orthogonal cosets",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_orthogonal_cosets",
        "label": "n_orthogonal_cosets_transformations"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of orthogonal affine normalizer coset representatives stored for the setting.\n\nThis value MUST equal the length of the `orthogonal_affine_normalizer_cosets` list of the containing record.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        47,
        23
    ]
}
```