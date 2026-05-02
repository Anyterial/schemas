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

- `[{"hall_entry": "p_1", "it_number": 1, "crystal_system": "triclinic", "orthogonal_affine_normalizer_cosets": [{"matrix": [["-1", "0", "0"], ["0", "-1", "0"], ["0", "0", "-1"]], "vector": ["0", "0", "0"], "xyz": "-x,-y,-z", "det": -1, "is_orthogonal": true, "compatible_systems": ["triclinic", "monoclinic", "orthorhombic", "tetragonal", "trigonal", "hexagonal", "cubic"]}], "affine_normalizer_cosets": [{"matrix": [["-1", "0", "0"], ["0", "-1", "0"], ["0", "0", "-1"]], "vector": ["0", "0", "0"], "xyz": "-x,-y,-z", "det": -1, "is_orthogonal": true, "compatible_systems": ["triclinic", "monoclinic", "orthorhombic", "tetragonal", "trigonal", "hexagonal", "cubic"]}], "n_orthogonal_cosets": 47, "n_cosets": 63, "candidate_sets": {"orthogonal_affine_normalizer_cosets": {"candidate_set": "signed_permutation_matrices", "n_linear_candidates": 48, "n_raw_candidates": 96, "n_coset_representatives_before_metric_filter": 47}, "affine_normalizer_cosets": {"candidate_set": "bounded_unimodular_integer_matrices", "n_linear_candidates": 6960, "n_raw_candidates": 13920, "n_coset_representatives_before_metric_filter": 63, "bounds": {"det_abs": 1, "max_abs_linear_entry": 1}}}}]`

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
        "description": "One affine-normalizer coset-data row for a single Hall setting.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **hall\\_entry**: REQUIRED; String.\n      Normalized Hall entry identifying the Hall setting represented by this row.\n\n    - **it\\_number**: REQUIRED; Integer.\n      International Tables space-group number of the represented Hall setting.\n\n    - **crystal\\_system**: REQUIRED; String.\n      Crystal system of the represented Hall setting.\n\n    - **orthogonal\\_affine\\_normalizer\\_cosets**: REQUIRED; List of dictionaries.\n      Signed-permutation affine normalizer coset representatives modulo the space group.\n      Each item follows `/defs/v0.1/properties/symmetry/affine_transformation`.\n\n    - **affine\\_normalizer\\_cosets**: REQUIRED; List of dictionaries.\n      Bounded affine normalizer coset representatives modulo the space group.\n      Each item follows `/defs/v0.1/properties/symmetry/affine_transformation`.\n\n    - **n\\_orthogonal\\_cosets**: REQUIRED; Integer.\n      Number of representatives in `orthogonal_affine_normalizer_cosets`.\n\n    - **n\\_cosets**: REQUIRED; Integer.\n      Number of representatives in `affine_normalizer_cosets`.\n\n    - **candidate\\_sets**: REQUIRED; Dictionary.\n      Generator bookkeeping for the finite candidate sets used to produce the two representative lists.",
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
                "description": "Runtime list of bounded affine normalizer coset representatives modulo the space group.\nEach item is one finite listed representative and follows `/properties/symmetry/affine_transformation`.\nThe list is a bounded representative table, not a complete infinite affine normalizer.",
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
                                "-1"
                            ]
                        ],
                        "vector": [
                            "0",
                            "0",
                            "0"
                        ],
                        "xyz": "-x,-y,-z",
                        "det": -1,
                        "is_orthogonal": true,
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
                                "-1"
                            ]
                        ],
                        "vector": [
                            "0",
                            "0",
                            "0"
                        ],
                        "xyz": "-x,-y,-z",
                        "det": -1,
                        "is_orthogonal": true,
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