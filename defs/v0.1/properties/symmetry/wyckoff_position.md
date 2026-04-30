# Wyckoff position (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/wyckoff_position`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/wyckoff_position.md)**  
**Definition name:** `wyckoff_position`

**Property name:** Wyckoff position  
**Description:** One Wyckoff position in a space-group setting.
The record gives the multiplicity, oriented site-symmetry symbol, representative coordinate, full orbit, and orbit factorized modulo centering translations.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary with the following keys:

    - **multiplicity**: REQUIRED; Integer.
      Multiplicity of the Wyckoff position in the conventional cell.

    - **sitesym**: REQUIRED; String.
      Oriented site-symmetry symbol.

    - **hasfreedom**: REQUIRED; List of booleans.
      Flags indicating whether each fractional coordinate has a free parameter.

    - **first\_orbit**: REQUIRED; String.
      First representative coordinate expression used by the generator.

    - **orbit\_affine**: REQUIRED; List.
      Full orbit in affine matrix/vector representation.

    - **orbit\_xyz**: REQUIRED; List of strings.
      Full orbit in `x,y,z` coordinate notation.

    - **orbit\_mod\_centering\_affine**: REQUIRED; List.
      Orbit representatives modulo centering translations in affine representation.

    - **orbit\_mod\_centering\_xyz**: REQUIRED; List of strings.
      Orbit representatives modulo centering translations in `x,y,z` notation.

**Examples:**

- `{"multiplicity": 2, "sitesym": "1", "hasfreedom": [true, true, true], "first_orbit": "x,y,z", "orbit_xyz": ["x", "y", "z", "-x", "y", "-z"], "orbit_mod_centering_xyz": ["x", "y", "z", "-x", "y", "-z"]}`

**Formats:** [[JSON](wyckoff_position.json)] [[MD](wyckoff_position.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/wyckoff_position",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Wyckoff position",
    "$comment": "Reusable Anyterial definition for one Wyckoff-position record in a space-group setting.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "wyckoff_position",
        "label": "wyckoff_position_symmetry"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "One Wyckoff position in a space-group setting.\nThe record gives the multiplicity, oriented site-symmetry symbol, representative coordinate, full orbit, and orbit factorized modulo centering translations.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **multiplicity**: REQUIRED; Integer.\n      Multiplicity of the Wyckoff position in the conventional cell.\n\n    - **sitesym**: REQUIRED; String.\n      Oriented site-symmetry symbol.\n\n    - **hasfreedom**: REQUIRED; List of booleans.\n      Flags indicating whether each fractional coordinate has a free parameter.\n\n    - **first\\_orbit**: REQUIRED; String.\n      First representative coordinate expression used by the generator.\n\n    - **orbit\\_affine**: REQUIRED; List.\n      Full orbit in affine matrix/vector representation.\n\n    - **orbit\\_xyz**: REQUIRED; List of strings.\n      Full orbit in `x,y,z` coordinate notation.\n\n    - **orbit\\_mod\\_centering\\_affine**: REQUIRED; List.\n      Orbit representatives modulo centering translations in affine representation.\n\n    - **orbit\\_mod\\_centering\\_xyz**: REQUIRED; List of strings.\n      Orbit representatives modulo centering translations in `x,y,z` notation.",
    "properties": {
        "multiplicity": {
            "x-optimade-type": "integer",
            "x-optimade-unit": "inapplicable",
            "type": [
                "integer",
                "null"
            ],
            "description": "Multiplicity of the Wyckoff position in the conventional cell."
        },
        "sitesym": {
            "x-optimade-type": "string",
            "x-optimade-unit": "inapplicable",
            "type": [
                "string",
                "null"
            ],
            "description": "Oriented site-symmetry symbol."
        },
        "hasfreedom": {
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
            "description": "Three flags indicating whether each fractional coordinate contains a free parameter.",
            "items": {
                "x-optimade-type": "boolean",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "boolean"
                ],
                "description": "Whether the corresponding coordinate is free."
            }
        },
        "first_orbit_ita": {
            "x-optimade-type": "string",
            "x-optimade-unit": "inapplicable",
            "type": [
                "string",
                "null"
            ],
            "description": "Representative coordinate expression following the ITA source convention, when distinct from `first_orbit`."
        },
        "first_orbit": {
            "x-optimade-type": "string",
            "x-optimade-unit": "inapplicable",
            "type": [
                "string",
                "null"
            ],
            "description": "Representative coordinate expression for the Wyckoff position."
        },
        "orbit_affine": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Full orbit represented as affine matrix/vector data.",
            "items": {
                "x-optimade-type": "list",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "array"
                ],
                "description": "One generator-emitted affine orbit operation represented as nested exact lists.",
                "items": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array"
                    ],
                    "description": "One row or component list of the affine orbit representation.",
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
        "orbit_xyz": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Full orbit represented as `x,y,z` coordinate expressions.",
            "items": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "string"
                ],
                "description": "One coordinate expression."
            }
        },
        "orbit_mod_centering_affine": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Orbit representatives modulo centering translations in affine matrix/vector representation.",
            "items": {
                "x-optimade-type": "list",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "array"
                ],
                "description": "One generator-emitted affine orbit operation represented as nested exact lists.",
                "items": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array"
                    ],
                    "description": "One row or component list of the affine orbit representation.",
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
        "orbit_mod_centering_xyz": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Orbit representatives modulo centering translations as `x,y,z` coordinate expressions.",
            "items": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "string"
                ],
                "description": "One coordinate expression."
            }
        }
    },
    "examples": [
        {
            "multiplicity": 2,
            "sitesym": "1",
            "hasfreedom": [
                true,
                true,
                true
            ],
            "first_orbit": "x,y,z",
            "orbit_xyz": [
                "x",
                "y",
                "z",
                "-x",
                "y",
                "-z"
            ],
            "orbit_mod_centering_xyz": [
                "x",
                "y",
                "z",
                "-x",
                "y",
                "-z"
            ]
        }
    ]
}
```