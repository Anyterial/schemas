# Same space group affine images std (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/same_space_group_affine_images_std`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/same_space_group_affine_images_std.md)**  
**Definition name:** `same_space_group_affine_images_std`

**Property name:** Same space group affine images std  
**Description:** Same-space-group affine-image record for one International Tables standard setting.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary with the following keys:

    - **it\_number**: REQUIRED; Integer.
      International Tables space-group number for the standard setting.

    - **hall**: REQUIRED; String.
      Hall-entry key of the reference setting used for the standard setting.

    - **affine\_images**: REQUIRED; List of dictionaries.
      Same-space-group affine images represented by exact `matrix` and `vector` transforms.

**Examples:**

- `{"it_number": 1, "hall": "p_1", "affine_images": [{"affine_transformation": {"matrix": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "1"]], "vector": ["0", "0", "0"]}}]}`

**Formats:** [[JSON](same_space_group_affine_images_std.json)] [[MD](same_space_group_affine_images_std.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/same_space_group_affine_images_std",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Same space group affine images std",
    "$comment": "IT-number keyed same-space-group affine-image records for standard settings.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "same_space_group_affine_images_std",
        "label": "same_space_group_affine_images_std_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Same-space-group affine-image record for one International Tables standard setting.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **it\\_number**: REQUIRED; Integer.\n      International Tables space-group number for the standard setting.\n\n    - **hall**: REQUIRED; String.\n      Hall-entry key of the reference setting used for the standard setting.\n\n    - **affine\\_images**: REQUIRED; List of dictionaries.\n      Same-space-group affine images represented by exact `matrix` and `vector` transforms.",
    "properties": {
        "it_number": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number",
            "title": "International Tables Space-Group Number",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "integer",
            "x-compatibility": [
                "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_it_number"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "it_number",
                "label": "it_number_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "The International Tables space-group number.\n\nThis integer identifies the space-group type numbered 1 through 230 in International Tables for Crystallography. Multiple Hall settings can share the same `it_number`.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                1,
                5
            ]
        },
        "hall": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry",
            "title": "Hall entry",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hall_entry",
                "label": "hall_entry_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Normalized Hall-table entry key used internally by the generated datasets.\n\nThe value is derived from the Hall symbol by using lowercase letters and underscores in place of spaces. It is stable for lookup within these data files, while the display Hall symbol is provided separately by `hall` and its formatted variants.\n\n**Requirements/Conventions**:\n\n- This field identifies a concrete Hall setting, not only an IT space-group type.\n- The same value is normally used as the key of the containing `spacegroups` map.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "p_1",
                "-p_1"
            ]
        },
        "affine_images": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Same-space-group affine image transforms.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/basis_transform",
                "title": "Basis transformation",
                "$comment": "Reusable Anyterial definition for one crystallographic basis, setting, cell, or embedding transform.",
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
                "description": "One crystallographic transform between coordinate descriptions, settings, cells, or related group embeddings.\nThe affine map itself is stored in the embedded `affine_transformation` field.\nParent tables use this object for Hall-to-standard transforms, B\u00e4rnighausen subgroup transforms, isomorphic subgroup transforms, normalizer representatives, and same-space-group affine images.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **affine\\_transformation**: REQUIRED; Dictionary.\n      Exact affine map for the transform.\n      It MUST follow `/defs/v0.1/properties/symmetry/affine_transformation`.\n\n    - **index**: OPTIONAL; Integer.\n      Subgroup index, same-setting transform index, or cell-index metadata whose interpretation is defined by the parent table.\n\n    - **subgroup\\_type**: OPTIONAL; String.\n      International Tables subgroup-type label when the transform describes a subgroup embedding.\n\n    - **k\\_subtype**: OPTIONAL; String or null.\n      Klassengleiche subtype when the transform describes a klassengleiche subgroup relation.\n\n    - **compatible\\_systems**: OPTIONAL; List of strings.\n      Crystal metric systems for which the transform is compatible.\n      This is used for bounded affine normalizer representatives.\n\n    - **operation\\_kind**: OPTIONAL; String.\n      Generator classification of the transform or representative.\n\n    - **wyckoff\\_splitting**: OPTIONAL; List.\n      Wyckoff-position splitting metadata induced by the transform when available.\n\n    - **criteria**: OPTIONAL; List.\n      Backward-lift constraint metadata induced by the transform when available.",
                "properties": {
                    "affine_transformation": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation",
                        "title": "Affine transformation",
                        "$comment": "Reusable Anyterial definition for the pure affine-map part of crystallographic transformation records.",
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
                        "description": "One exact affine transformation acting on fractional crystallographic coordinates.\nThe transformation is represented by a 3 by 3 matrix and a 3-vector, both serialized with exact string entries.\nParent properties define the coordinate convention and semantic role of the transformation, for example whether it is an operation within one setting, a setting transform, a subgroup embedding, or a normalizer representative.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **matrix**: REQUIRED; Exact 3x3 matrix.\n      Matrix part of the affine transformation.\n      It MUST be represented as a list of three row lists, each containing three exact rational entries represented as strings.\n\n    - **vector**: REQUIRED; List of 3 Fractions (String).\n      Translation or origin-shift vector of the affine transformation in fractional coordinates.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the affine transformation in `x,y,z` notation when available.\n\n    - **det**: OPTIONAL; Integer.\n      Determinant of `matrix` when the generator emits it.\n\n    - **is\\_orthogonal**: OPTIONAL; Boolean.\n      Whether `matrix` is orthogonal in the exact representation used by the generator.",
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
                        "description": "Generator classification of the transform or representative."
                    },
                    "wyckoff_splitting": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Wyckoff-position splitting metadata induced by the transform, grouped by explicit parent Wyckoff letter.",
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
                                                "type": [
                                                    "array"
                                                ],
                                                "description": "Exact affine representation for the split branch.",
                                                "items": {
                                                    "x-optimade-type": "list",
                                                    "x-optimade-unit": "inapplicable",
                                                    "type": [
                                                        "array"
                                                    ],
                                                    "description": "One affine row.",
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
                                            }
                                        }
                                    }
                                }
                            }
                        }
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
                                                        "type": [
                                                            "array"
                                                        ],
                                                        "description": "One exact coefficient vector.",
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
                            ]
                        },
                        "index": 2
                    }
                ]
            }
        }
    },
    "examples": [
        {
            "it_number": 1,
            "hall": "p_1",
            "affine_images": [
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
                                "1"
                            ]
                        ],
                        "vector": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                }
            ]
        }
    ]
}
```