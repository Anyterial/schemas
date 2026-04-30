# Symmetry operation translation vector (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/tvec`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/tvec.md)**  
**Definition name:** `tvec`

**Property name:** Symmetry operation translation vector  
**Description:** Translation vector of a same-setting affine operation.
This emitted space-group property uses the common `/properties/symmetry/tvec` definition for its nested value shape and dimensional metadata.  
**Type:** list  



**Examples:**

- `["0", "0", "0"]`
- `["1/2", "1/2", "0"]`

**Formats:** [[JSON](tvec.json)] [[MD](tvec.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/tvec",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Symmetry operation translation vector",
    "$comment": "Anyterial space-group property definition inheriting the common semantic `tvec` definition.",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "tvec",
        "label": "tvec_spacegroups"
    },
    "description": "Translation vector of a same-setting affine operation.\nThis emitted space-group property uses the common `/properties/symmetry/tvec` definition for its nested value shape and dimensional metadata.",
    "x-optimade-type": "list",
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "x-optimade-dimensions": {
        "names": [
            "dim_lattice"
        ],
        "sizes": [
            3
        ]
    },
    "items": {
        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
        "title": "fraction",
        "x-optimade-type": "string",
        "x-optimade-definition": {
            "label": "fraction_core",
            "kind": "property",
            "version": "0.1.0",
            "format": "1.3",
            "name": "fraction"
        },
        "type": [
            "string",
            "null"
        ],
        "description": "A fraction represented as a string.",
        "examples": [
            "2/3",
            "5/42",
            "10",
            "0"
        ],
        "x-optimade-unit": "inapplicable"
    },
    "examples": [
        [
            "0",
            "0",
            "0"
        ],
        [
            "1/2",
            "1/2",
            "0"
        ]
    ]
}
```