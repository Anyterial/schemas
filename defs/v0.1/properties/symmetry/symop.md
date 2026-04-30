# Symmetry operation (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/symop`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/symop.md)**  
**Definition name:** `symop`

**Property name:** Symmetry operation  
**Description:** A single crystallographic symmetry-operation descriptor.
Space-group operation lists currently store the operation type, axis, sense, and screw/glide decomposition.
Point-group operation lists currently store the full integer operation matrix under the legacy key `matrix` together with an integer operation-type code under `type`.
Future generated data may also use the semantic `rmat` key for the linear matrix part.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary with the following keys:

    - **rot\_type**: OPTIONAL; String.
      Crystallographic operation-type label for the linear part, such as `1`, `-1`, `2`, `m`, `-3`, `4`, `-4`, `6`, or `-6`.
      This is the preferred symbolic operation-type field in space-group operation descriptors.

    - **type**: OPTIONAL; Integer.
      Legacy numeric operation-type code used by point-group operation descriptors.

    - **axis**: OPTIONAL; List of 3 Integers.
      Operation axis or invariant direction using the integer-vector convention returned by the generator.

    - **sense**: OPTIONAL; Integer.
      Rotation sense/sign convention returned by the generator; `0` is used when no handed rotation sense is applicable.

    - **screw\_glide**: OPTIONAL; List of 3 Fractions (String).
      Screw-axis or glide-plane component associated with a space-group affine operation.

    - **origin\_shift**: OPTIONAL; List of 3 Fractions (String).
      Origin shift associated with the screw/glide decomposition of a space-group affine operation.

    - **matrix**: OPTIONAL; Integer 3x3 matrix.
      Legacy full point-group operation matrix.

    - **rmat**: OPTIONAL; Exact 3x3 matrix.
      Semantic linear matrix part of an affine operation when emitted by a parent table.

    - **xyz**: OPTIONAL; String.
      Coordinate expression for the operation in `x,y,z` notation when available.

    - **is\_proper**: OPTIONAL; Boolean.
      States whether the linear operation is proper, i.e., whether its determinant is +1.

**Examples:**

- `{"rot_type": "2", "sense": 0, "axis": [0, 1, 0], "screw_glide": ["0", "0", "0"], "origin_shift": ["0", "0", "0"]}`
- `{"matrix": [[1, 0, 0], [0, 1, 0], [0, 0, 1]], "xyz": "x,y,z", "type": 1, "is_proper": true, "axis": [0, 0, 0], "sense": 0}`

**Formats:** [[JSON](symop.json)] [[MD](symop.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/symop",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
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
}
```