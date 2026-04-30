# Symmetry operation rotation is orthogonal (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_is_orthogonal`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_is_orthogonal.md)**  
**Definition name:** `rmat_is_orthogonal`

**Property name:** Symmetry operation rotation is orthogonal  
**Description:** Boolean flag indicating whether `rmat` is orthogonal in the conventional coordinate basis.  
**Type:** boolean  



**Examples:**

- `true`
- `false`

**Formats:** [[JSON](rmat_is_orthogonal.json)] [[MD](rmat_is_orthogonal.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_is_orthogonal",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Symmetry operation rotation is orthogonal",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "boolean",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "rmat_is_orthogonal",
        "label": "rmat_is_orthogonal_spacegroups"
    },
    "type": [
        "boolean",
        "null"
    ],
    "description": "Boolean flag indicating whether `rmat` is orthogonal in the conventional coordinate basis.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        true,
        false
    ]
}
```