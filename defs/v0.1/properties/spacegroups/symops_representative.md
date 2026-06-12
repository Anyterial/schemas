# Representative symmetry operations (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative.md)**  
**Definition name:** `symops_representative`

**Property name:** Representative symmetry operations  
**Description:** Representative symmetry-operation descriptors modulo centering translations.  
**Type:** list  

Each list member is an operation on the format defined by the property definition: https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op

**Examples:**

- `[{"affine_transformation": {"matrix": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "1"]], "vector": ["0", "0", "0"], "xyz": "x,y,z"}, "rot_type": "1", "sense": 0, "axis": [0, 0, 0], "screw_glide": ["0", "0", "0"], "origin_shift": ["0", "0", "0"]}]`

**Formats:** [[JSON](symops_representative.json)] [[MD](symops_representative.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Representative symmetry operations",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "symops_representative",
        "label": "symops_representative_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Representative symmetry-operation descriptors modulo centering translations.\n\nEach list member is an operation on the format defined by the property definition: https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op",
    "items": {
        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op",
        "title": "Operation",
        "x-optimade-type": "dictionary",
        "x-optimade-definition": {
            "kind": "property",
            "version": "0.1.0",
            "format": "1.3",
            "name": "op",
            "label": "op_symmetry"
        },
        "x-optimade-unit": "inapplicable",
        "type": [
            "object",
            "null"
        ],
        "description": "Information related to a crystallographic operation acting within one coordinate setting.\n\nRepresents an affine_transformation that is a crystallographic operation within one setting.\nThe affine map itself is stored in the embedded `affine_transformation` field.\nThe remaining fields classify the operation crystallographically, for example by rotation type, axis, sense, and screw or glide component.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **affine\\_transformation**: REQUIRED; Dictionary.\n      Exact affine map for the operation.\n      It MUST follow `/defs/v0.1/properties/symmetry/affine_transformation`.\n\n    - **rot\\_type**: OPTIONAL; String.\n      Crystallographic operation-type label for the linear part.\n\n    - **axis**: OPTIONAL; List of 3 Integers.\n      Operation axis or invariant direction using the integer-vector convention returned by the generator.\n\n    - **sense**: OPTIONAL; Integer.\n      Rotation sense/sign convention returned by the generator; `0` is used when no handed rotation sense is applicable.\n\n    - **screw\\_glide**: OPTIONAL; List of 3 Fractions (String).\n      Screw-axis or glide-plane component associated with a space-group affine operation.\n\n    - **origin\\_shift**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift associated with the screw/glide decomposition of a space-group affine operation.\n\n- Whether the operation is proper follows from the sign of the `det` field of `affine_transformation`; no separate properness flag is stored.",
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
            "rot_type": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "string",
                    "null"
                ],
                "description": "Symbolic crystallographic operation-type label for the linear part.",
                "enum": [
                    "1",
                    "-1",
                    "2",
                    "m",
                    "3",
                    "-3",
                    "4",
                    "-4",
                    "6",
                    "-6"
                ]
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
        "examples": [
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
                },
                "rot_type": "2",
                "sense": 0,
                "axis": [
                    0,
                    0,
                    1
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
    },
    "examples": [
        [
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
                    ],
                    "xyz": "x,y,z"
                },
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
```