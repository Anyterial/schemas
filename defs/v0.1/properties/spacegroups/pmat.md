# Basis transformation matrix (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pmat`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pmat.md)**  
**Definition name:** `pmat`

**Property name:** Basis transformation matrix  
**Description:** Matrix part of a crystallographic basis or setting transformation.
This emitted space-group property uses the common `/properties/symmetry/pmat` definition for its nested value shape and dimensional metadata.  
**Type:** list  



**Examples:**

- `[["1", "0", "0"], ["0", "1", "0"], ["0", "0", "1"]]`
- `[["1", "0", "0"], ["0", "1", "0"], ["0", "0", "2"]]`

**Formats:** [[JSON](pmat.json)] [[MD](pmat.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pmat",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Basis transformation matrix",
    "$comment": "Anyterial space-group property definition inheriting the common semantic `pmat` definition.",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "pmat",
        "label": "pmat_spacegroups"
    },
    "description": "Matrix part of a crystallographic basis or setting transformation.\nThis emitted space-group property uses the common `/properties/symmetry/pmat` definition for its nested value shape and dimensional metadata.",
    "x-optimade-type": "list",
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "x-optimade-dimensions": {
        "names": [
            "dim_lattice",
            "dim_lattice"
        ],
        "sizes": [
            3,
            3
        ]
    },
    "items": {
        "x-optimade-type": "list",
        "x-optimade-unit": "inapplicable",
        "x-optimade-dimensions": {
            "names": [
                "dim_lattice"
            ],
            "sizes": [
                3
            ]
        },
        "type": [
            "array"
        ],
        "description": "One row of the 3 by 3 basis-transformation matrix.",
        "items": {
            "x-optimade-type": "string",
            "x-optimade-unit": "inapplicable",
            "type": [
                "string"
            ],
            "description": "One exact matrix entry."
        }
    },
    "examples": [
        [
            [
                "1",
                "0",
                "0"
            ],
            [
                "0",
                "1",
                "0"
            ],
            [
                "0",
                "0",
                "1"
            ]
        ],
        [
            [
                "1",
                "0",
                "0"
            ],
            [
                "0",
                "1",
                "0"
            ],
            [
                "0",
                "0",
                "2"
            ]
        ]
    ]
}
```