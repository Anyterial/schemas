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
      Number of distinct linear matrix parts represented in `symops`.

    - **symops**: REQUIRED; List of dictionaries.
      Finite Euclidean normalizer operations for the setting.
      Each item follows `/defs/v0.1/properties/symmetry/affine_transformation`.

**Examples:**

- `{"normalizer_kind": "euclidean", "n_centering_translations": 1, "n_pointgroup_symops": 1, "n_symops": 2, "n_linear_parts": 2, "symops": [{"xyz": "-x,-y,-z", "matrix": [["-1", "0", "0"], ["0", "-1", "0"], ["0", "0", "-1"]], "vector": ["0", "0", "0"], "det": -1, "is_orthogonal": true, "rot_type": "-1", "sense": 0, "axis": [0, 0, 0], "screw_glide": ["0", "0", "0"], "origin_shift": ["0", "0", "0"], "operation_kind": "euclidean"}]}`

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
    "description": "Finite Euclidean normalizer operations for one crystallographic space-group setting.\nThe Euclidean normalizer consists of metric-preserving affine operations that normalize the space group in the chosen setting.\nThese operations are useful for algorithms that need to compare or enumerate equivalent descriptions of the same setting under rigid crystallographic changes of coordinates.\n\nThis object is generated from the finite Euclidean normalizer operations exposed by cctbx.\nIt is not a bounded candidate search table.\nTherefore fields such as `candidate_set`, `candidate_sets`, and bounded-search `bounds` do not belong to this property.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **normalizer\\_kind**: REQUIRED; String.\n      Kind label for this normalizer contribution.\n      For this property the value is `euclidean`.\n\n    - **n\\_centering\\_translations**: REQUIRED; Integer.\n      Number of centering translations represented in the underlying Euclidean normalizer operation construction.\n\n    - **n\\_pointgroup\\_symops**: REQUIRED; Integer.\n      Number of point-group symmetry operations represented before centering translations are combined with them.\n\n    - **n\\_symops**: REQUIRED; Integer.\n      Number of Euclidean normalizer operations listed in `symops`.\n      This value MUST equal the length of `symops`.\n\n    - **n\\_linear\\_parts**: REQUIRED; Integer.\n      Number of distinct linear matrix parts represented in `symops`.\n\n    - **symops**: REQUIRED; List of dictionaries.\n      Finite Euclidean normalizer operations for the setting.\n      Each item follows `/defs/v0.1/properties/symmetry/affine_transformation`.",
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
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Finite Euclidean normalizer operations for the setting.",
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
            "normalizer_kind": "euclidean",
            "n_centering_translations": 1,
            "n_pointgroup_symops": 1,
            "n_symops": 2,
            "n_linear_parts": 2,
            "symops": [
                {
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
                    "is_orthogonal": true,
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