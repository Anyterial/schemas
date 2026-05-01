# Orthogonal affine normalizer (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer.md)**  
**Definition name:** `orthogonal_affine_normalizer`

**Property name:** Orthogonal affine normalizer  
**Description:** Orthogonal affine normalizer coset representatives for one crystallographic space-group setting.
The representatives are listed modulo the space group itself, so each listed operation represents an equivalence class of affine normalizer operations rather than every operation in that class.
This property contains the signed-permutation subset of affine normalizer representatives.  
**Type:** dictionary  

The `candidate_set` field belongs in this property because the listed representatives are produced from a deliberately restricted finite candidate set.
For this property `candidate_set` is `signed_permutation_matrices`, meaning 3 by 3 integer matrices with exactly one nonzero entry in each row and column and each nonzero entry equal to `-1` or `1`.
The plural field `candidate_sets` is not part of the emitted data and MUST NOT be used here.

**Requirements/Conventions**:

- It MUST be a dictionary with the following keys:

    - **normalizer\_kind**: REQUIRED; String.
      Kind label for this normalizer contribution.

    - **representation**: REQUIRED; String.
      Representation label for the listed data.

    - **candidate\_set**: REQUIRED; String.
      Name of the finite linear candidate set used for generation.

    - **n\_symops**: REQUIRED; Integer.
      Number of listed coset representatives after metric-compatibility filtering.

    - **n\_linear\_parts**: REQUIRED; Integer.
      Number of distinct linear matrix parts represented in `symops`.

    - **n\_raw\_candidates**: REQUIRED; Integer.
      Number of affine candidates found before deduplication modulo the space group.

    - **n\_unique\_candidates**: REQUIRED; Integer.
      Number of unique affine candidates before quotienting by the space group.

    - **n\_coset\_representatives**: REQUIRED; Integer.
      Number of non-trivial coset representatives before metric-compatibility filtering.

    - **bounds**: REQUIRED; Dictionary.
      Simple numerical bounds satisfied by the signed-permutation candidate matrices.

    - **symops**: REQUIRED; List of dictionaries.
      Listed orthogonal affine normalizer coset representatives.
      Each item follows `/defs/v0.1/properties/symmetry/normalizer_representative`.

**Examples:**

- `{"normalizer_kind": "orthogonal_affine", "representation": "orthogonal_coset_representatives", "candidate_set": "signed_permutation_matrices", "n_symops": 47, "n_linear_parts": 47, "n_raw_candidates": 48, "n_unique_candidates": 48, "n_coset_representatives": 47, "bounds": {"det_abs": 1, "max_abs_linear_entry": 1}, "symops": [{"xyz": "-x,-y,-z", "rmat": [["-1", "0", "0"], ["0", "-1", "0"], ["0", "0", "-1"]], "tvec": ["0", "0", "0"], "rmat_det": -1, "rmat_is_orthogonal": true, "compatible_systems": ["triclinic", "monoclinic", "orthorhombic", "tetragonal", "trigonal", "hexagonal", "cubic"], "operation_kind": "orthogonal_affine"}]}`

**Formats:** [[JSON](orthogonal_affine_normalizer.json)] [[MD](orthogonal_affine_normalizer.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Orthogonal affine normalizer",
    "$comment": "Anyterial signed-permutation affine normalizer coset representatives for one space-group setting.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "orthogonal_affine_normalizer",
        "label": "orthogonal_affine_normalizer_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Orthogonal affine normalizer coset representatives for one crystallographic space-group setting.\nThe representatives are listed modulo the space group itself, so each listed operation represents an equivalence class of affine normalizer operations rather than every operation in that class.\nThis property contains the signed-permutation subset of affine normalizer representatives.\n\nThe `candidate_set` field belongs in this property because the listed representatives are produced from a deliberately restricted finite candidate set.\nFor this property `candidate_set` is `signed_permutation_matrices`, meaning 3 by 3 integer matrices with exactly one nonzero entry in each row and column and each nonzero entry equal to `-1` or `1`.\nThe plural field `candidate_sets` is not part of the emitted data and MUST NOT be used here.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **normalizer\\_kind**: REQUIRED; String.\n      Kind label for this normalizer contribution.\n\n    - **representation**: REQUIRED; String.\n      Representation label for the listed data.\n\n    - **candidate\\_set**: REQUIRED; String.\n      Name of the finite linear candidate set used for generation.\n\n    - **n\\_symops**: REQUIRED; Integer.\n      Number of listed coset representatives after metric-compatibility filtering.\n\n    - **n\\_linear\\_parts**: REQUIRED; Integer.\n      Number of distinct linear matrix parts represented in `symops`.\n\n    - **n\\_raw\\_candidates**: REQUIRED; Integer.\n      Number of affine candidates found before deduplication modulo the space group.\n\n    - **n\\_unique\\_candidates**: REQUIRED; Integer.\n      Number of unique affine candidates before quotienting by the space group.\n\n    - **n\\_coset\\_representatives**: REQUIRED; Integer.\n      Number of non-trivial coset representatives before metric-compatibility filtering.\n\n    - **bounds**: REQUIRED; Dictionary.\n      Simple numerical bounds satisfied by the signed-permutation candidate matrices.\n\n    - **symops**: REQUIRED; List of dictionaries.\n      Listed orthogonal affine normalizer coset representatives.\n      Each item follows `/defs/v0.1/properties/symmetry/normalizer_representative`.",
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
        "representation": {
            "x-optimade-type": "string",
            "x-optimade-unit": "inapplicable",
            "type": [
                "string",
                "null"
            ],
            "description": "Representation label for the listed normalizer data."
        },
        "candidate_set": {
            "x-optimade-type": "string",
            "x-optimade-unit": "inapplicable",
            "type": [
                "string",
                "null"
            ],
            "description": "Name of the finite linear candidate set used for generation."
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
        "n_raw_candidates": {
            "x-optimade-type": "integer",
            "x-optimade-unit": "inapplicable",
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of affine candidates found before deduplication modulo the space group."
        },
        "n_unique_candidates": {
            "x-optimade-type": "integer",
            "x-optimade-unit": "inapplicable",
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of unique affine candidates before quotienting by the space group."
        },
        "n_coset_representatives": {
            "x-optimade-type": "integer",
            "x-optimade-unit": "inapplicable",
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of non-trivial coset representatives before metric-compatibility filtering."
        },
        "bounds": {
            "x-optimade-type": "dictionary",
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Simple numerical bounds satisfied by the signed-permutation candidate matrices.",
            "properties": {
                "det_abs": {
                    "x-optimade-type": "integer",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "integer",
                        "null"
                    ],
                    "description": "Absolute determinant of every signed-permutation candidate matrix."
                },
                "max_abs_linear_entry": {
                    "x-optimade-type": "integer",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "integer",
                        "null"
                    ],
                    "description": "Maximum absolute entry value in the signed-permutation candidate matrices."
                }
            }
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
            "normalizer_kind": "orthogonal_affine",
            "representation": "orthogonal_coset_representatives",
            "candidate_set": "signed_permutation_matrices",
            "n_symops": 47,
            "n_linear_parts": 47,
            "n_raw_candidates": 48,
            "n_unique_candidates": 48,
            "n_coset_representatives": 47,
            "bounds": {
                "det_abs": 1,
                "max_abs_linear_entry": 1
            },
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
                    "compatible_systems": [
                        "triclinic",
                        "monoclinic",
                        "orthorhombic",
                        "tetragonal",
                        "trigonal",
                        "hexagonal",
                        "cubic"
                    ],
                    "operation_kind": "orthogonal_affine"
                }
            ]
        }
    ]
}
```