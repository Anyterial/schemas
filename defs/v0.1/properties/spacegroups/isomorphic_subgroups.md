# Isomorphic subgroup transforms (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups.md)**  
**Definition name:** `isomorphic_subgroups`

**Property name:** Isomorphic subgroup transforms  
**Description:** Isomorphic subgroup transforms of bounded index for one parent setting or space-group type.
An isomorphic subgroup has the same space-group type as the parent but is embedded with a finite index, usually corresponding to an enlarged unit cell or a sublattice choice.
These transforms are useful for algorithms that need to enumerate same-type subgroup embeddings, compare structures under supercell changes, or construct bounded same-space-group refinement paths.  
**Type:** dictionary  

The transform records use the basis-transform convention represented by `pmat` and `pvec`.
The `index` field is the subgroup index and equals the determinant factor of the basis transformation.
The generator currently searches indices up to its configured maximum index and deduplicates equivalent transforms under normalizer equivalence.

**Requirements/Conventions**:

- It MUST be a dictionary containing an `items` list.
- Each item in `items` MUST describe one exact isomorphic subgroup transform.
- Matrix and vector entries MUST be exact strings, using integer strings or fraction strings as appropriate.

**Examples:**

- `{"items": [{"index": 2, "wyckoff_splitting": {"a": [["a", "x,y,z", [["1", "0", "0", "0"], ["0", "1", "0", "0"], ["0", "0", "1/2", "1/2"]]], ["a", "x,y,z", [["1", "0", "0", "0"], ["0", "1", "0", "0"], ["0", "0", "1/2", "0"]]]]}, "pmat": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "2"]], "pvec": ["0", "0", "0"]}]}`

**Formats:** [[JSON](isomorphic_subgroups.json)] [[MD](isomorphic_subgroups.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Isomorphic subgroup transforms",
    "$comment": "Anyterial keyed table of bounded-index isomorphic subgroup transforms.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "isomorphic_subgroups",
        "label": "isomorphic_subgroups_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Isomorphic subgroup transforms of bounded index for one parent setting or space-group type.\nAn isomorphic subgroup has the same space-group type as the parent but is embedded with a finite index, usually corresponding to an enlarged unit cell or a sublattice choice.\nThese transforms are useful for algorithms that need to enumerate same-type subgroup embeddings, compare structures under supercell changes, or construct bounded same-space-group refinement paths.\n\nThe transform records use the basis-transform convention represented by `pmat` and `pvec`.\nThe `index` field is the subgroup index and equals the determinant factor of the basis transformation.\nThe generator currently searches indices up to its configured maximum index and deduplicates equivalent transforms under normalizer equivalence.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary containing an `items` list.\n- Each item in `items` MUST describe one exact isomorphic subgroup transform.\n- Matrix and vector entries MUST be exact strings, using integer strings or fraction strings as appropriate.",
    "properties": {
        "items": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Isomorphic subgroup transform records for one parent key.",
            "items": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One exact isomorphic subgroup transform.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **index**: REQUIRED; Integer.\n      Subgroup index of the isomorphic embedding.\n\n    - **pmat**: REQUIRED; Exact 3x3 matrix.\n      Matrix part of the basis transform.\n\n    - **pvec**: REQUIRED; List of 3 Fractions (String).\n      Origin-shift vector of the basis transform.\n\n    - **wyckoff\\_splitting**: REQUIRED; Dictionary.\n      Wyckoff-position splitting data induced by this transform.",
                "properties": {
                    "index": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index",
                        "title": "Index",
                        "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                        "x-optimade-type": "integer",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "index",
                            "label": "index_spacegroups"
                        },
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Subgroup or transform index. For subgroup transforms it is the crystallographic subgroup index `[G:H]`, equal to the determinant factor of the basis transformation when applicable.",
                        "x-optimade-unit": "inapplicable",
                        "examples": [
                            2,
                            4
                        ]
                    },
                    "pmat": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pmat",
                        "title": "Basis transformation matrix",
                        "$comment": "Anyterial space-group property definition inheriting the common semantic `pmat` definition.",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "pmat",
                            "label": "pmat_spacegroups"
                        },
                        "description": "Matrix part of a crystallographic basis or setting transformation.\nThis emitted space-group property uses the common `/properties/symmetry/pmat` definition for its nested value shape and dimensional metadata.",
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
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
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pvec",
                        "title": "Basis transformation origin shift",
                        "$comment": "Anyterial space-group property definition inheriting the common semantic `pvec` definition.",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "pvec",
                            "label": "pvec_spacegroups"
                        },
                        "description": "Translation or origin-shift vector of a crystallographic basis or setting transformation.\nThis emitted space-group property uses the common `/properties/symmetry/pvec` definition for its nested value shape and dimensional metadata.",
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
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
                    "wyckoff_splitting": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_splitting",
                        "title": "Wyckoff splitting",
                        "$comment": "Anyterial property definition for Wyckoff-position splitting data attached to subgroup transforms.",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "wyckoff_splitting",
                            "label": "wyckoff_splitting_spacegroups"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Wyckoff-position splitting data associated with a subgroup or same-space-group transform.\nThe map is keyed by parent Wyckoff letter.\nEach value is an ordered list of subgroup Wyckoff-position assignments or coordinate expressions as emitted by the generator.\n\n**Requirements/Conventions**:\n\n- Dynamic keys MUST be parent Wyckoff letters.\n- Values MUST be lists.\n- Each listed item is currently a compact generator record whose exact shape is defined by the parent transform table.",
                        "properties": {},
                        "examples": [
                            {
                                "c": [
                                    [
                                        "e",
                                        "x",
                                        "y",
                                        "z"
                                    ],
                                    [
                                        "e",
                                        "-x",
                                        "y",
                                        "-z"
                                    ]
                                ]
                            }
                        ]
                    }
                }
            }
        }
    },
    "examples": [
        {
            "items": [
                {
                    "index": 2,
                    "wyckoff_splitting": {
                        "a": [
                            [
                                "a",
                                "x,y,z",
                                [
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
                                        "1/2",
                                        "1/2"
                                    ]
                                ]
                            ],
                            [
                                "a",
                                "x,y,z",
                                [
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
                                        "1/2",
                                        "0"
                                    ]
                                ]
                            ]
                        ]
                    },
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
    ]
}
```