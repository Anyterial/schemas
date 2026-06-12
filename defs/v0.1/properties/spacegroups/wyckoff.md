# Wyckoff positions (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff.md)**  
**Definition name:** `wyckoff`

**Property name:** Wyckoff positions  
**Description:** Wyckoff-position table for a specific space-group setting.  
**Type:** list  

Each list item describes one Wyckoff position and includes the Wyckoff letter as ordinary data.
This list representation avoids using JSON dictionary keys as crystallographic data.
Items follow `/properties/symmetry/wyckoff_position`.

**Requirements/Conventions**:

- It MUST be a list of dictionaries.
- Each item MUST include `letter`, identifying the Wyckoff letter for that position in the setting.
- `orbit` contains the full orbit as affine transformations from Wyckoff-position parameters to fractional coordinates.
- `orbit_mod_centering` contains one representative modulo centering translations in the same representation.

**Examples:**

- `[{"letter": "e", "multiplicity": 2, "sitesym": "1", "hasfreedom": [true, true, true], "first_orbit": "x,y,z", "orbit": [{"matrix": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "1"]], "vector": ["0", "0", "0"], "xyz": "x,y,z"}], "orbit_mod_centering": [{"matrix": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "1"]], "vector": ["0", "0", "0"], "xyz": "x,y,z"}]}]`

**Formats:** [[JSON](wyckoff.json)] [[MD](wyckoff.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Wyckoff positions",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "wyckoff",
        "label": "wyckoff_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Wyckoff-position table for a specific space-group setting.\n\nEach list item describes one Wyckoff position and includes the Wyckoff letter as ordinary data.\nThis list representation avoids using JSON dictionary keys as crystallographic data.\nItems follow `/properties/symmetry/wyckoff_position`.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each item MUST include `letter`, identifying the Wyckoff letter for that position in the setting.\n- `orbit` contains the full orbit as affine transformations from Wyckoff-position parameters to fractional coordinates.\n- `orbit_mod_centering` contains one representative modulo centering translations in the same representation.",
    "items": {
        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/wyckoff_position",
        "title": "Wyckoff position",
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
        "description": "Information related to a Wyckoff position in a space-group setting.\n\nWyckoff positions represent symmetry-equivalent sites paritioned by multiplicity and site symmetry in a given space group.\nThe property is a dictionary containing information about the multiplicity, oriented site-symmetry symbol, representative coordinate, full orbit, and orbit factorized modulo centering translations.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **letter**: REQUIRED; String.\n      Wyckoff letter for this position in the setting.\n\n    - **multiplicity**: REQUIRED; Integer.\n      Multiplicity of the Wyckoff position in the conventional cell.\n\n    - **sitesym**: REQUIRED; String.\n      Oriented site-symmetry symbol.\n\n    - **hasfreedom**: REQUIRED; List of booleans.\n      Flags indicating whether each fractional coordinate has a free parameter.\n\n    - **first\\_orbit**: REQUIRED; String.\n      First representative coordinate expression used by the generator.\n\n    - **orbit**: REQUIRED; List.\n      Full orbit as a list of affine transformations from Wyckoff-position parameters to fractional coordinates.\n\n    - **orbit\\_mod\\_centering**: REQUIRED; List.\n      Orbit representatives modulo centering translations, represented in the same form as `orbit`.",
        "properties": {
            "letter": {
                "$id": "https://schemas.optimade.org/defs/v1.3/properties/optimade/structures/wyckoff_positions",
                "title": "Wyckoff positions",
                "x-optimade-type": "list",
                "x-optimade-definition": {
                    "label": "wyckoff_positions_optimade_structures",
                    "kind": "property",
                    "version": "1.3.0",
                    "format": "1.2",
                    "name": "wyckoff_positions"
                },
                "x-optimade-dimensions": {
                    "names": [
                        "dim_sites"
                    ],
                    "sizes": [
                        null
                    ]
                },
                "type": [
                    "array",
                    "null"
                ],
                "description": "A list of Wyckoff symbols of sites (where values for sites are specified with the same order of the property `cartesian_site_positions` and/or `fractional_site_positions`).\n\n**Requirements/Conventions**:\n\n- MUST have length equal to the number of sites in the structure (first dimension of the list properties `cartesian_site_positions` and/or `fractional_site_positions`).\n- If provided, MUST list a single letter (`a`-`z` or `\u03b1`) Wyckoff position for each site in the structure according to the International Tables for Crystallography vol. A (IUCr, 2016).\n\n**Bibliographic References**:\n\n- IUCr (2016). International Tables for Crystallography vol. A. Space-group Symmetry, Ed. M. I. Aroyo, 6-th edition. Chichester, John Wiley & Sons.",
                "x-optimade-unit": "inapplicable",
                "items": {
                    "$id": "https://schemas.optimade.org/defs/v1.3/properties/optimade/common/wyckoff_position",
                    "title": "Wyckoff position",
                    "x-optimade-type": "string",
                    "x-optimade-definition": {
                        "label": "wyckoff_position_optimade_common",
                        "kind": "property",
                        "version": "1.3.0",
                        "format": "1.2",
                        "name": "wyckoff_position"
                    },
                    "description": "The Wyckoff symbol for a site.",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string"
                    ],
                    "maxLength": 1,
                    "enum": [
                        "a",
                        "b",
                        "c",
                        "d",
                        "e",
                        "f",
                        "g",
                        "h",
                        "i",
                        "j",
                        "k",
                        "l",
                        "m",
                        "n",
                        "o",
                        "p",
                        "q",
                        "r",
                        "s",
                        "t",
                        "u",
                        "v",
                        "w",
                        "x",
                        "y",
                        "z",
                        "\u03b1"
                    ]
                }
            },
            "multiplicity": {
                "x-optimade-type": "integer",
                "x-optimade-unit": "inapplicable",
                "x-compatible": [
                    "https://www.iucr.org/__data/iucr/cifdic_html/3/CORE_DIC/Ispace_group_Wyckoff.multiplicity.html"
                ],
                "type": [
                    "integer",
                    "null"
                ],
                "description": "Multiplicity of the Wyckoff position in the conventional cell."
            },
            "sitesym": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "x-compatible": [
                    "https://www.iucr.org/__data/iucr/cifdic_html/3/CORE_DIC/Ispace_group_Wyckoff.site_symmetry.html"
                ],
                "type": [
                    "string",
                    "null"
                ],
                "description": "The site-symmetry symbol for the subgroup of the space group that leaves the point fixed.\nThe symmetry direction is determined by the Hermann-Mauguin symbol of the space group, as given in International Tables for Crystallography Volume A, Section 2.2.12 (2006)."
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
                "description": "A list of three booleans indicating whether each fractional coordinate contains a free parameter.",
                "items": {
                    "x-optimade-type": "boolean",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "boolean"
                    ],
                    "description": "A boolean indicating if the corresponding coordinate is free."
                }
            },
            "first_orbit_ita": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "string",
                    "null"
                ],
                "description": "Representative coordinate expression following the source convention in the International Tables of Crystallography Volume A (2006), when distinct from `first_orbit`."
            },
            "first_orbit": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "string",
                    "null"
                ],
                "description": "Representative coordinate expression for the Wyckoff position chosen such that the degrees of freedom can be chosen to place it inside the asymmetric unit obtained from cctbx."
            },
            "orbit": {
                "x-optimade-type": "list",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "array",
                    "null"
                ],
                "description": "Full orbit of the Wyckoff position.\nEach item is an affine transformation from the Wyckoff-position parameter vector `(x, y, z)` to one fractional coordinate in the orbit.\nThe matrix part may be singular because special Wyckoff positions can constrain or identify parameters.",
                "items": {
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
                }
            },
            "orbit_mod_centering": {
                "x-optimade-type": "list",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "array",
                    "null"
                ],
                "description": "Representatives of the Wyckoff-position orbit modulo centering translations.\nEach item has the same affine-transformation representation as an item in `orbit`.",
                "items": {
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
                }
            }
        },
        "examples": [
            {
                "letter": "e",
                "multiplicity": 2,
                "sitesym": "1",
                "hasfreedom": [
                    true,
                    true,
                    true
                ],
                "first_orbit": "x,y,z",
                "orbit": [
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
                        ],
                        "xyz": "x,y,z"
                    },
                    {
                        "matrix": [
                            [
                                "-1",
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
                                "-1"
                            ]
                        ],
                        "vector": [
                            "0",
                            "0",
                            "0"
                        ],
                        "xyz": "-x,y,-z"
                    }
                ],
                "orbit_mod_centering": [
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
                        ],
                        "xyz": "x,y,z"
                    },
                    {
                        "matrix": [
                            [
                                "-1",
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
                                "-1"
                            ]
                        ],
                        "vector": [
                            "0",
                            "0",
                            "0"
                        ],
                        "xyz": "-x,y,-z"
                    }
                ]
            }
        ]
    },
    "examples": [
        [
            {
                "letter": "e",
                "multiplicity": 2,
                "sitesym": "1",
                "hasfreedom": [
                    true,
                    true,
                    true
                ],
                "first_orbit": "x,y,z",
                "orbit": [
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
                        ],
                        "xyz": "x,y,z"
                    }
                ],
                "orbit_mod_centering": [
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
                        ],
                        "xyz": "x,y,z"
                    }
                ]
            }
        ]
    ]
}
```