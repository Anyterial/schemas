# Affine transformation (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation.md)**  
**Definition name:** `affine_transformation`

**Property name:** Affine transformation  
**Description:** One exact affine transformation acting on fractional crystallographic coordinates.
The transformation is represented by a 3 by 3 matrix and a 3-vector, both serialized with exact string entries.
Parent properties define the coordinate convention and semantic role of the transformation, for example whether it is an operation within one setting, a setting transform, a subgroup embedding, or a normalizer representative.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary with the following keys:

    - **matrix**: REQUIRED; Exact 3x3 matrix.
      Matrix part of the affine transformation.
      It MUST be represented as a list of three row lists, each containing three exact rational entries represented as strings.

    - **vector**: REQUIRED; List of 3 Fractions (String).
      Translation or origin-shift vector of the affine transformation in fractional coordinates.

    - **xyz**: OPTIONAL; String.
      Coordinate expression for the affine transformation in `x,y,z` notation when available.

    - **det**: OPTIONAL; Integer.
      Determinant of `matrix` when the generator emits it.

    - **is\_orthogonal**: OPTIONAL; Boolean.
      Whether `matrix` is orthogonal in the exact representation used by the generator.

**Examples:**

- `{"matrix": [["-1", "0", "0"], ["0", "-1", "0"], ["0", "0", "1"]], "vector": ["0", "0", "0"], "xyz": "-x,-y,z", "det": 1, "is_orthogonal": true}`

**Formats:** [[JSON](affine_transformation.json)] [[MD](affine_transformation.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
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
```