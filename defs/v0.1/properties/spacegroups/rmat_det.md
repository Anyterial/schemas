# Symmetry operation rotation determinant (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_det`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_det.md)**  
**Definition name:** `rmat_det`

**Property name:** Symmetry operation rotation determinant  
**Description:** Determinant of the `rmat` linear matrix part of a same-setting operation.  
**Type:** integer  



**Examples:**

- `-1`
- `1`

**Formats:** [[JSON](rmat_det.json)] [[MD](rmat_det.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_det",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Symmetry operation rotation determinant",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "rmat_det",
        "label": "rmat_det_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Determinant of the `rmat` linear matrix part of a same-setting operation.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        -1,
        1
    ]
}
```