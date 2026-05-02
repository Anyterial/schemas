# Orthogonal affine normalizer cosets (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer_cosets.md)**  
**Definition name:** `orthogonal_affine_normalizer_cosets`

**Property name:** Orthogonal affine normalizer cosets  
**Description:** Runtime list of orthogonal signed-permutation affine normalizer coset representatives modulo the space group.
Each item is one finite listed representative and follows `/properties/symmetry/affine_transformation`.
The list is a bounded representative table, not a complete infinite affine normalizer.  
**Type:** list  



**Examples:**

- `[{"matrix": [["-1", "0", "0"], ["0", "-1", "0"], ["0", "0", "1"]], "vector": ["0", "0", "0"], "xyz": "-x,-y,z", "det": 1, "is_orthogonal": true}]`

**Formats:** [[JSON](orthogonal_affine_normalizer_cosets.json)] [[MD](orthogonal_affine_normalizer_cosets.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer_cosets",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Orthogonal affine normalizer cosets",
    "$comment": "Anyterial normalizer-coset list property using the common normalizer-representative definition.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "orthogonal_affine_normalizer_cosets",
        "label": "orthogonal_affine_normalizer_cosets_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Runtime list of orthogonal signed-permutation affine normalizer coset representatives modulo the space group.\nEach item is one finite listed representative and follows `/properties/symmetry/affine_transformation`.\nThe list is a bounded representative table, not a complete infinite affine normalizer.",
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
    },
    "examples": [
        [
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
    ]
}
```