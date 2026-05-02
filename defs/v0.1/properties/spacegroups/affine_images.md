# Affine images (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_images`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_images.md)**  
**Definition name:** `affine_images`

**Property name:** Affine images  
**Description:** Same-space-group affine images for a standard setting.
The list combines Euclidean normalizer operations and isomorphic subgroup transforms to enumerate alternative affine images of the same space group used by runtime search code.
Matrix/vector transform fields follow `/properties/symmetry/basis_transform`.  
**Type:** list  



**Examples:**

- `[{"matrix": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "1"]], "vector": ["0", "0", "0"]}]`

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
    "description": "Same-space-group affine images for a standard setting.\nThe list combines Euclidean normalizer operations and isomorphic subgroup transforms to enumerate alternative affine images of the same space group used by runtime search code.\nMatrix/vector transform fields follow `/properties/symmetry/basis_transform`.",
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
    },
    "examples": [
        [
            {
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
        ]
    ]
}
```