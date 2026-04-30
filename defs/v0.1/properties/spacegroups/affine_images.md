# Affine images (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_images`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_images.md)**  
**Definition name:** `affine_images`

**Property name:** Affine images  
**Description:** Same-space-group affine images for a standard setting.
The list combines Euclidean normalizer operations and isomorphic subgroup transforms to enumerate alternative affine images of the same space group used by runtime search code.
Matrix/vector transform fields use `pmat` and `pvec` according to `/properties/symmetry/basis_transform`.  
**Type:** list  



**Examples:**

- `[{"pmat": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "1"]], "pvec": ["0", "0", "0"]}]`

**Formats:** [[JSON](affine_images.json)] [[MD](affine_images.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_images",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Affine images",
    "$comment": "Anyterial property definition for same-space-group affine images.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "affine_images",
        "label": "affine_images_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Same-space-group affine images for a standard setting.\nThe list combines Euclidean normalizer operations and isomorphic subgroup transforms to enumerate alternative affine images of the same space group used by runtime search code.\nMatrix/vector transform fields use `pmat` and `pvec` according to `/properties/symmetry/basis_transform`.",
    "items": {
        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/basis_transform",
        "title": "Basis transformation",
        "$comment": "Reusable Anyterial definition for one crystallographic change-of-basis or setting transform.",
        "x-optimade-type": "dictionary",
        "x-optimade-definition": {
            "kind": "property",
            "version": "0.1.0",
            "format": "1.3",
            "name": "basis_transform",
            "label": "basis_transform_symmetry"
        },
        "x-optimade-unit": "inapplicable",
        "type": [
            "object",
            "null"
        ],
        "description": "One crystallographic basis or setting transformation represented by an exact matrix and an exact origin shift.\nParent tables use this object for B\u00e4rnighausen transforms, isomorphic subgroup transforms, Hall-to-standard transforms, and related setting maps.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **pmat**: REQUIRED; Exact 3x3 matrix.\n      Matrix part of the basis or setting transformation.\n\n    - **pvec**: REQUIRED; List of 3 Fractions (String).\n      Translation or origin-shift vector of the basis or setting transformation.\n\n    - **index**: OPTIONAL; Integer.\n      Subgroup index or cell-index metadata when the parent table defines such an index.\n\n    - **target**: OPTIONAL; String or integer.\n      Target setting, Hall entry, IT number, or other target identifier as defined by the parent table.\n\n    - **wyckoff\\_splitting**: OPTIONAL; Dictionary.\n      Wyckoff-position splitting metadata associated with the transform when available.",
        "properties": {
            "pmat": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pmat",
                "title": "Basis transformation matrix",
                "$comment": "Reusable Anyterial definition for the matrix part of a crystallographic basis or setting transformation.",
                "x-optimade-type": "list",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "pmat",
                    "label": "pmat_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "array",
                    "null"
                ],
                "description": "Matrix part of a crystallographic basis or setting transformation.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings so that exact rational or algebraic values can be preserved without floating-point rounding.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- The parent transform definition specifies the coordinate convention and whether the matrix maps from a source setting to a target setting or conversely.",
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
            },
            "pvec": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec",
                "title": "Basis transformation origin shift",
                "$comment": "Reusable Anyterial definition for the translation/origin-shift part of a crystallographic basis or setting transformation.",
                "x-optimade-type": "list",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "pvec",
                    "label": "pvec_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "array",
                    "null"
                ],
                "description": "Translation or origin-shift part of a crystallographic basis or setting transformation.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- The parent transform definition specifies the source and target setting convention for the transformation.",
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
                        "1/4",
                        "1/4",
                        "0"
                    ]
                ]
            },
            "index": {
                "x-optimade-type": "integer",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "integer",
                    "null"
                ],
                "description": "Optional subgroup or cell index associated with the transform."
            },
            "target": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "string",
                    "null"
                ],
                "description": "Optional target identifier whose interpretation is supplied by the parent table."
            },
            "wyckoff_splitting": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "Optional Wyckoff-position splitting metadata associated with the transform.",
                "properties": {}
            }
        },
        "examples": [
            {
                "index": 2,
                "pmat": [
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
                ],
                "pvec": [
                    "0",
                    "0",
                    "0"
                ]
            }
        ]
    },
    "examples": [
        [
            {
                "pmat": [
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
                "pvec": [
                    "0",
                    "0",
                    "0"
                ]
            }
        ]
    ]
}
```