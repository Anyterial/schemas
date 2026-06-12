# Orthogonal affine normalizer (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/orthogonal_affine_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/orthogonal_affine_normalizer.md)**  
**Definition name:** `orthogonal_affine_normalizer`

**Property name:** Orthogonal affine normalizer  
**Description:** Orthogonal affine normalizer coset representatives for one crystallographic space-group setting.  
**Type:** dictionary  

The representatives are listed modulo the space group itself, so each listed operation represents an equivalence class of affine normalizer operations rather than every operation in that class.
This property contains the signed-permutation subset of affine normalizer representatives.

The `candidate_set` field belongs in this property because the listed representatives are produced from a deliberately restricted finite candidate set.
For this property `candidate_set` is `signed_permutation_matrices`, meaning 3 by 3 integer matrices with exactly one nonzero entry in each row and column and each nonzero entry equal to `-1` or `1`.
The plural field `candidate_sets` is not part of the emitted data and MUST NOT be used here.

This property is one of three related normalizer tables for a setting:
`euclidean_normalizer` holds the finite Euclidean normalizer operations obtained from cctbx,
this property holds the older bounded table restricted to signed-permutation linear parts,
and `affine_normalizer` holds the bounded table generated from unimodular integer linear parts, which is a superset of this one.

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
      Each item follows `/defs/v0.1/properties/symmetry/basis_transform`.
      Each item MUST carry `compatible_systems`, the list of crystal systems for which the representative's linear part is compatible with a crystallographic metric.

**Examples:**

- `{"normalizer_kind": "orthogonal_affine", "representation": "orthogonal_coset_representatives", "candidate_set": "signed_permutation_matrices", "n_symops": 47, "n_linear_parts": 47, "n_raw_candidates": 48, "n_unique_candidates": 48, "n_coset_representatives": 47, "bounds": {"det_abs": 1, "max_abs_linear_entry": 1}, "symops": [{"affine_transformation": {"xyz": "-x,-y,-z", "matrix": [["-1", "0", "0"], ["0", "-1", "0"], ["0", "0", "-1"]], "vector": ["0", "0", "0"], "det": -1, "is_orthogonal": true}, "compatible_systems": ["triclinic", "monoclinic", "orthorhombic", "tetragonal", "trigonal", "hexagonal", "cubic"], "operation_kind": "orthogonal_affine"}]}`

**Formats:** [[JSON](orthogonal_affine_normalizer.json)] [[MD](orthogonal_affine_normalizer.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/transformations/orthogonal_affine_normalizer",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Orthogonal affine normalizer",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "orthogonal_affine_normalizer",
        "label": "orthogonal_affine_normalizer_transformations"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Orthogonal affine normalizer coset representatives for one crystallographic space-group setting.\n\nThe representatives are listed modulo the space group itself, so each listed operation represents an equivalence class of affine normalizer operations rather than every operation in that class.\nThis property contains the signed-permutation subset of affine normalizer representatives.\n\nThe `candidate_set` field belongs in this property because the listed representatives are produced from a deliberately restricted finite candidate set.\nFor this property `candidate_set` is `signed_permutation_matrices`, meaning 3 by 3 integer matrices with exactly one nonzero entry in each row and column and each nonzero entry equal to `-1` or `1`.\nThe plural field `candidate_sets` is not part of the emitted data and MUST NOT be used here.\n\nThis property is one of three related normalizer tables for a setting:\n`euclidean_normalizer` holds the finite Euclidean normalizer operations obtained from cctbx,\nthis property holds the older bounded table restricted to signed-permutation linear parts,\nand `affine_normalizer` holds the bounded table generated from unimodular integer linear parts, which is a superset of this one.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **normalizer\\_kind**: REQUIRED; String.\n      Kind label for this normalizer contribution.\n\n    - **representation**: REQUIRED; String.\n      Representation label for the listed data.\n\n    - **candidate\\_set**: REQUIRED; String.\n      Name of the finite linear candidate set used for generation.\n\n    - **n\\_symops**: REQUIRED; Integer.\n      Number of listed coset representatives after metric-compatibility filtering.\n\n    - **n\\_linear\\_parts**: REQUIRED; Integer.\n      Number of distinct linear matrix parts represented in `symops`.\n\n    - **n\\_raw\\_candidates**: REQUIRED; Integer.\n      Number of affine candidates found before deduplication modulo the space group.\n\n    - **n\\_unique\\_candidates**: REQUIRED; Integer.\n      Number of unique affine candidates before quotienting by the space group.\n\n    - **n\\_coset\\_representatives**: REQUIRED; Integer.\n      Number of non-trivial coset representatives before metric-compatibility filtering.\n\n    - **bounds**: REQUIRED; Dictionary.\n      Simple numerical bounds satisfied by the signed-permutation candidate matrices.\n\n    - **symops**: REQUIRED; List of dictionaries.\n      Listed orthogonal affine normalizer coset representatives.\n      Each item follows `/defs/v0.1/properties/symmetry/basis_transform`.\n      Each item MUST carry `compatible_systems`, the list of crystal systems for which the representative's linear part is compatible with a crystallographic metric.",
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
            "title": "Number of symops",
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
            "description": "Number of symmetry operations in the finite operation list of the generated entry.\n\nWhen the entry contains a `symops` list, this value MUST equal its length.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                1,
                2
            ]
        },
        "n_linear_parts": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_linear_parts",
            "title": "Number of linear parts",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_linear_parts",
                "label": "n_linear_parts_transformations"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of distinct linear matrix parts represented in a normalizer or transform table.\n\nDistinctness is determined by exact element-wise comparison of the 3 by 3 matrix parts of the listed operations.",
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
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Listed orthogonal affine normalizer coset representatives.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/basis_transform",
                "title": "Basis transformation",
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
                "description": "One crystallographic transform between coordinate descriptions, settings, cells, or related group embeddings.\n\nThe affine map itself is stored in the embedded `affine_transformation` field.\nThe parent property defines the source and target coordinate systems and the precise role of the transform.\nUseful, for example, for representing setting changes, subgroup embeddings, isomorphic subgroup transforms, normalizer representatives, and same-space-group affine images.\nThis property is not limited to symmetry operations within one fixed setting; the matrix may be non-orthogonal or have determinant different from one when the transform changes cell or basis.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **affine\\_transformation**: REQUIRED; Dictionary.\n      Exact affine map for the transform, using exact rational matrix and vector entries.\n      The coordinate convention and source/target interpretation are supplied by the parent property.\n\n    - **index**: OPTIONAL; Integer or null.\n      Index metadata whose interpretation is defined by the parent property.\n      Common uses include the subgroup index for subgroup embeddings, the cell index for isomorphic subgroup transforms, or an ordinal representative index in a finite transform table.\n\n    - **subgroup\\_type**: OPTIONAL; String.\n      International Tables subgroup-type label when the transform describes a maximal subgroup embedding.\n      The value MUST be `t` for a translationengleiche subgroup or `k` for a klassengleiche subgroup.\n      It MUST be omitted when the transform is not a maximal subgroup embedding.\n\n    - **k\\_subtype**: OPTIONAL; String or null.\n      Klassengleiche subtype when the transform describes a klassengleiche subgroup relation.\n      The value MUST be `loss_of_centering_translation` or `enlarged_unit_cell` for klassengleiche relations and null or omitted otherwise.\n\n    - **compatible\\_systems**: OPTIONAL; List of strings.\n      Crystal metric systems for which the transform is compatible.\n      This is used for bounded affine normalizer representatives.\n\n    - **operation\\_kind**: OPTIONAL; String.\n      Categorical label for normalizer-type representatives.\n      The value MUST be `euclidean` for Euclidean normalizer operations, `orthogonal_affine` for the signed-permutation affine normalizer subset, or `affine` for the bounded unimodular affine normalizer table.\n      It MUST be omitted when the transform is a setting transform, subgroup embedding, or other transform for which no normalizer operation class applies.\n\n    - **wyckoff\\_splitting**: OPTIONAL; List.\n      Wyckoff-position splitting metadata induced by the transform when available.\n      The list is grouped by explicit parent Wyckoff letter.\n\n    - **criteria**: OPTIONAL; List.\n      Backward-lift constraint metadata induced by the transform when available.\n      The list is grouped by explicit parent Wyckoff letter.",
                "properties": {
                    "affine_transformation": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation",
                        "title": "Affine transformation",
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
                        "description": "An affine transformation acting on fractional crystallographic coordinates.\n\nAn affine transformation is a geometric transformation preserving points, straight lines, and parallelism (collinearity), but may not preserve Euclidean distances and angles.\nThe transformation is represented by a 3 by 3 matrix and a 3-vector, both serialized with exact string entries.\nThe transformation may, for example, represent an operation within one setting, a setting transform, a subgroup embedding, a normalizer representative, or a parametric coordinate map for a Wyckoff-position orbit representative.\nWhen used as a parametric coordinate map, the matrix may be singular because special Wyckoff positions can constrain or identify parameters.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **matrix**: REQUIRED; Exact 3x3 matrix.\n      Matrix part of the affine transformation.\n      It MUST be represented as a list of three row lists, each containing three exact rational entries represented as strings.\n\n    - **vector**: REQUIRED; List of 3 Fractions (String).\n      Translation or origin-shift vector of the affine transformation in fractional coordinates.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the affine transformation in `x,y,z` notation when available.\n\n    - **det**: OPTIONAL; Integer.\n      Determinant of `matrix` when the generator emits it.\n\n    - **is\\_orthogonal**: OPTIONAL; Boolean.\n      Whether `matrix` is orthogonal in the exact representation used by the generator.",
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
                                        "title": "Fraction",
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
                                        "description": "A numerical representation formed as the quotient of two numbers represented as a string.",
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
                                    "title": "Fraction",
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
                                    "description": "A numerical representation formed as the quotient of two numbers represented as a string.",
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
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op_xyz",
                                "title": "Operation xyz",
                                "x-optimade-type": "string",
                                "x-compatibility": [
                                    "https://schemas.optimade.org/defs/v1.2/properties/optimade/common/symmetry_operation_xyz",
                                    "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group_symop.operation_xyz.html"
                                ],
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "op_xyz",
                                    "label": "op_xyz_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate operation expressed in the algebraic xyz form, also known as Jones' faithful representation (Bradley & Cracknell, 1972: pp. 35-37; adapted for computer strings).\n\nThe following definition is adapted from (and meant to be compatible with) the IUCr symCIF version 1.0.1 dictionary definition of `_space_group_symop.operation_xyz` referenced to: International Tables for Crystallography (2002). Volume A, Space-group symmetry, edited by Th. Hahn, 5th. ed. (Kluwer Academic Publishers).\nIt is available at: https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group_symop.operation_xyz.html\n\nIf W is a matrix representation of the rotational part of the symmetry operation defined by the positions and signs of x, y and z, and w is a column of translations defined by the fractions, an equivalent position X' is generated from a given position X by the equation: X' = WX + w.",
                                "x-undef-pattern": "^([-+]?[xyz]([-+][xyz])?([-+](1/2|[12]/3|[1-3]/4|[1-5]/6))?|[-+]?(1/2|[12]/3|[1-3]/4|[1-5]/6)([-+][xyz]([-+][xyz])?)?),([-+]?[xyz]([-+][xyz])?([-+](1/2|[12]/3|[1-3]/4|[1-5]/6))?|[-+]?(1/2|[12]/3|[1-3]/4|[1-5]/6)([-+][xyz]([-+][xyz])?)?),([-+]?[xyz]([-+][xyz])?([-+](1/2|[12]/3|[1-3]/4|[1-5]/6))?|[-+]?(1/2|[12]/3|[1-3]/4|[1-5]/6)([-+][xyz]([-+][xyz])?)?)$",
                                "examples": [
                                    "-x,-y,z",
                                    "x,1/2-y,1/2+z"
                                ]
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
                            "string"
                        ],
                        "description": "International Tables subgroup-type label when applicable.",
                        "enum": [
                            "t",
                            "k"
                        ]
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
                    "compatible_systems": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Crystal metric systems compatible with the transform.",
                        "items": {
                            "x-optimade-type": "string",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "string"
                            ],
                            "description": "One compatible crystal-system label.",
                            "enum": [
                                "triclinic",
                                "monoclinic",
                                "orthorhombic",
                                "tetragonal",
                                "trigonal",
                                "hexagonal",
                                "cubic"
                            ]
                        }
                    },
                    "operation_kind": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "description": "Categorical label for normalizer-type representatives.",
                        "enum": [
                            "euclidean",
                            "orthogonal_affine",
                            "affine"
                        ]
                    },
                    "wyckoff_splitting": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/transformations/wyckoff_splitting",
                        "title": "Wyckoff splitting",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "wyckoff_splitting",
                            "label": "wyckoff_splitting_transformations"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Wyckoff-position splitting data associated with a subgroup or same-space-group transform.\n\nEach list item gives the split of one parent Wyckoff position.\nThe parent Wyckoff letter is stored in the `parent` field rather than as a JSON dictionary key.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST contain `parent`, the Wyckoff letter in the parent setting.\n- Each dictionary MUST contain `splits`, an ordered list of subgroup Wyckoff-position assignments or coordinate expressions emitted by the generator.",
                        "items": {
                            "x-optimade-type": "dictionary",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "object"
                            ],
                            "description": "Splitting data for one parent Wyckoff position.",
                            "required": [
                                "parent",
                                "splits"
                            ],
                            "properties": {
                                "parent": {
                                    "x-optimade-type": "string",
                                    "x-optimade-unit": "inapplicable",
                                    "type": [
                                        "string"
                                    ],
                                    "description": "Parent Wyckoff letter."
                                },
                                "splits": {
                                    "x-optimade-type": "list",
                                    "x-optimade-unit": "inapplicable",
                                    "type": [
                                        "array"
                                    ],
                                    "description": "Ordered split records for this parent Wyckoff letter.",
                                    "items": {
                                        "x-optimade-type": "dictionary",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "object"
                                        ],
                                        "description": "One Wyckoff split record.",
                                        "required": [
                                            "letter",
                                            "xyz",
                                            "affine"
                                        ],
                                        "properties": {
                                            "letter": {
                                                "x-optimade-type": "string",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "string"
                                                ],
                                                "description": "Subgroup Wyckoff letter assigned by this split branch."
                                            },
                                            "xyz": {
                                                "x-optimade-type": "string",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "string"
                                                ],
                                                "description": "Coordinate expression for the split branch."
                                            },
                                            "affine": {
                                                "x-optimade-type": "list",
                                                "x-optimade-unit": "inapplicable",
                                                "x-optimade-dimensions": {
                                                    "names": [
                                                        "dim_lattice",
                                                        "dim_affine"
                                                    ],
                                                    "sizes": [
                                                        3,
                                                        4
                                                    ]
                                                },
                                                "type": [
                                                    "array"
                                                ],
                                                "description": "Exact affine representation for the split branch as a 3 by 4 augmented matrix.\nEach row holds the three linear coefficients followed by the translation component, all as exact fraction strings.",
                                                "items": {
                                                    "x-optimade-type": "list",
                                                    "x-optimade-unit": "inapplicable",
                                                    "x-optimade-dimensions": {
                                                        "names": [
                                                            "dim_affine"
                                                        ],
                                                        "sizes": [
                                                            4
                                                        ]
                                                    },
                                                    "type": [
                                                        "array"
                                                    ],
                                                    "description": "One row of the augmented affine matrix.",
                                                    "items": {
                                                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                                        "title": "Fraction",
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
                                                        "description": "A numerical representation formed as the quotient of two numbers represented as a string.",
                                                        "examples": [
                                                            "2/3",
                                                            "5/42",
                                                            "10",
                                                            "0"
                                                        ],
                                                        "x-optimade-unit": "inapplicable"
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        },
                        "examples": [
                            [
                                {
                                    "parent": "c",
                                    "splits": [
                                        {
                                            "letter": "e",
                                            "xyz": "x,y,z",
                                            "affine": [
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
                                                    "1",
                                                    "0"
                                                ]
                                            ]
                                        }
                                    ]
                                }
                            ]
                        ]
                    },
                    "criteria": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Backward-lift constraint metadata induced by the transform, grouped by explicit parent Wyckoff letter.",
                        "items": {
                            "x-optimade-type": "dictionary",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "object"
                            ],
                            "description": "Backward-lift constraints for one parent Wyckoff position.",
                            "required": [
                                "parent",
                                "constraints"
                            ],
                            "properties": {
                                "parent": {
                                    "x-optimade-type": "string",
                                    "x-optimade-unit": "inapplicable",
                                    "type": [
                                        "string"
                                    ],
                                    "description": "Parent Wyckoff letter."
                                },
                                "constraints": {
                                    "x-optimade-type": "list",
                                    "x-optimade-unit": "inapplicable",
                                    "type": [
                                        "array"
                                    ],
                                    "description": "Constraint records for this parent Wyckoff letter.",
                                    "items": {
                                        "x-optimade-type": "dictionary",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "object"
                                        ],
                                        "description": "One linear backward-lift constraint record.",
                                        "properties": {
                                            "roles": {
                                                "x-optimade-type": "list",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "array"
                                                ],
                                                "description": "Wyckoff-position role references entering the constraint.",
                                                "items": {
                                                    "x-optimade-type": "dictionary",
                                                    "x-optimade-unit": "inapplicable",
                                                    "type": [
                                                        "object"
                                                    ],
                                                    "description": "One role reference.",
                                                    "required": [
                                                        "letter",
                                                        "index"
                                                    ],
                                                    "properties": {
                                                        "letter": {
                                                            "x-optimade-type": "string",
                                                            "x-optimade-unit": "inapplicable",
                                                            "type": [
                                                                "string"
                                                            ],
                                                            "description": "Wyckoff letter for the referenced role."
                                                        },
                                                        "index": {
                                                            "x-optimade-type": "integer",
                                                            "x-optimade-unit": "inapplicable",
                                                            "type": [
                                                                "integer"
                                                            ],
                                                            "description": "Zero-based occurrence index for the role."
                                                        }
                                                    }
                                                }
                                            },
                                            "coeffs": {
                                                "x-optimade-type": "list",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "array"
                                                ],
                                                "description": "Exact coefficient vectors for the constraint.",
                                                "items": {
                                                    "x-optimade-type": "list",
                                                    "x-optimade-unit": "inapplicable",
                                                    "type": [
                                                        "array"
                                                    ],
                                                    "description": "Coefficients associated with one role.",
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
                                                        "description": "One exact coefficient vector.",
                                                        "items": {
                                                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                                            "title": "Fraction",
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
                                                            "description": "A numerical representation formed as the quotient of two numbers represented as a string.",
                                                            "examples": [
                                                                "2/3",
                                                                "5/42",
                                                                "10",
                                                                "0"
                                                            ],
                                                            "x-optimade-unit": "inapplicable"
                                                        }
                                                    }
                                                }
                                            },
                                            "target": {
                                                "x-optimade-type": "list",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "array"
                                                ],
                                                "description": "Exact target vector or scalar for the constraint.",
                                                "items": {
                                                    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                                    "title": "Fraction",
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
                                                    "description": "A numerical representation formed as the quotient of two numbers represented as a string.",
                                                    "examples": [
                                                        "2/3",
                                                        "5/42",
                                                        "10",
                                                        "0"
                                                    ],
                                                    "x-optimade-unit": "inapplicable"
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                },
                "examples": [
                    {
                        "affine_transformation": {
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
                            ],
                            "xyz": "x,y,2z",
                            "det": 2,
                            "is_orthogonal": false
                        },
                        "index": 2,
                        "subgroup_type": "k",
                        "k_subtype": "enlarged_unit_cell",
                        "wyckoff_splitting": [
                            {
                                "parent": "a",
                                "splits": [
                                    {
                                        "letter": "a",
                                        "xyz": "x,y,z",
                                        "affine": [
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
                                                "1",
                                                "0"
                                            ]
                                        ]
                                    }
                                ]
                            }
                        ],
                        "criteria": [
                            {
                                "parent": "a",
                                "constraints": [
                                    {
                                        "roles": [
                                            {
                                                "letter": "a",
                                                "index": 0
                                            }
                                        ],
                                        "coeffs": [
                                            [
                                                [
                                                    "1",
                                                    "0",
                                                    "0"
                                                ]
                                            ]
                                        ],
                                        "target": [
                                            "0"
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "affine_transformation": {
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
                                    "-1"
                                ]
                            ],
                            "vector": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "-x,-y,-z",
                            "det": -1,
                            "is_orthogonal": true
                        },
                        "compatible_systems": [
                            "triclinic",
                            "monoclinic",
                            "orthorhombic",
                            "tetragonal",
                            "trigonal",
                            "hexagonal",
                            "cubic"
                        ],
                        "operation_kind": "affine"
                    }
                ]
            }
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
                    "affine_transformation": {
                        "xyz": "-x,-y,-z",
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
                                "-1"
                            ]
                        ],
                        "vector": [
                            "0",
                            "0",
                            "0"
                        ],
                        "det": -1,
                        "is_orthogonal": true
                    },
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