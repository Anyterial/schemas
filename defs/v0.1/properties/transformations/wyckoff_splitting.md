# Wyckoff splitting (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/wyckoff_splitting`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/wyckoff_splitting.md)**  
**Definition name:** `wyckoff_splitting`

**Property name:** Wyckoff splitting  
**Description:** Wyckoff-position splitting data associated with a subgroup or same-space-group transform.  
**Type:** list  

Each list item gives the split of one parent Wyckoff position.
The parent Wyckoff letter is stored in the `parent` field rather than as a JSON dictionary key.

**Requirements/Conventions**:

- It MUST be a list of dictionaries.
- Each dictionary MUST contain `parent`, the Wyckoff letter in the parent setting.
- Each dictionary MUST contain `splits`, an ordered list of subgroup Wyckoff-position assignments or coordinate expressions emitted by the generator.

**Examples:**

- `[{"parent": "c", "splits": [{"letter": "e", "xyz": "x,y,z", "affine": [["1", "0", "0", "0"], ["0", "1", "0", "0"], ["0", "0", "1", "0"]]}]}]`

**Formats:** [[JSON](wyckoff_splitting.json)] [[MD](wyckoff_splitting.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/transformations/wyckoff_splitting",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Wyckoff splitting",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "wyckoff_splitting",
        "label": "wyckoff_splitting_transformations"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Wyckoff-position splitting data associated with a subgroup or same-space-group transform.\n\nEach list item gives the split of one parent Wyckoff position.\nThe parent Wyckoff letter is stored in the `parent` field rather than as a JSON dictionary key.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST contain `parent`, the Wyckoff letter in the parent setting.\n- Each dictionary MUST contain `splits`, an ordered list of subgroup Wyckoff-position assignments or coordinate expressions emitted by the generator.",
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
                            "x-optimade-dimensions": {
                                "names": [
                                    "dim_lattice",
                                    "dim_affine"
                                ],
                                "sizes": [
                                    3,
                                    4
                                ]
                            },
                            "type": [
                                "array"
                            ],
                            "description": "Exact affine representation for the split branch as a 3 by 4 augmented matrix.\nEach row holds the three linear coefficients followed by the translation component, all as exact fraction strings.",
                            "items": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "x-optimade-dimensions": {
                                    "names": [
                                        "dim_affine"
                                    ],
                                    "sizes": [
                                        4
                                    ]
                                },
                                "type": [
                                    "array"
                                ],
                                "description": "One row of the augmented affine matrix.",
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
                        }
                    }
                }
            }
        }
    },
    "examples": [
        [
            {
                "parent": "c",
                "splits": [
                    {
                        "letter": "e",
                        "xyz": "x,y,z",
                        "affine": [
                            [
                                "1",
                                "0",
                                "0",
                                "0"
                            ],
                            [
                                "0",
                                "1",
                                "0",
                                "0"
                            ],
                            [
                                "0",
                                "0",
                                "1",
                                "0"
                            ]
                        ]
                    }
                ]
            }
        ]
    ]
}
```