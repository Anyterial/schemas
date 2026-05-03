# Asu (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu.md)**  
**Definition name:** `asu`

**Property name:** Asu  
**Description:** Structured asymmetric-unit description for the space-group setting.  
**Type:** dictionary  

The asymmetric unit is represented as a list of half-space cuts and logical cut expressions in fractional coordinates. Together these cuts define a representative region of the unit cell from which the full space group can generate all equivalent positions.

**Requirements/Conventions**:

- `cuts` contains the complete serialized cut tree.
- `shape_only_cuts` contains only the geometric shape restrictions, omitting some conditional refinements.
- The formatted `asu_*` fields provide compact textual renderings of the same information.

**Examples:**

- `{"cuts": [{"kind": "cut", "ascii": "x0", "xyz": "x>=0", "inclusive": true, "base_symbol": "x0", "normal": ["1", "0"], "const": "0"}, {"kind": "cut", "ascii": "+x1", "xyz": "x<1", "inclusive": false, "base_symbol": "x1", "normal": ["-1", "0"], "const": "1"}], "shape_only_cuts": [{"kind": "cut", "ascii": "x0", "xyz": "x>=0", "inclusive": true, "base_symbol": "x0", "normal": ["1", "0"], "const": "0"}, {"kind": "cut", "ascii": "x1", "xyz": "x<=1", "inclusive": true, "base_symbol": "x1", "normal": ["-1", "0"], "const": "1"}]}`
- `{"cuts": [{"kind": "cut", "ascii": "x0(y0(z2) & y2(z2))", "xyz": "x>=0 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]", "inclusive": true, "base_symbol": "x0", "normal": ["1", "0"], "const": "0", "condition": {"kind": "expr", "ascii": "y0(z2) & y2(z2)", "xyz": "y>=0 [z<=1/2] & y<=1/2 [z<=1/2]", "op": "&", "lhs": {"kind": "cut", "ascii": "y0(z2)", "xyz": "y>=0 [z<=1/2]", "inclusive": true, "base_symbol": "y0", "normal": ["0", "1"], "const": "0", "condition": {"kind": "cut", "ascii": "z2"}}, "rhs": {"kind": "cut", "ascii": "y2(z2)", "xyz": "y<=1/2 [z<=1/2]", "inclusive": true, "base_symbol": "y2", "normal": ["0", "-1"], "const": "1/2", "condition": {"kind": "cut", "ascii": "z2"}}}}, {"kind": "cut", "ascii": "x2(y0(z2) & y2(z2))", "xyz": "x<=1/2 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]", "inclusive": true, "base_symbol": "x2", "normal": ["-1", "0"], "const": "1/2", "condition": {"kind": "expr", "ascii": "y0(z2) & y2(z2)", "xyz": "y>=0 [z<=1/2] & y<=1/2 [z<=1/2]", "op": "&", "lhs": {"kind": "cut", "ascii": "y0(z2)", "xyz": "y>=0 [z<=1/2]", "inclusive": true, "base_symbol": "y0", "normal": ["0", "1"], "const": "0", "condition": {"kind": "cut", "ascii": "z2"}}, "rhs": {"kind": "cut", "ascii": "y2(z2)", "xyz": "y<=1/2 [z<=1/2]", "inclusive": true, "base_symbol": "y2", "normal": ["0", "-1"], "const": "1/2", "condition": {"kind": "cut", "ascii": "z2"}}}}], "shape_only_cuts": [{"kind": "cut", "ascii": "x0", "xyz": "x>=0", "inclusive": true, "base_symbol": "x0", "normal": ["1", "0"], "const": "0"}, {"kind": "cut", "ascii": "x2", "xyz": "x<=1/2", "inclusive": true, "base_symbol": "x2", "normal": ["-1", "0"], "const": "1/2"}]}`

**Formats:** [[JSON](asu.json)] [[MD](asu.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Asu",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "asu",
        "label": "asu_spacegroups"
    },
    "type": [
        "object",
        "null"
    ],
    "description": "Structured asymmetric-unit description for the space-group setting.\n\nThe asymmetric unit is represented as a list of half-space cuts and logical cut expressions in fractional coordinates. Together these cuts define a representative region of the unit cell from which the full space group can generate all equivalent positions.\n\n**Requirements/Conventions**:\n\n- `cuts` contains the complete serialized cut tree.\n- `shape_only_cuts` contains only the geometric shape restrictions, omitting some conditional refinements.\n- The formatted `asu_*` fields provide compact textual renderings of the same information.",
    "x-optimade-unit": "inapplicable",
    "properties": {
        "cuts": {
            "x-optimade-type": "list",
            "type": [
                "array",
                "null"
            ],
            "description": "Complete serialized asymmetric-unit cut tree.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_cut",
                "title": "Asymmetric-unit cut",
                "$comment": "Reusable Anyterial source definition for one serialized asymmetric-unit cut expression.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "asu_cut",
                    "label": "asu_cut_spacegroups"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One serialized asymmetric-unit half-space cut or logical cut expression.\nCut objects may recursively refer to other cut objects through `condition`, `lhs`, and `rhs`.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **kind**: REQUIRED; String.\n      Kind of cut expression, for example a half-space cut or a logical expression.\n\n    - **ascii**: OPTIONAL; String.\n      Compact plain-text rendering of the cut expression.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the cut in fractional `x,y,z` notation.\n\n    - **inclusive**: OPTIONAL; Boolean.\n      Whether the cut boundary is included.\n\n    - **normal**: OPTIONAL; List of 3 Fractions (String).\n      Normal vector of a half-space cut.\n\n    - **const**: OPTIONAL; Fraction (String).\n      Right-hand-side constant of a half-space cut.\n\n    - **condition**, **lhs**, **rhs**: OPTIONAL; Dictionary.\n      Recursive cut-expression objects.",
                "properties": {
                    "kind": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Kind of cut expression."
                    },
                    "ascii": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Plain-text rendering of the cut expression."
                    },
                    "xyz": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Coordinate expression for the cut in `x,y,z` notation."
                    },
                    "inclusive": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether the cut boundary is included."
                    },
                    "base_symbol": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Base symbolic inequality or coordinate label used for the cut."
                    },
                    "normal": {
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
                        "description": "Normal vector of a half-space cut.",
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
                    "const": {
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
                    "op": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Logical operator used when the expression combines two subexpressions."
                    },
                    "lhs": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Left-hand operand for a logical cut expression.",
                        "properties": {
                            "kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Kind of cut expression."
                            },
                            "ascii": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Plain-text rendering of the cut expression."
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the cut in `x,y,z` notation."
                            },
                            "inclusive": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the cut boundary is included."
                            },
                            "base_symbol": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Base symbolic inequality or coordinate label used for the cut."
                            },
                            "normal": {
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
                                "description": "Normal vector of a half-space cut.",
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
                            "const": {
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
                            "op": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Logical operator used when the expression combines two subexpressions."
                            }
                        }
                    },
                    "rhs": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Right-hand operand for a logical cut expression.",
                        "properties": {
                            "kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Kind of cut expression."
                            },
                            "ascii": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Plain-text rendering of the cut expression."
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the cut in `x,y,z` notation."
                            },
                            "inclusive": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the cut boundary is included."
                            },
                            "base_symbol": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Base symbolic inequality or coordinate label used for the cut."
                            },
                            "normal": {
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
                                "description": "Normal vector of a half-space cut.",
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
                            "const": {
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
                            "op": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Logical operator used when the expression combines two subexpressions."
                            }
                        }
                    },
                    "condition": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Optional conditional cut expression that refines when this cut applies.",
                        "properties": {
                            "kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Kind of cut expression."
                            },
                            "ascii": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Plain-text rendering of the cut expression."
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the cut in `x,y,z` notation."
                            },
                            "inclusive": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the cut boundary is included."
                            },
                            "base_symbol": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Base symbolic inequality or coordinate label used for the cut."
                            },
                            "normal": {
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
                                "description": "Normal vector of a half-space cut.",
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
                            "const": {
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
                            "op": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Logical operator used when the expression combines two subexpressions."
                            }
                        }
                    }
                },
                "examples": [
                    {
                        "kind": "cut",
                        "ascii": "x0",
                        "xyz": "x>=0",
                        "inclusive": true,
                        "base_symbol": "x0",
                        "normal": [
                            "1",
                            "0",
                            "0"
                        ],
                        "const": "0"
                    }
                ]
            },
            "x-optimade-unit": "inapplicable"
        },
        "shape_only_cuts": {
            "x-optimade-type": "list",
            "type": [
                "array",
                "null"
            ],
            "description": "Geometric cut tree with conditional refinements omitted.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_cut",
                "title": "Asymmetric-unit cut",
                "$comment": "Reusable Anyterial source definition for one serialized asymmetric-unit cut expression.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "asu_cut",
                    "label": "asu_cut_spacegroups"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One serialized asymmetric-unit half-space cut or logical cut expression.\nCut objects may recursively refer to other cut objects through `condition`, `lhs`, and `rhs`.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **kind**: REQUIRED; String.\n      Kind of cut expression, for example a half-space cut or a logical expression.\n\n    - **ascii**: OPTIONAL; String.\n      Compact plain-text rendering of the cut expression.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the cut in fractional `x,y,z` notation.\n\n    - **inclusive**: OPTIONAL; Boolean.\n      Whether the cut boundary is included.\n\n    - **normal**: OPTIONAL; List of 3 Fractions (String).\n      Normal vector of a half-space cut.\n\n    - **const**: OPTIONAL; Fraction (String).\n      Right-hand-side constant of a half-space cut.\n\n    - **condition**, **lhs**, **rhs**: OPTIONAL; Dictionary.\n      Recursive cut-expression objects.",
                "properties": {
                    "kind": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Kind of cut expression."
                    },
                    "ascii": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Plain-text rendering of the cut expression."
                    },
                    "xyz": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Coordinate expression for the cut in `x,y,z` notation."
                    },
                    "inclusive": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether the cut boundary is included."
                    },
                    "base_symbol": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Base symbolic inequality or coordinate label used for the cut."
                    },
                    "normal": {
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
                        "description": "Normal vector of a half-space cut.",
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
                    "const": {
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
                    "op": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Logical operator used when the expression combines two subexpressions."
                    },
                    "lhs": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Left-hand operand for a logical cut expression.",
                        "properties": {
                            "kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Kind of cut expression."
                            },
                            "ascii": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Plain-text rendering of the cut expression."
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the cut in `x,y,z` notation."
                            },
                            "inclusive": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the cut boundary is included."
                            },
                            "base_symbol": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Base symbolic inequality or coordinate label used for the cut."
                            },
                            "normal": {
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
                                "description": "Normal vector of a half-space cut.",
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
                            "const": {
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
                            "op": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Logical operator used when the expression combines two subexpressions."
                            }
                        }
                    },
                    "rhs": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Right-hand operand for a logical cut expression.",
                        "properties": {
                            "kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Kind of cut expression."
                            },
                            "ascii": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Plain-text rendering of the cut expression."
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the cut in `x,y,z` notation."
                            },
                            "inclusive": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the cut boundary is included."
                            },
                            "base_symbol": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Base symbolic inequality or coordinate label used for the cut."
                            },
                            "normal": {
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
                                "description": "Normal vector of a half-space cut.",
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
                            "const": {
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
                            "op": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Logical operator used when the expression combines two subexpressions."
                            }
                        }
                    },
                    "condition": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Optional conditional cut expression that refines when this cut applies.",
                        "properties": {
                            "kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Kind of cut expression."
                            },
                            "ascii": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Plain-text rendering of the cut expression."
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the cut in `x,y,z` notation."
                            },
                            "inclusive": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the cut boundary is included."
                            },
                            "base_symbol": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Base symbolic inequality or coordinate label used for the cut."
                            },
                            "normal": {
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
                                "description": "Normal vector of a half-space cut.",
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
                            "const": {
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
                            "op": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Logical operator used when the expression combines two subexpressions."
                            }
                        }
                    }
                },
                "examples": [
                    {
                        "kind": "cut",
                        "ascii": "x0",
                        "xyz": "x>=0",
                        "inclusive": true,
                        "base_symbol": "x0",
                        "normal": [
                            "1",
                            "0",
                            "0"
                        ],
                        "const": "0"
                    }
                ]
            },
            "x-optimade-unit": "inapplicable"
        }
    },
    "examples": [
        {
            "cuts": [
                {
                    "kind": "cut",
                    "ascii": "x0",
                    "xyz": "x>=0",
                    "inclusive": true,
                    "base_symbol": "x0",
                    "normal": [
                        "1",
                        "0"
                    ],
                    "const": "0"
                },
                {
                    "kind": "cut",
                    "ascii": "+x1",
                    "xyz": "x<1",
                    "inclusive": false,
                    "base_symbol": "x1",
                    "normal": [
                        "-1",
                        "0"
                    ],
                    "const": "1"
                }
            ],
            "shape_only_cuts": [
                {
                    "kind": "cut",
                    "ascii": "x0",
                    "xyz": "x>=0",
                    "inclusive": true,
                    "base_symbol": "x0",
                    "normal": [
                        "1",
                        "0"
                    ],
                    "const": "0"
                },
                {
                    "kind": "cut",
                    "ascii": "x1",
                    "xyz": "x<=1",
                    "inclusive": true,
                    "base_symbol": "x1",
                    "normal": [
                        "-1",
                        "0"
                    ],
                    "const": "1"
                }
            ]
        },
        {
            "cuts": [
                {
                    "kind": "cut",
                    "ascii": "x0(y0(z2) & y2(z2))",
                    "xyz": "x>=0 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]",
                    "inclusive": true,
                    "base_symbol": "x0",
                    "normal": [
                        "1",
                        "0"
                    ],
                    "const": "0",
                    "condition": {
                        "kind": "expr",
                        "ascii": "y0(z2) & y2(z2)",
                        "xyz": "y>=0 [z<=1/2] & y<=1/2 [z<=1/2]",
                        "op": "&",
                        "lhs": {
                            "kind": "cut",
                            "ascii": "y0(z2)",
                            "xyz": "y>=0 [z<=1/2]",
                            "inclusive": true,
                            "base_symbol": "y0",
                            "normal": [
                                "0",
                                "1"
                            ],
                            "const": "0",
                            "condition": {
                                "kind": "cut",
                                "ascii": "z2"
                            }
                        },
                        "rhs": {
                            "kind": "cut",
                            "ascii": "y2(z2)",
                            "xyz": "y<=1/2 [z<=1/2]",
                            "inclusive": true,
                            "base_symbol": "y2",
                            "normal": [
                                "0",
                                "-1"
                            ],
                            "const": "1/2",
                            "condition": {
                                "kind": "cut",
                                "ascii": "z2"
                            }
                        }
                    }
                },
                {
                    "kind": "cut",
                    "ascii": "x2(y0(z2) & y2(z2))",
                    "xyz": "x<=1/2 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]",
                    "inclusive": true,
                    "base_symbol": "x2",
                    "normal": [
                        "-1",
                        "0"
                    ],
                    "const": "1/2",
                    "condition": {
                        "kind": "expr",
                        "ascii": "y0(z2) & y2(z2)",
                        "xyz": "y>=0 [z<=1/2] & y<=1/2 [z<=1/2]",
                        "op": "&",
                        "lhs": {
                            "kind": "cut",
                            "ascii": "y0(z2)",
                            "xyz": "y>=0 [z<=1/2]",
                            "inclusive": true,
                            "base_symbol": "y0",
                            "normal": [
                                "0",
                                "1"
                            ],
                            "const": "0",
                            "condition": {
                                "kind": "cut",
                                "ascii": "z2"
                            }
                        },
                        "rhs": {
                            "kind": "cut",
                            "ascii": "y2(z2)",
                            "xyz": "y<=1/2 [z<=1/2]",
                            "inclusive": true,
                            "base_symbol": "y2",
                            "normal": [
                                "0",
                                "-1"
                            ],
                            "const": "1/2",
                            "condition": {
                                "kind": "cut",
                                "ascii": "z2"
                            }
                        }
                    }
                }
            ],
            "shape_only_cuts": [
                {
                    "kind": "cut",
                    "ascii": "x0",
                    "xyz": "x>=0",
                    "inclusive": true,
                    "base_symbol": "x0",
                    "normal": [
                        "1",
                        "0"
                    ],
                    "const": "0"
                },
                {
                    "kind": "cut",
                    "ascii": "x2",
                    "xyz": "x<=1/2",
                    "inclusive": true,
                    "base_symbol": "x2",
                    "normal": [
                        "-1",
                        "0"
                    ],
                    "const": "1/2"
                }
            ]
        }
    ]
}
```