# Hall to IT standard transform (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_to_it_std_transform`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_to_it_std_transform.md)**  
**Definition name:** `hall_to_it_std_transform`

**Property name:** Hall to IT standard transform  
**Description:** Exact basis and origin transform from one stored Hall setting to the International Tables standard Hall setting of the same space-group type.
This transform is useful when data generated or detected in an arbitrary Hall setting needs to be compared with a conventional IT-standard reference setting.
The transform is represented by `matrix` and `vector`, following the same affine-transformation convention as the other generated transformation tables.  
**Type:** dictionary  

If `x_to_ref_hall` is a fractional coordinate column vector in the target IT-standard Hall setting, and `x_from_hall` is the corresponding fractional coordinate column vector in the source Hall setting keyed by the containing map, then the stored transform satisfies:
`x_from_hall = matrix * x_to_ref_hall + vector`.

**Requirements/Conventions**:

- It MUST be a dictionary describing one exact transform from the containing Hall setting to the IT-standard Hall setting of the same `it_number`.
- The `index` value is always `1`, because this is a same-space-group setting transform rather than a proper subgroup transform.
- Matrix and vector entries MUST be exact strings, using integer strings or fraction strings as appropriate.
- It MUST be a dictionary with the following keys:

    - **hall\_entry**: REQUIRED; String.
      Source Hall-entry key for the setting transformed by this object.

    - **it\_number**: REQUIRED; Integer.
      International Tables space-group number shared by the source and target Hall settings.

    - **to\_hall**: REQUIRED; String.
      Target Hall-entry key for the IT-standard Hall setting of the same space-group type.

    - **to\_hall\_symbol**: REQUIRED; String.
      Display Hall symbol corresponding to `to_hall`, using spaces rather than the normalized Hall-entry key syntax.

    - **index**: REQUIRED; Integer.
      Transform index.
      For this table the value is `1` because the transform maps between settings of the same space group.

    - **affine\_transformation**: REQUIRED; Dictionary.
      Exact affine map for this setting transform.
      It MUST follow `/defs/v0.1/properties/symmetry/affine_transformation`.
      The transform convention is `x_from_hall = matrix * x_to_ref_hall + vector`, where `matrix` and `vector` are the fields inside `affine_transformation`.

**Examples:**

- `{"hall_entry": "p_1", "it_number": 1, "to_hall": "p_1", "to_hall_symbol": "p 1", "index": 1, "affine_transformation": {"matrix": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "1"]], "vector": ["0", "0", "0"]}}`

**Formats:** [[JSON](hall_to_it_std_transform.json)] [[MD](hall_to_it_std_transform.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_to_it_std_transform",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Hall to IT standard transform",
    "$comment": "Hall-keyed exact change-of-basis transforms to the IT standard Hall setting.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hall_to_it_std_transform",
        "label": "hall_to_it_std_transform_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Exact basis and origin transform from one stored Hall setting to the International Tables standard Hall setting of the same space-group type.\nThis transform is useful when data generated or detected in an arbitrary Hall setting needs to be compared with a conventional IT-standard reference setting.\nThe transform is represented by `matrix` and `vector`, following the same affine-transformation convention as the other generated transformation tables.\n\nIf `x_to_ref_hall` is a fractional coordinate column vector in the target IT-standard Hall setting, and `x_from_hall` is the corresponding fractional coordinate column vector in the source Hall setting keyed by the containing map, then the stored transform satisfies:\n`x_from_hall = matrix * x_to_ref_hall + vector`.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary describing one exact transform from the containing Hall setting to the IT-standard Hall setting of the same `it_number`.\n- The `index` value is always `1`, because this is a same-space-group setting transform rather than a proper subgroup transform.\n- Matrix and vector entries MUST be exact strings, using integer strings or fraction strings as appropriate.\n- It MUST be a dictionary with the following keys:\n\n    - **hall\\_entry**: REQUIRED; String.\n      Source Hall-entry key for the setting transformed by this object.\n\n    - **it\\_number**: REQUIRED; Integer.\n      International Tables space-group number shared by the source and target Hall settings.\n\n    - **to\\_hall**: REQUIRED; String.\n      Target Hall-entry key for the IT-standard Hall setting of the same space-group type.\n\n    - **to\\_hall\\_symbol**: REQUIRED; String.\n      Display Hall symbol corresponding to `to_hall`, using spaces rather than the normalized Hall-entry key syntax.\n\n    - **index**: REQUIRED; Integer.\n      Transform index.\n      For this table the value is `1` because the transform maps between settings of the same space group.\n\n    - **affine\\_transformation**: REQUIRED; Dictionary.\n      Exact affine map for this setting transform.\n      It MUST follow `/defs/v0.1/properties/symmetry/affine_transformation`.\n      The transform convention is `x_from_hall = matrix * x_to_ref_hall + vector`, where `matrix` and `vector` are the fields inside `affine_transformation`.",
    "properties": {
        "hall_entry": {
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
        "to_hall": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall",
            "title": "To Hall",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "to_hall",
                "label": "to_hall_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Reference Hall-entry key to which a setting transform maps the current Hall setting.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "p_1",
                "-p_1"
            ]
        },
        "to_hall_symbol": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall_symbol",
            "title": "To Hall Symbol",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "to_hall_symbol",
                "label": "to_hall_symbol_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Display Hall symbol corresponding to `to_hall`.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "p 1",
                "-p 1"
            ]
        },
        "index": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index",
            "title": "Index",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "index",
                "label": "index_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Subgroup or transform index. For subgroup transforms it is the crystallographic subgroup index `[G:H]`, equal to the determinant factor of the basis transformation when applicable.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                2,
                4
            ]
        },
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
        }
    },
    "examples": [
        {
            "hall_entry": "p_1",
            "it_number": 1,
            "to_hall": "p_1",
            "to_hall_symbol": "p 1",
            "index": 1,
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
```