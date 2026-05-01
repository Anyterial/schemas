# Affine normalizer coset data (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_coset_data`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_coset_data.md)**  
**Definition name:** `affine_normalizer_coset_data`

**Property name:** Affine normalizer coset data  
**Description:** Ordered table of bounded affine normalizer coset-representative data for crystallographic space groups, with one item for each Hall setting.
The affine normalizer of a space group describes affine mappings that send the space group to itself.
In practical algorithms this information is useful after a candidate space-group setting has been identified, because additional normalizer representatives can be applied to explore equivalent descriptions, equivalent origin choices, or equivalent embeddings without changing the underlying space group.
The representatives are listed modulo the space group itself, so each listed operation represents an equivalence class of normalizer operations rather than every operation in that class.  
**Type:** list  

The `orthogonal_affine_normalizer_cosets` list is the signed-permutation subset of representatives.
The `affine_normalizer_cosets` list is generated from a bounded set of unimodular integer linear parts and may include non-orthogonal representatives.
Both lists are finite bounded tables and MUST NOT be interpreted as complete infinite affine normalizers.
Each listed representative carries `compatible_systems`, which states the crystal metric systems for which the representative preserves the metric constraints.

**Requirements/Conventions**:

- It MUST be a list of dictionaries.
- The list order MUST match the generator's Hall-setting order.
- The companion `hall_symbol_to_affine_normalizer_coset_data` index maps normalized Hall entries to zero-based positions in this list.
- Each dictionary MUST contain a `hall_entry` value equal to the Hall-entry key used by the companion index.
- Count fields MUST equal the length of their corresponding representative lists.
- Matrix and vector entries inside representatives MUST be exact strings, using integer strings or fraction strings as appropriate.
- The `candidate_sets` dictionary records generation bookkeeping for the finite candidate searches and is not itself a crystallographic normalizer object.

**Examples:**

- `[{"hall_entry": "p_1", "it_number": 1, "crystal_system": "triclinic", "orthogonal_affine_normalizer_cosets": [{"rmat": [["-1", "0", "0"], ["0", "-1", "0"], ["0", "0", "-1"]], "tvec": ["0", "0", "0"], "xyz": "-x,-y,-z", "rmat_det": -1, "rmat_is_orthogonal": true, "compatible_systems": ["triclinic", "monoclinic", "orthorhombic", "tetragonal", "trigonal", "hexagonal", "cubic"]}], "affine_normalizer_cosets": [{"rmat": [["-1", "0", "0"], ["0", "-1", "0"], ["0", "0", "-1"]], "tvec": ["0", "0", "0"], "xyz": "-x,-y,-z", "rmat_det": -1, "rmat_is_orthogonal": true, "compatible_systems": ["triclinic", "monoclinic", "orthorhombic", "tetragonal", "trigonal", "hexagonal", "cubic"]}], "n_orthogonal_cosets": 47, "n_cosets": 63, "candidate_sets": {"orthogonal_affine_normalizer_cosets": {"candidate_set": "signed_permutation_matrices", "n_linear_candidates": 48, "n_raw_candidates": 96, "n_coset_representatives_before_metric_filter": 47}, "affine_normalizer_cosets": {"candidate_set": "bounded_unimodular_integer_matrices", "n_linear_candidates": 6960, "n_raw_candidates": 13920, "n_coset_representatives_before_metric_filter": 63, "bounds": {"det_abs": 1, "max_abs_linear_entry": 1}}}}]`

**Formats:** [[JSON](affine_normalizer_coset_data.json)] [[MD](affine_normalizer_coset_data.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_coset_data",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Affine normalizer coset data",
    "$comment": "Ordered Anyterial table of bounded affine normalizer coset-representative data by Hall setting.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "affine_normalizer_coset_data",
        "label": "affine_normalizer_coset_data_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Ordered table of bounded affine normalizer coset-representative data for crystallographic space groups, with one item for each Hall setting.\nThe affine normalizer of a space group describes affine mappings that send the space group to itself.\nIn practical algorithms this information is useful after a candidate space-group setting has been identified, because additional normalizer representatives can be applied to explore equivalent descriptions, equivalent origin choices, or equivalent embeddings without changing the underlying space group.\nThe representatives are listed modulo the space group itself, so each listed operation represents an equivalence class of normalizer operations rather than every operation in that class.\n\nThe `orthogonal_affine_normalizer_cosets` list is the signed-permutation subset of representatives.\nThe `affine_normalizer_cosets` list is generated from a bounded set of unimodular integer linear parts and may include non-orthogonal representatives.\nBoth lists are finite bounded tables and MUST NOT be interpreted as complete infinite affine normalizers.\nEach listed representative carries `compatible_systems`, which states the crystal metric systems for which the representative preserves the metric constraints.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- The list order MUST match the generator's Hall-setting order.\n- The companion `hall_symbol_to_affine_normalizer_coset_data` index maps normalized Hall entries to zero-based positions in this list.\n- Each dictionary MUST contain a `hall_entry` value equal to the Hall-entry key used by the companion index.\n- Count fields MUST equal the length of their corresponding representative lists.\n- Matrix and vector entries inside representatives MUST be exact strings, using integer strings or fraction strings as appropriate.\n- The `candidate_sets` dictionary records generation bookkeeping for the finite candidate searches and is not itself a crystallographic normalizer object.",
    "items": {
        "x-optimade-type": "dictionary",
        "x-optimade-unit": "inapplicable",
        "type": [
            "object",
            "null"
        ],
        "description": "One affine-normalizer coset-data row for a single Hall setting.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **hall\\_entry**: REQUIRED; String.\n      Normalized Hall entry identifying the Hall setting represented by this row.\n\n    - **it\\_number**: REQUIRED; Integer.\n      International Tables space-group number of the represented Hall setting.\n\n    - **crystal\\_system**: REQUIRED; String.\n      Crystal system of the represented Hall setting.\n\n    - **orthogonal\\_affine\\_normalizer\\_cosets**: REQUIRED; List of dictionaries.\n      Signed-permutation affine normalizer coset representatives modulo the space group.\n      Each item follows `/defs/v0.1/properties/symmetry/normalizer_representative`.\n\n    - **affine\\_normalizer\\_cosets**: REQUIRED; List of dictionaries.\n      Bounded affine normalizer coset representatives modulo the space group.\n      Each item follows `/defs/v0.1/properties/symmetry/normalizer_representative`.\n\n    - **n\\_orthogonal\\_cosets**: REQUIRED; Integer.\n      Number of representatives in `orthogonal_affine_normalizer_cosets`.\n\n    - **n\\_cosets**: REQUIRED; Integer.\n      Number of representatives in `affine_normalizer_cosets`.\n\n    - **candidate\\_sets**: REQUIRED; Dictionary.\n      Generator bookkeeping for the finite candidate sets used to produce the two representative lists.",
        "properties": {
            "hall_entry": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry",
                "title": "Hall entry",
                "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                "x-optimade-type": "string",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "hall_entry",
                    "label": "hall_entry_spacegroups"
                },
                "type": [
                    "string",
                    "null"
                ],
                "description": "Normalized Hall-table entry key used internally by the generated datasets.\n\nThe value is derived from the Hall symbol by using lowercase letters and underscores in place of spaces. It is stable for lookup within these data files, while the display Hall symbol is provided separately by `hall` and its formatted variants.\n\n**Requirements/Conventions**:\n\n- This field identifies a concrete Hall setting, not only an IT space-group type.\n- The same value is normally used as the key of the containing `spacegroups` map.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    "p_1",
                    "-p_1"
                ]
            },
            "it_number": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number",
                "title": "International Tables Space-Group Number",
                "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
                "x-optimade-type": "integer",
                "x-compatibility": [
                    "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_it_number"
                ],
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "it_number",
                    "label": "it_number_spacegroups"
                },
                "type": [
                    "integer",
                    "null"
                ],
                "description": "The International Tables space-group number.\n\nThis integer identifies the space-group type numbered 1 through 230 in International Tables for Crystallography. Multiple Hall settings can share the same `it_number`.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    1,
                    5
                ]
            },
            "crystal_system": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/crystal_system",
                "title": "Crystal System",
                "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
                "x-optimade-type": "string",
                "x-compatibility": [
                    "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.crystal_system.html"
                ],
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "crystal_system",
                    "label": "crystal_system_spacegroups"
                },
                "type": [
                    "string",
                    "null"
                ],
                "description": "The crystal system of the space group or point group.\n\nValues use the conventional crystallographic system names such as triclinic, monoclinic, orthorhombic, tetragonal, trigonal, hexagonal, and cubic.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    "triclinic",
                    "monoclinic"
                ]
            },
            "orthogonal_affine_normalizer_cosets": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer_cosets",
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
                "description": "Runtime list of orthogonal signed-permutation affine normalizer coset representatives modulo the space group.\nEach item is one finite listed representative and follows `/properties/symmetry/normalizer_representative`.\nThe list is a bounded representative table, not a complete infinite affine normalizer.",
                "items": {
                    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/normalizer_representative",
                    "title": "Normalizer representative",
                    "$comment": "Reusable Anyterial definition for one listed Euclidean or affine normalizer representative.",
                    "x-optimade-type": "dictionary",
                    "x-optimade-definition": {
                        "kind": "property",
                        "version": "0.1.0",
                        "format": "1.3",
                        "name": "normalizer_representative",
                        "label": "normalizer_representative_symmetry"
                    },
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "object",
                        "null"
                    ],
                    "description": "One listed representative of a Euclidean or affine normalizer operation or coset.\nIn affine-normalizer tables the representative is taken modulo the space group, so it should be read as one representative of an equivalence class rather than as the only operation in that class.\nBounded affine-normalizer tables enumerate only the finite candidate set documented by the generator.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Linear part when the representative is expressed as a same-setting affine operation.\n\n    - **tvec**: OPTIONAL; List of 3 Fractions (String).\n      Translation part when the representative is expressed as a same-setting affine operation.\n\n    - **pmat**: OPTIONAL; Exact 3x3 matrix.\n      Matrix part when the representative is expressed as a basis or setting transform.\n\n    - **pvec**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift when the representative is expressed as a basis or setting transform.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for display and debugging.\n\n    - **compatible\\_systems**: OPTIONAL; List of strings.\n      Crystal metric systems for which a bounded affine candidate is compatible.\n\n    - **operation\\_kind**: OPTIONAL; String.\n      Generator classification of the operation.\n\n    - **normalizer\\_kind**: OPTIONAL; String.\n      Classification of the normalizer contribution.",
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
                        "pmat": {
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pmat",
                            "title": "Basis transformation matrix",
                            "$comment": "Reusable Anyterial definition for the matrix part of a crystallographic basis or setting transformation.",
                            "x-optimade-type": "list",
                            "x-optimade-definition": {
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "pmat",
                                "label": "pmat_symmetry"
                            },
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "array",
                                "null"
                            ],
                            "description": "Matrix part of a crystallographic basis or setting transformation.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings so that exact rational or algebraic values can be preserved without floating-point rounding.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- The parent transform definition specifies the coordinate convention and whether the matrix maps from a source setting to a target setting or conversely.",
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
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec",
                            "title": "Basis transformation origin shift",
                            "$comment": "Reusable Anyterial definition for the translation/origin-shift part of a crystallographic basis or setting transformation.",
                            "x-optimade-type": "list",
                            "x-optimade-definition": {
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "pvec",
                                "label": "pvec_symmetry"
                            },
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "array",
                                "null"
                            ],
                            "description": "Translation or origin-shift part of a crystallographic basis or setting transformation.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- The parent transform definition specifies the source and target setting convention for the transformation.",
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
                        "xyz": {
                            "x-optimade-type": "string",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "Coordinate expression for the representative in `x,y,z` notation."
                        },
                        "rmat_det": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "Determinant of the same-setting linear part, when supplied."
                        },
                        "rmat_is_orthogonal": {
                            "x-optimade-type": "boolean",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "boolean",
                                "null"
                            ],
                            "description": "Whether `rmat` is orthogonal, when supplied."
                        },
                        "pmat_is_orthogonal": {
                            "x-optimade-type": "boolean",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "boolean",
                                "null"
                            ],
                            "description": "Whether `pmat` is orthogonal, when supplied."
                        },
                        "compatible_systems": {
                            "x-optimade-type": "list",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "array",
                                "null"
                            ],
                            "description": "Crystal metric systems compatible with the candidate representative.",
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
                            "description": "Generator classification of the operation."
                        },
                        "normalizer_kind": {
                            "x-optimade-type": "string",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "Classification of the normalizer contribution."
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
                            "rmat_is_orthogonal": true,
                            "compatible_systems": [
                                "monoclinic",
                                "orthorhombic"
                            ]
                        }
                    ]
                },
                "examples": [
                    [
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
                ]
            },
            "affine_normalizer_cosets": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_cosets",
                "title": "Affine normalizer cosets",
                "$comment": "Anyterial normalizer-coset list property using the common normalizer-representative definition.",
                "x-optimade-type": "list",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "affine_normalizer_cosets",
                    "label": "affine_normalizer_cosets_spacegroups"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "array",
                    "null"
                ],
                "description": "Runtime list of bounded affine normalizer coset representatives modulo the space group.\nEach item is one finite listed representative and follows `/properties/symmetry/normalizer_representative`.\nThe list is a bounded representative table, not a complete infinite affine normalizer.",
                "items": {
                    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/normalizer_representative",
                    "title": "Normalizer representative",
                    "$comment": "Reusable Anyterial definition for one listed Euclidean or affine normalizer representative.",
                    "x-optimade-type": "dictionary",
                    "x-optimade-definition": {
                        "kind": "property",
                        "version": "0.1.0",
                        "format": "1.3",
                        "name": "normalizer_representative",
                        "label": "normalizer_representative_symmetry"
                    },
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "object",
                        "null"
                    ],
                    "description": "One listed representative of a Euclidean or affine normalizer operation or coset.\nIn affine-normalizer tables the representative is taken modulo the space group, so it should be read as one representative of an equivalence class rather than as the only operation in that class.\nBounded affine-normalizer tables enumerate only the finite candidate set documented by the generator.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Linear part when the representative is expressed as a same-setting affine operation.\n\n    - **tvec**: OPTIONAL; List of 3 Fractions (String).\n      Translation part when the representative is expressed as a same-setting affine operation.\n\n    - **pmat**: OPTIONAL; Exact 3x3 matrix.\n      Matrix part when the representative is expressed as a basis or setting transform.\n\n    - **pvec**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift when the representative is expressed as a basis or setting transform.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for display and debugging.\n\n    - **compatible\\_systems**: OPTIONAL; List of strings.\n      Crystal metric systems for which a bounded affine candidate is compatible.\n\n    - **operation\\_kind**: OPTIONAL; String.\n      Generator classification of the operation.\n\n    - **normalizer\\_kind**: OPTIONAL; String.\n      Classification of the normalizer contribution.",
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
                        "pmat": {
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pmat",
                            "title": "Basis transformation matrix",
                            "$comment": "Reusable Anyterial definition for the matrix part of a crystallographic basis or setting transformation.",
                            "x-optimade-type": "list",
                            "x-optimade-definition": {
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "pmat",
                                "label": "pmat_symmetry"
                            },
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "array",
                                "null"
                            ],
                            "description": "Matrix part of a crystallographic basis or setting transformation.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings so that exact rational or algebraic values can be preserved without floating-point rounding.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- The parent transform definition specifies the coordinate convention and whether the matrix maps from a source setting to a target setting or conversely.",
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
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec",
                            "title": "Basis transformation origin shift",
                            "$comment": "Reusable Anyterial definition for the translation/origin-shift part of a crystallographic basis or setting transformation.",
                            "x-optimade-type": "list",
                            "x-optimade-definition": {
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "pvec",
                                "label": "pvec_symmetry"
                            },
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "array",
                                "null"
                            ],
                            "description": "Translation or origin-shift part of a crystallographic basis or setting transformation.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- The parent transform definition specifies the source and target setting convention for the transformation.",
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
                        "xyz": {
                            "x-optimade-type": "string",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "Coordinate expression for the representative in `x,y,z` notation."
                        },
                        "rmat_det": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "Determinant of the same-setting linear part, when supplied."
                        },
                        "rmat_is_orthogonal": {
                            "x-optimade-type": "boolean",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "boolean",
                                "null"
                            ],
                            "description": "Whether `rmat` is orthogonal, when supplied."
                        },
                        "pmat_is_orthogonal": {
                            "x-optimade-type": "boolean",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "boolean",
                                "null"
                            ],
                            "description": "Whether `pmat` is orthogonal, when supplied."
                        },
                        "compatible_systems": {
                            "x-optimade-type": "list",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "array",
                                "null"
                            ],
                            "description": "Crystal metric systems compatible with the candidate representative.",
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
                            "description": "Generator classification of the operation."
                        },
                        "normalizer_kind": {
                            "x-optimade-type": "string",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "Classification of the normalizer contribution."
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
                            "rmat_is_orthogonal": true,
                            "compatible_systems": [
                                "monoclinic",
                                "orthorhombic"
                            ]
                        }
                    ]
                },
                "examples": [
                    [
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
                ]
            },
            "n_orthogonal_cosets": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_orthogonal_cosets",
                "title": "N Orthogonal Cosets",
                "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                "x-optimade-type": "integer",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "n_orthogonal_cosets",
                    "label": "n_orthogonal_cosets_spacegroups"
                },
                "type": [
                    "integer",
                    "null"
                ],
                "description": "Number of orthogonal affine normalizer coset representatives stored for the setting.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    47,
                    23
                ]
            },
            "n_cosets": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_cosets",
                "title": "N Cosets",
                "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                "x-optimade-type": "integer",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "n_cosets",
                    "label": "n_cosets_spacegroups"
                },
                "type": [
                    "integer",
                    "null"
                ],
                "description": "Number of affine normalizer coset representatives stored for the setting.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    63,
                    31
                ]
            },
            "candidate_sets": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "Generator bookkeeping for the finite candidate sets used to produce the stored affine-normalizer coset representatives.\nThis dictionary records how many candidate affine operations were considered before and after quotienting modulo the space group and before applying metric-compatibility filters.",
                "properties": {
                    "orthogonal_affine_normalizer_cosets": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Candidate-set metadata for the orthogonal signed-permutation representative list.",
                        "properties": {
                            "candidate_set": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Name of the linear candidate set used by the generator."
                            },
                            "n_linear_candidates": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Number of linear matrices in the raw candidate set."
                            },
                            "n_raw_candidates": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Number of affine candidates generated before deduplication modulo the space group."
                            },
                            "n_coset_representatives_before_metric_filter": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Number of coset representatives before filtering by crystal metric compatibility."
                            }
                        }
                    },
                    "affine_normalizer_cosets": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Candidate-set metadata for the bounded unimodular-integer representative list.",
                        "properties": {
                            "candidate_set": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Name of the linear candidate set used by the generator."
                            },
                            "n_linear_candidates": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Number of linear matrices in the raw candidate set."
                            },
                            "n_raw_candidates": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Number of affine candidates generated before deduplication modulo the space group."
                            },
                            "n_coset_representatives_before_metric_filter": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Number of coset representatives before filtering by crystal metric compatibility."
                            },
                            "bounds": {
                                "x-optimade-type": "dictionary",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "object",
                                    "null"
                                ],
                                "description": "Bounds that define the finite bounded unimodular-integer linear candidate set.",
                                "properties": {
                                    "det_abs": {
                                        "x-optimade-type": "integer",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "integer",
                                            "null"
                                        ],
                                        "description": "Required absolute determinant of every bounded linear candidate."
                                    },
                                    "max_abs_linear_entry": {
                                        "x-optimade-type": "integer",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "integer",
                                            "null"
                                        ],
                                        "description": "Maximum absolute value allowed for entries of the bounded integer linear candidates."
                                    }
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
                "hall_entry": "p_1",
                "it_number": 1,
                "crystal_system": "triclinic",
                "orthogonal_affine_normalizer_cosets": [
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
                                "-1"
                            ]
                        ],
                        "tvec": [
                            "0",
                            "0",
                            "0"
                        ],
                        "xyz": "-x,-y,-z",
                        "rmat_det": -1,
                        "rmat_is_orthogonal": true,
                        "compatible_systems": [
                            "triclinic",
                            "monoclinic",
                            "orthorhombic",
                            "tetragonal",
                            "trigonal",
                            "hexagonal",
                            "cubic"
                        ]
                    }
                ],
                "affine_normalizer_cosets": [
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
                                "-1"
                            ]
                        ],
                        "tvec": [
                            "0",
                            "0",
                            "0"
                        ],
                        "xyz": "-x,-y,-z",
                        "rmat_det": -1,
                        "rmat_is_orthogonal": true,
                        "compatible_systems": [
                            "triclinic",
                            "monoclinic",
                            "orthorhombic",
                            "tetragonal",
                            "trigonal",
                            "hexagonal",
                            "cubic"
                        ]
                    }
                ],
                "n_orthogonal_cosets": 47,
                "n_cosets": 63,
                "candidate_sets": {
                    "orthogonal_affine_normalizer_cosets": {
                        "candidate_set": "signed_permutation_matrices",
                        "n_linear_candidates": 48,
                        "n_raw_candidates": 96,
                        "n_coset_representatives_before_metric_filter": 47
                    },
                    "affine_normalizer_cosets": {
                        "candidate_set": "bounded_unimodular_integer_matrices",
                        "n_linear_candidates": 6960,
                        "n_raw_candidates": 13920,
                        "n_coset_representatives_before_metric_filter": 63,
                        "bounds": {
                            "det_abs": 1,
                            "max_abs_linear_entry": 1
                        }
                    }
                }
            }
        ]
    ]
}
```