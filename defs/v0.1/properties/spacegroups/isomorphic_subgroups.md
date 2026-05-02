# Isomorphic subgroup transforms (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups.md)**  
**Definition name:** `isomorphic_subgroups`

**Property name:** Isomorphic subgroup transforms  
**Description:** Isomorphic subgroup transforms of bounded index for one parent setting or space-group type.
An isomorphic subgroup has the same space-group type as the parent but is embedded with a finite index, usually corresponding to an enlarged unit cell or a sublattice choice.
These transforms are useful for algorithms that need to enumerate same-type subgroup embeddings, compare structures under supercell changes, or construct bounded same-space-group refinement paths.  
**Type:** dictionary  

The transform records use the basis-transform convention represented by `matrix` and `vector`.
The `index` field is the subgroup index and equals the determinant factor of the basis transformation.
The generator currently searches indices up to its configured maximum index and deduplicates equivalent transforms under normalizer equivalence.

**Requirements/Conventions**:

- It MUST be a dictionary containing an `items` list.
- Each item in `items` MUST describe one exact isomorphic subgroup transform.
- Matrix and vector entries MUST be exact strings, using integer strings or fraction strings as appropriate.

**Examples:**

- `{"items": [{"index": 2, "wyckoff_splitting": {"a": [["a", "x,y,z", [["1", "0", "0", "0"], ["0", "1", "0", "0"], ["0", "0", "1/2", "1/2"]]], ["a", "x,y,z", [["1", "0", "0", "0"], ["0", "1", "0", "0"], ["0", "0", "1/2", "0"]]]]}, "matrix": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "2"]], "vector": ["0", "0", "0"]}]}`

**Formats:** [[JSON](isomorphic_subgroups.json)] [[MD](isomorphic_subgroups.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Isomorphic subgroup transforms",
    "$comment": "Anyterial keyed table of bounded-index isomorphic subgroup transforms.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "isomorphic_subgroups",
        "label": "isomorphic_subgroups_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Isomorphic subgroup transforms of bounded index for one parent setting or space-group type.\nAn isomorphic subgroup has the same space-group type as the parent but is embedded with a finite index, usually corresponding to an enlarged unit cell or a sublattice choice.\nThese transforms are useful for algorithms that need to enumerate same-type subgroup embeddings, compare structures under supercell changes, or construct bounded same-space-group refinement paths.\n\nThe transform records use the basis-transform convention represented by `matrix` and `vector`.\nThe `index` field is the subgroup index and equals the determinant factor of the basis transformation.\nThe generator currently searches indices up to its configured maximum index and deduplicates equivalent transforms under normalizer equivalence.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary containing an `items` list.\n- Each item in `items` MUST describe one exact isomorphic subgroup transform.\n- Matrix and vector entries MUST be exact strings, using integer strings or fraction strings as appropriate.",
    "properties": {
        "items": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Isomorphic subgroup transform records for one parent key.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation",
                "title": "Affine transformation",
                "$comment": "Reusable Anyterial definition for one exact crystallographic affine transformation record.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "affine_transformation",
                    "label": "affine_transformation_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One exact affine transformation acting on fractional crystallographic coordinates.\nThe transformation core is represented by a 3 by 3 matrix and a 3-vector, both serialized with exact string entries.\nParent properties define the coordinate convention and semantic role of the transformation, for example whether it is a setting transform, a subgroup embedding, a same-space-group image, or a normalizer representative.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **matrix**: REQUIRED; Exact 3x3 matrix.\n      Matrix part of the affine transformation.\n      It MUST be represented as a list of three row lists, each containing three exact rational entries represented as strings.\n\n    - **vector**: REQUIRED; List of 3 Fractions (String).\n      Translation or origin-shift vector of the affine transformation in fractional coordinates.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the affine transformation in `x,y,z` notation when available.\n\n    - **det**: OPTIONAL; Integer.\n      Determinant of `matrix` when the generator emits it.\n\n    - **is\\_orthogonal**: OPTIONAL; Boolean.\n      Whether `matrix` is orthogonal in the exact representation used by the generator.\n\n    - **compatible\\_systems**: OPTIONAL; List of strings.\n      Crystal metric systems for which the transformation is compatible.\n      This is used for bounded affine normalizer representatives.\n\n    - **operation\\_kind**: OPTIONAL; String.\n      Generator classification of the operation or representative.\n\n    - **index**: OPTIONAL; Integer.\n      Subgroup index, same-setting transform index, or other index metadata whose interpretation is defined by the parent property.\n\n    - **subgroup\\_type**: OPTIONAL; String.\n      International Tables subgroup-type label when the transformation describes a subgroup embedding.\n\n    - **k\\_subtype**: OPTIONAL; String or null.\n      Klassengleiche subtype when the transformation describes a klassengleiche subgroup relation.\n\n    - **wyckoff\\_splitting**: OPTIONAL; Dictionary.\n      Wyckoff-position splitting metadata induced by the transformation when available.\n\n    - **criteria**: OPTIONAL; Dictionary.\n      Backward-lift constraint metadata induced by the transformation when available.",
                "properties": {
                    "matrix": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
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
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Exact 3 by 3 matrix part of the affine transformation.",
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
                            "description": "One row of the exact 3 by 3 matrix.",
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
                            }
                        }
                    },
                    "vector": {
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
                            "array",
                            "null"
                        ],
                        "description": "Exact fractional-coordinate vector part of the affine transformation.",
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
                        }
                    },
                    "xyz": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Coordinate expression for the affine transformation in `x,y,z` notation."
                    },
                    "det": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Determinant of the matrix part when emitted by the generator."
                    },
                    "is_orthogonal": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether the matrix part is orthogonal."
                    },
                    "compatible_systems": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Crystal metric systems compatible with the transformation.",
                        "items": {
                            "x-optimade-type": "string",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "string"
                            ],
                            "description": "One compatible crystal-system label."
                        }
                    },
                    "operation_kind": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Generator classification of the operation or representative."
                    },
                    "index": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Index metadata whose interpretation is supplied by the parent property."
                    },
                    "subgroup_type": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "International Tables subgroup-type label when applicable."
                    },
                    "k_subtype": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Klassengleiche subtype when applicable."
                    },
                    "wyckoff_splitting": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Wyckoff-position splitting metadata induced by the transformation.",
                        "properties": {}
                    },
                    "criteria": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Backward-lift constraint metadata induced by the transformation.",
                        "properties": {}
                    }
                },
                "examples": [
                    {
                        "matrix": [
                            [
                                "-1",
                                "0",
                                "0"
                            ],
                            [
                                "0",
                                "-1",
                                "0"
                            ],
                            [
                                "0",
                                "0",
                                "1"
                            ]
                        ],
                        "vector": [
                            "0",
                            "0",
                            "0"
                        ],
                        "xyz": "-x,-y,z",
                        "det": 1,
                        "is_orthogonal": true
                    }
                ]
            }
        }
    },
    "examples": [
        {
            "items": [
                {
                    "index": 2,
                    "wyckoff_splitting": {
                        "a": [
                            [
                                "a",
                                "x,y,z",
                                [
                                    [
                                        "1",
                                        "0",
                                        "0",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "1",
                                        "0",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "0",
                                        "1/2",
                                        "1/2"
                                    ]
                                ]
                            ],
                            [
                                "a",
                                "x,y,z",
                                [
                                    [
                                        "1",
                                        "0",
                                        "0",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "1",
                                        "0",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "0",
                                        "1/2",
                                        "0"
                                    ]
                                ]
                            ]
                        ]
                    },
                    "matrix": [
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
                    "vector": [
                        "0",
                        "0",
                        "0"
                    ]
                }
            ]
        }
    ]
}
```