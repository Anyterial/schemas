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
      Same-space-group affine images represented by exact `pmat` and `pvec` transforms.

**Examples:**

- `{"it_number": 1, "hall": "p_1", "affine_images": [{"pmat": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "1"]], "pvec": ["0", "0", "0"]}]}`

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
    "description": "Same-space-group affine-image record for one International Tables standard setting.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **it\\_number**: REQUIRED; Integer.\n      International Tables space-group number for the standard setting.\n\n    - **hall**: REQUIRED; String.\n      Hall-entry key of the reference setting used for the standard setting.\n\n    - **affine\\_images**: REQUIRED; List of dictionaries.\n      Same-space-group affine images represented by exact `pmat` and `pvec` transforms.",
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
            }
        }
    },
    "examples": [
        {
            "it_number": 1,
            "hall": "p_1",
            "affine_images": [
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
        }
    ]
}
```