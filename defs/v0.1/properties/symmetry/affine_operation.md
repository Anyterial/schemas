# Affine operation (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_operation`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_operation.md)**  
**Definition name:** `affine_operation`

**Property name:** Affine operation  
**Description:** One affine operation in a fixed crystallographic setting.
The operation may be represented by an exact matrix/vector pair, by an `x,y,z` expression, or by both depending on the parent table.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary with the following keys:

    - **rmat**: OPTIONAL; Exact 3x3 matrix.
      Linear matrix part of the affine operation.

    - **tvec**: OPTIONAL; List of 3 Fractions (String).
      Translation vector of the affine operation.

    - **xyz**: OPTIONAL; String.
      Coordinate expression for the affine operation in `x,y,z` notation.

    - **rmat\_det**: OPTIONAL; Integer.
      Determinant of `rmat` when supplied.

    - **rmat\_is\_orthogonal**: OPTIONAL; Boolean.
      States whether the linear matrix is orthogonal in the generator's exact representation.

**Examples:**

- `{"rmat": [["-1", "0", "0"], ["0", "-1", "0"], ["0", "0", "1"]], "tvec": ["0", "0", "0"], "xyz": "-x,-y,z", "rmat_det": 1, "rmat_is_orthogonal": true}`

**Formats:** [[JSON](affine_operation.json)] [[MD](affine_operation.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_operation",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Affine operation",
    "$comment": "Reusable Anyterial definition for one affine operation within a fixed crystallographic setting.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "affine_operation",
        "label": "affine_operation_symmetry"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "One affine operation in a fixed crystallographic setting.\nThe operation may be represented by an exact matrix/vector pair, by an `x,y,z` expression, or by both depending on the parent table.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Linear matrix part of the affine operation.\n\n    - **tvec**: OPTIONAL; List of 3 Fractions (String).\n      Translation vector of the affine operation.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the affine operation in `x,y,z` notation.\n\n    - **rmat\\_det**: OPTIONAL; Integer.\n      Determinant of `rmat` when supplied.\n\n    - **rmat\\_is\\_orthogonal**: OPTIONAL; Boolean.\n      States whether the linear matrix is orthogonal in the generator's exact representation.",
    "properties": {
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
        "tvec": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/tvec",
            "title": "Symmetry operation translation vector",
            "$comment": "Reusable Anyterial definition for the translation part of a same-setting affine operation.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "tvec",
                "label": "tvec_symmetry"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Translation part of a same-setting affine operation acting on fractional coordinates.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- Together with `rmat`, this vector represents an affine operation within one coordinate setting.",
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
                    "1/2",
                    "1/2",
                    "0"
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
            "description": "Coordinate expression for the affine operation in `x,y,z` notation."
        },
        "rmat_det": {
            "x-optimade-type": "integer",
            "x-optimade-unit": "inapplicable",
            "type": [
                "integer",
                "null"
            ],
            "description": "Determinant of the linear matrix part."
        },
        "rmat_is_orthogonal": {
            "x-optimade-type": "boolean",
            "x-optimade-unit": "inapplicable",
            "type": [
                "boolean",
                "null"
            ],
            "description": "Whether the linear matrix part is orthogonal."
        }
    },
    "examples": [
        {
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
                    "1"
                ]
            ],
            "tvec": [
                "0",
                "0",
                "0"
            ],
            "xyz": "-x,-y,z",
            "rmat_det": 1,
            "rmat_is_orthogonal": true
        }
    ]
}
```