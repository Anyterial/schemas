# Anyterial point group symmetry fields (entrytype)

This page documents an [OPTIMADE](https://www.optimade.org/) [Entrytype Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/entrytypes/pointgroups`](https://schemas.anyterial.se/defs/v0.1/entrytypes/pointgroups.md)**  
**Definition name:** `pointgroups`

**Entrytype name:** Anyterial point group symmetry fields  
  

**Formats:** [[JSON](pointgroups.json)] [[MD](pointgroups.md)]

This entrytype defines the following properties:

* **[ID](https://schemas.optimade.org/defs/v1.2/properties/core/id.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/id`](https://schemas.optimade.org/defs/v1.2/properties/core/id.md)  
  A unique string referencing a specific entry in the database.

    **Requirements/Conventions:**  

    - **Support:** MUST be supported by all implementations, MUST NOT be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MUST always be included in the response.
    - Taken together, the ID and entry type MUST uniquely identify the entry.
    - Reasonably short IDs are encouraged and SHOULD NOT be longer than 255 characters.
    - IDs MAY change over time.


* **[type](https://schemas.optimade.org/defs/v1.2/properties/core/type.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/type`](https://schemas.optimade.org/defs/v1.2/properties/core/type.md)  
  The name of the type of an entry.

    **Requirements/Conventions:**  

    - **Support:** MUST be supported by all implementations, MUST NOT be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MUST always be included in the response.
    - MUST be an existing entry type.
    - The entry of type <type> and ID <id> MUST be returned in response to a request for /<type>/<id> under the versioned or unversioned base URL serving the API.


* **[immutable ID (immutable_id)](https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id`](https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id.md)  
  The entry's immutable ID (e.g., a UUID).

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MAY be included by default in the response.
    - This is important for databases having preferred IDs that point to "the latest version" of a record, but still offer access to older variants.
    - This ID maps to the version-specific record, in case it changes in the future.


* **[last modified (last_modified)](https://schemas.optimade.org/defs/v1.2/properties/core/last_modified.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/last_modified`](https://schemas.optimade.org/defs/v1.2/properties/core/last_modified.md)  
  Date and time representing when the entry was last modified.

    **Requirements/Conventions:**  

    - **Support:** SHOULD be supported by all implementations, i.e., SHOULD NOT be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MUST be included by default in the response.

* **[Character Table Complex (character_table_complex)](../properties/pointgroups/character_table_complex.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_complex`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_complex.md)  
  Complex irreducible character table of the crystallographic point group. Rows correspond to complex irreducible representations and columns follow the order of `conjugacy_classes`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Character Table Real (character_table_real)](../properties/pointgroups/character_table_real.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_real`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_real.md)  
  Real irreducible character table of the crystallographic point group. Rows correspond to real irreducible representations and columns follow the order of `conjugacy_classes`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Conjugacy Classes (conjugacy_classes)](../properties/pointgroups/conjugacy_classes.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/conjugacy_classes`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/conjugacy_classes.md)  
  Conjugacy classes of a crystallographic point group. Each class lists its member operation indices, a representative operation, a conventional class label, and operation-type metadata used by the character tables.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Crystal System (crystal_system)](../properties/pointgroups/crystal_system.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system.md)  
  The crystal system of the space group or point group.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    Values use the conventional crystallographic system names such as triclinic, monoclinic, orthorhombic, tetragonal, trigonal, hexagonal, and cubic.


* **[Hermann-Mauguin Symbol (hm_symbol)](../properties/pointgroups/hm_symbol.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol.md)  
  Hermann-Mauguin point-group symbol used as the key and display symbol for a point-group record.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Is Centrosymmetric (is_centrosymmetric)](../properties/pointgroups/is_centrosymmetric.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/is_centrosymmetric`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/is_centrosymmetric.md)  
  Boolean flag indicating whether the point group contains inversion symmetry.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Laue Class (laue_class)](../properties/pointgroups/laue_class.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class.md)  
  The Laue class associated with the space group or point group.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The Laue class groups point groups that become equivalent when inversion symmetry is included.


* **[N Conjugacy Classes (n_conjugacy_classes)](../properties/pointgroups/n_conjugacy_classes.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_conjugacy_classes`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_conjugacy_classes.md)  
  Number of conjugacy classes in the crystallographic point group.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Order](../properties/pointgroups/order.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/order`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/order.md)  
  Order of the point group, i.e. the number of operations in the finite point group.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Schoenflies Symbol (schoenflies)](../properties/pointgroups/schoenflies.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies.md)  
  The Schoenflies symbol for the space-group type.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The ASCII form follows the CIF convention for `_space_group.name_Schoenflies`, using a period to separate the Schoenflies point-group symbol from the superscript index.


* **[Symmetry operations (symops)](../properties/pointgroups/symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/symops`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/symops.md)  
  Full list of symmetry-operation descriptors for a point group.
Each list member is a `op` object as defined by `/properties/symmetry/op`.
For point-group operations, generated data currently uses `matrix` and `type`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a list of dictionaries.
    - Each dictionary MUST follow the schema inherited from `/properties/symmetry/op`.


* **[Schoenflies symbol markups (schoenflies_markup)](../properties/pointgroups/schoenflies_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies_markup`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies_markup.md)  
  Display-oriented renderings of the Schoenflies symbol in `schoenflies`.
The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.


**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/entrytypes/pointgroups",
    "$schema": "https://schemas.optimade.org/meta/v1.2/optimade/entrytype_definition.json",
    "type": "object",
    "title": "Anyterial point group symmetry fields",
    "x-optimade-definition": {
        "kind": "entrytype",
        "format": "1.3",
        "version": "0.1.0",
        "name": "pointgroups",
        "label": "pointgroups_entrytype_anyterial"
    },
    "properties": {
        "id": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/id",
            "x-optimade-requirements": {
                "support": "must",
                "sortable": true,
                "query-support": "all mandatory",
                "response-level": "always"
            },
            "title": "ID",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "label": "id_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "id"
            },
            "type": [
                "string"
            ],
            "description": "A unique string referencing a specific entry in the database.\n\n**Requirements/Conventions:**\n\n- Taken together, the ID and entry type MUST uniquely identify the entry.\n- Reasonably short IDs are encouraged and SHOULD NOT be longer than 255 characters.\n- IDs MAY change over time.",
            "examples": [
                "db/1234567",
                "cod/2000000",
                "cod/2000000@1234567",
                "nomad/L1234567890",
                "42"
            ],
            "x-optimade-unit": "inapplicable"
        },
        "type": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/type",
            "x-optimade-requirements": {
                "support": "must",
                "sortable": true,
                "query-support": "all mandatory",
                "response-level": "always"
            },
            "title": "type",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "label": "type_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "type"
            },
            "type": [
                "string"
            ],
            "description": "The name of the type of an entry.\n\n**Requirements/Conventions:**\n\n- MUST be an existing entry type.\n- The entry of type <type> and ID <id> MUST be returned in response to a request for /<type>/<id> under the versioned or unversioned base URL serving the API.",
            "examples": [
                "structures"
            ],
            "x-optimade-unit": "inapplicable"
        },
        "immutable_id": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "all mandatory",
                "response-level": "may"
            },
            "title": "immutable ID",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "label": "immutable_id_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "immutable_id"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The entry's immutable ID (e.g., a UUID).\n\n**Requirements/Conventions:**\n\n- This is important for databases having preferred IDs that point to \"the latest version\" of a record, but still offer access to older variants.\n- This ID maps to the version-specific record, in case it changes in the future.",
            "examples": [
                "8bd3e750-b477-41a0-9b11-3a799f21b44f",
                "fjeiwoj,54;@=%<>#32"
            ],
            "x-optimade-unit": "inapplicable"
        },
        "last_modified": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/last_modified",
            "x-optimade-requirements": {
                "support": "should",
                "sortable": false,
                "query-support": "all mandatory",
                "response-level": "must"
            },
            "title": "last modified",
            "x-optimade-type": "timestamp",
            "x-optimade-definition": {
                "label": "last_modified_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "last_modified"
            },
            "type": [
                "string",
                "null"
            ],
            "format": "date-time",
            "description": "Date and time representing when the entry was last modified.",
            "examples": [
                "2007-04-05T14:30:20Z"
            ],
            "x-optimade-unit": "inapplicable"
        },
        "character_table_complex": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_complex",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Character Table Complex",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "character_table_complex",
                "label": "character_table_complex_pointgroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Complex irreducible character table of the crystallographic point group. Rows correspond to complex irreducible representations and columns follow the order of `conjugacy_classes`.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "dictionary",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One row of a point-group character table.",
                "properties": {
                    "label": {
                        "x-optimade-type": "string",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Irreducible-representation label.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "label_markup": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/string_markups",
                        "title": "String markups",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "string_markups",
                            "label": "string_markups_core"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Strings with alternate markup and/or encoding for display rendering.\n\nThe object is intended for display-oriented variants only, a sibling property should be used for canonical plain string value.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **html**: OPTIONAL; String.\n      HTML rendering of the sibling string, using inline HTML elements where needed for typographic structure such as subscripts, superscripts, overlines, fractions, and line breaks.\n\n    - **latex**: OPTIONAL; String.\n      LaTeX rendering of the sibling string, suitable for use with a LaTeX or MathJax-like renderer.\n\n    - **unicode**: OPTIONAL; String.\n      Unicode rendering of the sibling string, using Unicode code points for display features where practical.",
                        "properties": {
                            "html": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "HTML rendering of the sibling string."
                            },
                            "latex": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "LaTeX rendering of the sibling string."
                            },
                            "unicode": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Unicode rendering of the sibling string."
                            }
                        },
                        "examples": [
                            {
                                "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                                "latex": "\\mathit{P}\\,2_{1}/c",
                                "unicode": "P2\u2081/c"
                            }
                        ]
                    },
                    "dimension": {
                        "x-optimade-type": "integer",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Dimension of the irreducible representation.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "characters": {
                        "x-optimade-type": "list",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Characters for the conjugacy classes in table order.",
                        "items": {
                            "x-optimade-type": "dictionary",
                            "type": [
                                "object",
                                "null"
                            ],
                            "description": "One complex character value represented as exact real and imaginary parts.",
                            "x-optimade-unit": "inapplicable",
                            "properties": {
                                "re": {
                                    "x-optimade-type": "string",
                                    "type": [
                                        "string",
                                        "null"
                                    ],
                                    "description": "Exact real part represented as a string.",
                                    "x-optimade-unit": "inapplicable"
                                },
                                "im": {
                                    "x-optimade-type": "string",
                                    "type": [
                                        "string",
                                        "null"
                                    ],
                                    "description": "Exact imaginary part represented as a string.",
                                    "x-optimade-unit": "inapplicable"
                                }
                            }
                        },
                        "x-optimade-unit": "inapplicable"
                    },
                    "frobenius_schur_indicator": {
                        "x-optimade-type": "integer",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Frobenius-Schur indicator of the representation.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "basis_linear": {
                        "x-optimade-type": "list",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Linear basis functions transforming as this representation.",
                        "items": {
                            "x-optimade-type": "string",
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "One basis function.",
                            "x-optimade-unit": "inapplicable"
                        },
                        "x-optimade-unit": "inapplicable"
                    },
                    "basis_rotation": {
                        "x-optimade-type": "list",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Rotational basis functions transforming as this representation.",
                        "items": {
                            "x-optimade-type": "string",
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "One rotational basis function.",
                            "x-optimade-unit": "inapplicable"
                        },
                        "x-optimade-unit": "inapplicable"
                    },
                    "basis_quadratic": {
                        "x-optimade-type": "list",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Quadratic basis functions transforming as this representation.",
                        "items": {
                            "x-optimade-type": "string",
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "One quadratic basis function.",
                            "x-optimade-unit": "inapplicable"
                        },
                        "x-optimade-unit": "inapplicable"
                    }
                },
                "x-optimade-unit": "inapplicable"
            },
            "examples": [
                [
                    {
                        "label": "A",
                        "dimension": 1,
                        "characters": [
                            1
                        ],
                        "frobenius_schur_indicator": 1,
                        "label_markup": {
                            "latex": "A",
                            "unicode": "A"
                        }
                    }
                ],
                [
                    {
                        "label": "Ag",
                        "dimension": 1,
                        "characters": [
                            1,
                            1
                        ],
                        "frobenius_schur_indicator": 1,
                        "label_markup": {
                            "latex": "A_{g}",
                            "unicode": "Ag"
                        }
                    },
                    {
                        "label": "Au",
                        "dimension": 1,
                        "characters": [
                            1,
                            -1
                        ],
                        "frobenius_schur_indicator": 1,
                        "label_markup": {
                            "latex": "A_{u}",
                            "unicode": "Au"
                        }
                    }
                ]
            ]
        },
        "character_table_real": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_real",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Character Table Real",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "character_table_real",
                "label": "character_table_real_pointgroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Real irreducible character table of the crystallographic point group. Rows correspond to real irreducible representations and columns follow the order of `conjugacy_classes`.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "dictionary",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One row of a point-group character table.",
                "properties": {
                    "label": {
                        "x-optimade-type": "string",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Irreducible-representation label.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "label_markup": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/string_markups",
                        "title": "String markups",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "string_markups",
                            "label": "string_markups_core"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Strings with alternate markup and/or encoding for display rendering.\n\nThe object is intended for display-oriented variants only, a sibling property should be used for canonical plain string value.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **html**: OPTIONAL; String.\n      HTML rendering of the sibling string, using inline HTML elements where needed for typographic structure such as subscripts, superscripts, overlines, fractions, and line breaks.\n\n    - **latex**: OPTIONAL; String.\n      LaTeX rendering of the sibling string, suitable for use with a LaTeX or MathJax-like renderer.\n\n    - **unicode**: OPTIONAL; String.\n      Unicode rendering of the sibling string, using Unicode code points for display features where practical.",
                        "properties": {
                            "html": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "HTML rendering of the sibling string."
                            },
                            "latex": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "LaTeX rendering of the sibling string."
                            },
                            "unicode": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Unicode rendering of the sibling string."
                            }
                        },
                        "examples": [
                            {
                                "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                                "latex": "\\mathit{P}\\,2_{1}/c",
                                "unicode": "P2\u2081/c"
                            }
                        ]
                    },
                    "dimension": {
                        "x-optimade-type": "integer",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Dimension of the irreducible representation.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "characters": {
                        "x-optimade-type": "list",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Characters for the conjugacy classes in table order.",
                        "items": {
                            "x-optimade-type": "integer",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "One real character value represented as an exact integer.",
                            "x-optimade-unit": "inapplicable"
                        },
                        "x-optimade-unit": "inapplicable"
                    },
                    "frobenius_schur_indicator": {
                        "x-optimade-type": "integer",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Frobenius-Schur indicator of the representation.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "basis_linear": {
                        "x-optimade-type": "list",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Linear basis functions transforming as this representation.",
                        "items": {
                            "x-optimade-type": "string",
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "One basis function.",
                            "x-optimade-unit": "inapplicable"
                        },
                        "x-optimade-unit": "inapplicable"
                    },
                    "basis_rotation": {
                        "x-optimade-type": "list",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Rotational basis functions transforming as this representation.",
                        "items": {
                            "x-optimade-type": "string",
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "One rotational basis function.",
                            "x-optimade-unit": "inapplicable"
                        },
                        "x-optimade-unit": "inapplicable"
                    },
                    "basis_quadratic": {
                        "x-optimade-type": "list",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Quadratic basis functions transforming as this representation.",
                        "items": {
                            "x-optimade-type": "string",
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "One quadratic basis function.",
                            "x-optimade-unit": "inapplicable"
                        },
                        "x-optimade-unit": "inapplicable"
                    }
                },
                "x-optimade-unit": "inapplicable"
            },
            "examples": [
                [
                    {
                        "label": "A",
                        "dimension": 1,
                        "characters": [
                            1
                        ],
                        "basis_linear": [
                            "x",
                            "y"
                        ],
                        "basis_rotation": [
                            "Rx",
                            "Ry"
                        ],
                        "basis_quadratic": [
                            "x^2",
                            "y^2"
                        ],
                        "label_markup": {
                            "latex": "A",
                            "unicode": "A"
                        }
                    }
                ],
                [
                    {
                        "label": "Ag",
                        "dimension": 1,
                        "characters": [
                            1,
                            1
                        ],
                        "basis_rotation": [
                            "Rx",
                            "Ry"
                        ],
                        "basis_quadratic": [
                            "x^2",
                            "y^2"
                        ],
                        "label_markup": {
                            "latex": "A_{g}",
                            "unicode": "Ag"
                        }
                    },
                    {
                        "label": "Au",
                        "dimension": 1,
                        "characters": [
                            1,
                            -1
                        ],
                        "basis_linear": [
                            "x",
                            "y"
                        ],
                        "label_markup": {
                            "latex": "A_{u}",
                            "unicode": "Au"
                        }
                    }
                ]
            ]
        },
        "conjugacy_classes": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/conjugacy_classes",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Conjugacy Classes",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "conjugacy_classes",
                "label": "conjugacy_classes_pointgroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Conjugacy classes of a crystallographic point group. Each class lists its member operation indices, a representative operation, a conventional class label, and operation-type metadata used by the character tables.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "dictionary",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One conjugacy class of a crystallographic point group.",
                "properties": {
                    "label": {
                        "x-optimade-type": "dictionary",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Rendered class label.",
                        "properties": {
                            "ascii": {
                                "x-optimade-type": "string",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Plain-text rendering intended for logs, command-line output, or compact display.",
                                "x-optimade-unit": "inapplicable"
                            },
                            "unicode": {
                                "x-optimade-type": "string",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Unicode rendering of the same label.",
                                "x-optimade-unit": "inapplicable"
                            },
                            "latex": {
                                "x-optimade-type": "string",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "LaTeX rendering of the same label.",
                                "x-optimade-unit": "inapplicable"
                            }
                        },
                        "x-optimade-unit": "inapplicable"
                    },
                    "size": {
                        "x-optimade-type": "integer",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Number of point-group operations in the class.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "members": {
                        "x-optimade-type": "list",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Indices of operations belonging to this class.",
                        "items": {
                            "x-optimade-type": "integer",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "Operation index.",
                            "x-optimade-unit": "inapplicable"
                        },
                        "x-optimade-unit": "inapplicable"
                    },
                    "representative": {
                        "x-optimade-type": "integer",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Index of a representative operation for the class.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "op_type": {
                        "x-optimade-type": "integer",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Numeric operation type code of the representative.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "op_axis": {
                        "x-optimade-type": "list",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Three integer components.",
                        "items": {
                            "x-optimade-type": "integer",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "One integer component.",
                            "x-optimade-unit": "inapplicable"
                        },
                        "x-optimade-unit": "inapplicable"
                    }
                },
                "x-optimade-unit": "inapplicable"
            },
            "examples": [
                [
                    {
                        "label": {
                            "ascii": "E",
                            "unicode": "E",
                            "latex": "E"
                        },
                        "size": 1,
                        "members": [
                            0
                        ],
                        "representative": 0,
                        "op_type": 1,
                        "op_axis": [
                            0,
                            0
                        ]
                    }
                ],
                [
                    {
                        "label": {
                            "ascii": "E",
                            "unicode": "E",
                            "latex": "E"
                        },
                        "size": 1,
                        "members": [
                            0
                        ],
                        "representative": 0,
                        "op_type": 1,
                        "op_axis": [
                            0,
                            0
                        ]
                    },
                    {
                        "label": {
                            "ascii": "i",
                            "unicode": "i",
                            "latex": "i"
                        },
                        "size": 1,
                        "members": [
                            1
                        ],
                        "representative": 1,
                        "op_type": -1,
                        "op_axis": [
                            0,
                            0
                        ]
                    }
                ]
            ]
        },
        "crystal_system": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Crystal System",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.crystal_system.html"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "crystal_system",
                "label": "crystal_system_pointgroups"
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
        "hm_symbol": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hermann-Mauguin Symbol",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_symbol",
                "label": "hm_symbol_pointgroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Hermann-Mauguin point-group symbol used as the key and display symbol for a point-group record.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "1",
                "-1"
            ]
        },
        "is_centrosymmetric": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/is_centrosymmetric",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Is Centrosymmetric",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "boolean",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "is_centrosymmetric",
                "label": "is_centrosymmetric_pointgroups"
            },
            "type": [
                "boolean",
                "null"
            ],
            "description": "Boolean flag indicating whether the point group contains inversion symmetry.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                false,
                true
            ]
        },
        "laue_class": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Laue Class",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.Laue_class.html"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "laue_class",
                "label": "laue_class_pointgroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The Laue class associated with the space group or point group.\n\nThe Laue class groups point groups that become equivalent when inversion symmetry is included.",
            "x-optimade-unit": "inapplicable",
            "enum": [
                "-1",
                "2/m",
                "mmm",
                "4/m",
                "4/mmm",
                "-3",
                "-3m",
                "6/m",
                "6/mmm",
                "m-3",
                "m-3m"
            ],
            "examples": [
                "-1",
                "2/m"
            ]
        },
        "n_conjugacy_classes": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_conjugacy_classes",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "N Conjugacy Classes",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_conjugacy_classes",
                "label": "n_conjugacy_classes_pointgroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of conjugacy classes in the crystallographic point group.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                1,
                2
            ]
        },
        "order": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/order",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Order",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "order",
                "label": "order_pointgroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Order of the point group, i.e. the number of operations in the finite point group.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                1,
                2
            ]
        },
        "schoenflies": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Schoenflies Symbol",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.name_Schoenflies.html"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "schoenflies",
                "label": "schoenflies_pointgroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The Schoenflies symbol for the space-group type.\n\nThe ASCII form follows the CIF convention for `_space_group.name_Schoenflies`, using a period to separate the Schoenflies point-group symbol from the superscript index.",
            "x-optimade-unit": "inapplicable",
            "enum": [
                "C1.1",
                "Ci.1",
                "C2.1",
                "C2.2",
                "C2.3",
                "Cs.1",
                "Cs.2",
                "Cs.3",
                "Cs.4",
                "C2h.1",
                "C2h.2",
                "C2h.3",
                "C2h.4",
                "C2h.5",
                "C2h.6",
                "D2.1",
                "D2.2",
                "D2.3",
                "D2.4",
                "D2.5",
                "D2.6",
                "D2.7",
                "D2.8",
                "D2.9",
                "C2v.1",
                "C2v.2",
                "C2v.3",
                "C2v.4",
                "C2v.5",
                "C2v.6",
                "C2v.7",
                "C2v.8",
                "C2v.9",
                "C2v.10",
                "C2v.11",
                "C2v.12",
                "C2v.13",
                "C2v.14",
                "C2v.15",
                "C2v.16",
                "C2v.17",
                "C2v.18",
                "C2v.19",
                "C2v.20",
                "C2v.21",
                "C2v.22",
                "D2h.1",
                "D2h.2",
                "D2h.3",
                "D2h.4",
                "D2h.5",
                "D2h.6",
                "D2h.7",
                "D2h.8",
                "D2h.9",
                "D2h.10",
                "D2h.11",
                "D2h.12",
                "D2h.13",
                "D2h.14",
                "D2h.15",
                "D2h.16",
                "D2h.17",
                "D2h.18",
                "D2h.19",
                "D2h.20",
                "D2h.21",
                "D2h.22",
                "D2h.23",
                "D2h.24",
                "D2h.25",
                "D2h.26",
                "D2h.27",
                "D2h.28",
                "C4.1",
                "C4.2",
                "C4.3",
                "C4.4",
                "C4.5",
                "C4.6",
                "S4.1",
                "S4.2",
                "C4h.1",
                "C4h.2",
                "C4h.3",
                "C4h.4",
                "C4h.5",
                "C4h.6",
                "D4.1",
                "D4.2",
                "D4.3",
                "D4.4",
                "D4.5",
                "D4.6",
                "D4.7",
                "D4.8",
                "D4.9",
                "D4.10",
                "C4v.1",
                "C4v.2",
                "C4v.3",
                "C4v.4",
                "C4v.5",
                "C4v.6",
                "C4v.7",
                "C4v.8",
                "C4v.9",
                "C4v.10",
                "C4v.11",
                "C4v.12",
                "D2d.1",
                "D2d.2",
                "D2d.3",
                "D2d.4",
                "D2d.5",
                "D2d.6",
                "D2d.7",
                "D2d.8",
                "D2d.9",
                "D2d.10",
                "D2d.11",
                "D2d.12",
                "D4h.1",
                "D4h.2",
                "D4h.3",
                "D4h.4",
                "D4h.5",
                "D4h.6",
                "D4h.7",
                "D4h.8",
                "D4h.9",
                "D4h.10",
                "D4h.11",
                "D4h.12",
                "D4h.13",
                "D4h.14",
                "D4h.15",
                "D4h.16",
                "D4h.17",
                "D4h.18",
                "D4h.19",
                "D4h.20",
                "C3.1",
                "C3.2",
                "C3.3",
                "C3.4",
                "C3i.1",
                "C3i.2",
                "D3.1",
                "D3.2",
                "D3.3",
                "D3.4",
                "D3.5",
                "D3.6",
                "D3.7",
                "C3v.1",
                "C3v.2",
                "C3v.3",
                "C3v.4",
                "C3v.5",
                "C3v.6",
                "D3d.1",
                "D3d.2",
                "D3d.3",
                "D3d.4",
                "D3d.5",
                "D3d.6",
                "C6.1",
                "C6.2",
                "C6.3",
                "C6.4",
                "C6.5",
                "C6.6",
                "C3h.1",
                "C6h.1",
                "C6h.2",
                "D6.1",
                "D6.2",
                "D6.3",
                "D6.4",
                "D6.5",
                "D6.6",
                "C6v.1",
                "C6v.2",
                "C6v.3",
                "C6v.4",
                "D3h.1",
                "D3h.2",
                "D3h.3",
                "D3h.4",
                "D6h.1",
                "D6h.2",
                "D6h.3",
                "D6h.4",
                "T.1",
                "T.2",
                "T.3",
                "T.4",
                "T.5",
                "Th.1",
                "Th.2",
                "Th.3",
                "Th.4",
                "Th.5",
                "Th.6",
                "Th.7",
                "O.1",
                "O.2",
                "O.3",
                "O.4",
                "O.5",
                "O.6",
                "O.7",
                "O.8",
                "Td.1",
                "Td.2",
                "Td.3",
                "Td.4",
                "Td.5",
                "Td.6",
                "Oh.1",
                "Oh.2",
                "Oh.3",
                "Oh.4",
                "Oh.5",
                "Oh.6",
                "Oh.7",
                "Oh.8",
                "Oh.9",
                "Oh.10"
            ],
            "examples": [
                "C1.1",
                "C2.3"
            ]
        },
        "symops": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/symops",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symmetry operations",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "symops",
                "label": "symops_pointgroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Full list of symmetry-operation descriptors for a point group.\nEach list member is a `op` object as defined by `/properties/symmetry/op`.\nFor point-group operations, generated data currently uses `matrix` and `type`.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST follow the schema inherited from `/properties/symmetry/op`.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op",
                "title": "Operation",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "op",
                    "label": "op_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "Information related to a crystallographic operation acting within one coordinate setting.\n\nRepresents an affine_transformation that is a crystallographic operation within one setting.\nThe affine map itself is stored in the embedded `affine_transformation` field.\nThe remaining fields classify the operation crystallographically, for example by rotation type, axis, sense, and screw or glide component.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **affine\\_transformation**: REQUIRED; Dictionary.\n      Exact affine map for the operation.\n      It MUST follow `/defs/v0.1/properties/symmetry/affine_transformation`.\n\n    - **rot\\_type**: OPTIONAL; String.\n      Crystallographic operation-type label for the linear part, such as `1`, `-1`, `2`, `m`, `-3`, `4`, `-4`, `6`, or `-6`.\n\n    - **axis**: OPTIONAL; List of 3 Integers.\n      Operation axis or invariant direction using the integer-vector convention returned by the generator.\n\n    - **sense**: OPTIONAL; Integer.\n      Rotation sense/sign convention returned by the generator; `0` is used when no handed rotation sense is applicable.\n\n    - **screw\\_glide**: OPTIONAL; List of 3 Fractions (String).\n      Screw-axis or glide-plane component associated with a space-group affine operation.\n\n    - **origin\\_shift**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift associated with the screw/glide decomposition of a space-group affine operation.\n\n    - **is\\_proper**: OPTIONAL; Boolean.\n      States whether the linear operation is proper, i.e., whether its determinant is +1.",
                "properties": {
                    "affine_transformation": {
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
                    },
                    "rot_type": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Symbolic crystallographic operation-type label for the linear part."
                    },
                    "axis": {
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
                        "description": "Integer-vector axis or invariant-direction descriptor for the operation.",
                        "items": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer"
                            ],
                            "description": "One integer component of the axis vector."
                        }
                    },
                    "sense": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Rotation sense/sign convention returned by the generator."
                    },
                    "screw_glide": {
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
                        "description": "Screw-axis or glide-plane component represented exactly as a list of fraction strings.",
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
                    "origin_shift": {
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
                        "description": "Origin-shift descriptor represented exactly as a list of fraction strings.",
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
                    "is_proper": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether the linear operation is proper."
                    }
                },
                "examples": [
                    {
                        "affine_transformation": {
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
                        },
                        "rot_type": "2",
                        "sense": 0,
                        "axis": [
                            0,
                            0,
                            1
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            },
            "examples": [
                [
                    {
                        "affine_transformation": {
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
                        "rot_type": "1",
                        "sense": 0,
                        "axis": [
                            0,
                            0,
                            0
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            ]
        },
        "schoenflies_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Schoenflies symbol markups",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "schoenflies_markup",
                "label": "schoenflies_markup_pointgroups"
            },
            "description": "Display-oriented renderings of the Schoenflies symbol in `schoenflies`.\nThe plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.",
            "x-optimade-type": "dictionary",
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "properties": {
                "html": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "HTML rendering of the sibling string."
                },
                "latex": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "LaTeX rendering of the sibling string."
                },
                "unicode": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Unicode rendering of the sibling string."
                }
            },
            "examples": [
                {
                    "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                    "latex": "\\mathit{P}\\,2_{1}/c",
                    "unicode": "P2\u2081/c"
                }
            ]
        }
    }
}
```