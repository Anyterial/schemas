# Euclidean normalizer (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/euclidean_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/euclidean_normalizer.md)**  
**Definition name:** `euclidean_normalizer`

**Property name:** Euclidean normalizer  
**Description:** Finite Euclidean normalizer operations for one crystallographic space-group setting.
The Euclidean normalizer consists of metric-preserving affine operations that normalize the space group in the chosen setting.
These operations are useful for algorithms that need to compare or enumerate equivalent descriptions of the same setting under rigid crystallographic changes of coordinates.  
**Type:** dictionary  

This object is generated from the finite Euclidean normalizer operations exposed by cctbx.
It is not a bounded candidate search table.
Therefore fields such as `candidate_set`, `candidate_sets`, and bounded-search `bounds` do not belong to this property.

**Requirements/Conventions**:

- It MUST be a dictionary with the following keys:

    - **normalizer\_kind**: REQUIRED; String.
      Kind label for this normalizer contribution.
      For this property the value is `euclidean`.

    - **n\_centering\_translations**: REQUIRED; Integer.
      Number of centering translations represented in the underlying Euclidean normalizer operation construction.

    - **n\_pointgroup\_symops**: REQUIRED; Integer.
      Number of point-group symmetry operations represented before centering translations are combined with them.

    - **n\_symops**: REQUIRED; Integer.
      Number of Euclidean normalizer operations listed in `symops`.
      This value MUST equal the length of `symops`.

    - **n\_linear\_parts**: REQUIRED; Integer.
      Number of distinct `rmat` linear matrix parts represented in `symops`.

    - **symops**: REQUIRED; List of dictionaries.
      Finite Euclidean normalizer operations for the setting.
      Each item follows `/defs/v0.1/properties/symmetry/symop`.

**Examples:**

- `{"normalizer_kind": "euclidean", "n_centering_translations": 1, "n_pointgroup_symops": 1, "n_symops": 2, "n_linear_parts": 2, "symops": [{"xyz": "-x,-y,-z", "rmat": [["-1", "0", "0"], ["0", "-1", "0"], ["0", "0", "-1"]], "tvec": ["0", "0", "0"], "rmat_det": -1, "rmat_is_orthogonal": true, "rot_type": "-1", "sense": 0, "axis": [0, 0, 0], "screw_glide": ["0", "0", "0"], "origin_shift": ["0", "0", "0"], "operation_kind": "euclidean"}]}`

**Formats:** [[JSON](euclidean_normalizer.json)] [[MD](euclidean_normalizer.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/euclidean_normalizer",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Euclidean normalizer",
    "$comment": "Anyterial finite Euclidean normalizer operation data for one space-group setting.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "euclidean_normalizer",
        "label": "euclidean_normalizer_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Finite Euclidean normalizer operations for one crystallographic space-group setting.\nThe Euclidean normalizer consists of metric-preserving affine operations that normalize the space group in the chosen setting.\nThese operations are useful for algorithms that need to compare or enumerate equivalent descriptions of the same setting under rigid crystallographic changes of coordinates.\n\nThis object is generated from the finite Euclidean normalizer operations exposed by cctbx.\nIt is not a bounded candidate search table.\nTherefore fields such as `candidate_set`, `candidate_sets`, and bounded-search `bounds` do not belong to this property.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **normalizer\\_kind**: REQUIRED; String.\n      Kind label for this normalizer contribution.\n      For this property the value is `euclidean`.\n\n    - **n\\_centering\\_translations**: REQUIRED; Integer.\n      Number of centering translations represented in the underlying Euclidean normalizer operation construction.\n\n    - **n\\_pointgroup\\_symops**: REQUIRED; Integer.\n      Number of point-group symmetry operations represented before centering translations are combined with them.\n\n    - **n\\_symops**: REQUIRED; Integer.\n      Number of Euclidean normalizer operations listed in `symops`.\n      This value MUST equal the length of `symops`.\n\n    - **n\\_linear\\_parts**: REQUIRED; Integer.\n      Number of distinct `rmat` linear matrix parts represented in `symops`.\n\n    - **symops**: REQUIRED; List of dictionaries.\n      Finite Euclidean normalizer operations for the setting.\n      Each item follows `/defs/v0.1/properties/symmetry/symop`.",
    "properties": {
        "normalizer_kind": {
            "x-optimade-type": "string",
            "x-optimade-unit": "inapplicable",
            "type": [
                "string",
                "null"
            ],
            "description": "Kind label for this normalizer contribution."
        },
        "n_centering_translations": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_centering_translations",
            "title": "N Centering Translations",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_centering_translations",
                "label": "n_centering_translations_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of centering translations in the conventional cell of the space-group setting.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                1,
                2
            ]
        },
        "n_pointgroup_symops": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_pointgroup_symops",
            "title": "N Pointgroup Symops",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_pointgroup_symops",
                "label": "n_pointgroup_symops_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of point-group symmetry operations represented by the space group, excluding centering translations.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                1,
                2
            ]
        },
        "n_symops": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops",
            "title": "N Symops",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_symops",
                "label": "n_symops_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of symmetry operations in the finite operation list of the generated entry.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                1,
                2
            ]
        },
        "n_linear_parts": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_linear_parts",
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
        },
        "symops": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops",
            "title": "Symmetry operations",
            "$comment": "Anyterial property definition using the common reusable symop object definition.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "symops",
                "label": "symops_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Full list of symmetry-operation descriptors for a space-group setting.\nEach list member is a `symop` object as defined by `/properties/symmetry/symop`.\nFor space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST follow the schema inherited from `/properties/symmetry/symop`.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/symop",
                "title": "Symmetry operation",
                "$comment": "Reusable Anyterial source definition for one crystallographic symmetry-operation descriptor used inside point-group and space-group operation lists.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "symop",
                    "label": "symop_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "A single crystallographic symmetry-operation descriptor.\nSpace-group operation lists currently store the operation type, axis, sense, and screw/glide decomposition.\nPoint-group operation lists currently store the full integer operation matrix under the legacy key `matrix` together with an integer operation-type code under `type`.\nFuture generated data may also use the semantic `rmat` key for the linear matrix part.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rot\\_type**: OPTIONAL; String.\n      Crystallographic operation-type label for the linear part, such as `1`, `-1`, `2`, `m`, `-3`, `4`, `-4`, `6`, or `-6`.\n      This is the preferred symbolic operation-type field in space-group operation descriptors.\n\n    - **type**: OPTIONAL; Integer.\n      Legacy numeric operation-type code used by point-group operation descriptors.\n\n    - **axis**: OPTIONAL; List of 3 Integers.\n      Operation axis or invariant direction using the integer-vector convention returned by the generator.\n\n    - **sense**: OPTIONAL; Integer.\n      Rotation sense/sign convention returned by the generator; `0` is used when no handed rotation sense is applicable.\n\n    - **screw\\_glide**: OPTIONAL; List of 3 Fractions (String).\n      Screw-axis or glide-plane component associated with a space-group affine operation.\n\n    - **origin\\_shift**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift associated with the screw/glide decomposition of a space-group affine operation.\n\n    - **matrix**: OPTIONAL; Integer 3x3 matrix.\n      Legacy full point-group operation matrix.\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Semantic linear matrix part of an affine operation when emitted by a parent table.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the operation in `x,y,z` notation when available.\n\n    - **is\\_proper**: OPTIONAL; Boolean.\n      States whether the linear operation is proper, i.e., whether its determinant is +1.",
                "properties": {
                    "rot_type": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Symbolic crystallographic operation-type label for the linear part."
                    },
                    "type": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Legacy numeric point-group operation-type code."
                    },
                    "axis": {
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
                        "description": "Integer-vector axis or invariant-direction descriptor for the operation.",
                        "items": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer"
                            ],
                            "description": "One integer component of the axis vector."
                        }
                    },
                    "sense": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Rotation sense/sign convention returned by the generator."
                    },
                    "screw_glide": {
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
                        "description": "Screw-axis or glide-plane component represented exactly as a list of fraction strings.",
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
                    "origin_shift": {
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
                        "description": "Origin-shift descriptor represented exactly as a list of fraction strings.",
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
                        "description": "Legacy integer 3 by 3 operation matrix used by point-group symops.",
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
                            "description": "One row of the integer operation matrix.",
                            "items": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "dimensionless",
                                "type": [
                                    "integer"
                                ],
                                "description": "One integer matrix entry."
                            }
                        }
                    },
                    "rmat": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/rmat",
                        "title": "Symmetry operation linear matrix",
                        "$comment": "Reusable Anyterial definition for the linear part of a same-setting affine operation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "rmat",
                            "label": "rmat_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Linear matrix part of a same-setting affine operation acting on fractional coordinates.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings in transformation tables because affine-normalizer candidates may be generated and serialized through exact arithmetic.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- For point-group operation matrices that are emitted as integers under the legacy key `matrix`, the parent property describes that separate shape.",
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
                            "description": "One row of the 3 by 3 operation matrix.",
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
                            ]
                        ]
                    },
                    "xyz": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Operation in `x,y,z` coordinate notation."
                    },
                    "is_proper": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether the linear operation is proper."
                    }
                },
                "examples": [
                    {
                        "rot_type": "2",
                        "sense": 0,
                        "axis": [
                            0,
                            1,
                            0
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    },
                    {
                        "matrix": [
                            [
                                1,
                                0,
                                0
                            ],
                            [
                                0,
                                1,
                                0
                            ],
                            [
                                0,
                                0,
                                1
                            ]
                        ],
                        "xyz": "x,y,z",
                        "type": 1,
                        "is_proper": true,
                        "axis": [
                            0,
                            0,
                            0
                        ],
                        "sense": 0
                    }
                ]
            },
            "examples": [
                [
                    {
                        "rot_type": "1",
                        "sense": 0,
                        "axis": [
                            0,
                            0,
                            0
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            ]
        }
    },
    "examples": [
        {
            "normalizer_kind": "euclidean",
            "n_centering_translations": 1,
            "n_pointgroup_symops": 1,
            "n_symops": 2,
            "n_linear_parts": 2,
            "symops": [
                {
                    "xyz": "-x,-y,-z",
                    "rmat": [
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
                            "-1"
                        ]
                    ],
                    "tvec": [
                        "0",
                        "0",
                        "0"
                    ],
                    "rmat_det": -1,
                    "rmat_is_orthogonal": true,
                    "rot_type": "-1",
                    "sense": 0,
                    "axis": [
                        0,
                        0,
                        0
                    ],
                    "screw_glide": [
                        "0",
                        "0",
                        "0"
                    ],
                    "origin_shift": [
                        "0",
                        "0",
                        "0"
                    ],
                    "operation_kind": "euclidean"
                }
            ]
        }
    ]
}
```