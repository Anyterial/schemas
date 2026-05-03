# Space-group symbols (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroup_symbols`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroup_symbols.md)**  
**Definition name:** `spacegroup_symbols`

**Property name:** Space-group symbols  
**Description:** Ordered table of conventional space-group symbol rows.
Each row describes one Hall setting where the International Tables symbol data is available, including the IT coordinate-system code, Hall symbol, IT number, and Hermann-Mauguin symbols.  
**Type:** list  

**Requirements/Conventions**:

- It MUST be a list of dictionaries.
- Each dictionary SHOULD contain the setting identifier `setting_it_nc`, the Hall symbol `hall`, the International Tables number `it_number`, and the setting-specific Hermann-Mauguin symbols `hm_short`, `hm_full`, and `hm_extended` when available.
- The order SHOULD follow the conventional ITA/Hall setting order used by the generated `symmetry_basics` space-group table.

**Examples:**

- `[{"setting_it_nc": "1", "hall": "P 1", "it_number": 1, "hm_short": "P 1", "hm_full": "P 1", "hm_extended": "P 1"}]`

**Formats:** [[JSON](spacegroup_symbols.json)] [[MD](spacegroup_symbols.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroup_symbols",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Space-group symbols",
    "$comment": "Ordered Anyterial table of conventional space-group symbols.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "spacegroup_symbols",
        "label": "spacegroup_symbols_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Ordered table of conventional space-group symbol rows.\nEach row describes one Hall setting where the International Tables symbol data is available, including the IT coordinate-system code, Hall symbol, IT number, and Hermann-Mauguin symbols.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary SHOULD contain the setting identifier `setting_it_nc`, the Hall symbol `hall`, the International Tables number `it_number`, and the setting-specific Hermann-Mauguin symbols `hm_short`, `hm_full`, and `hm_extended` when available.\n- The order SHOULD follow the conventional ITA/Hall setting order used by the generated `symmetry_basics` space-group table.",
    "items": {
        "x-optimade-type": "dictionary",
        "x-optimade-unit": "inapplicable",
        "type": [
            "object",
            "null"
        ],
        "description": "One space-group symbol row.",
        "properties": {
            "setting_it_nc": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc",
                "title": "International Tables setting code n:c",
                "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                "x-optimade-type": "string",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "setting_it_nc",
                    "label": "setting_it_nc_spacegroups"
                },
                "type": [
                    "string",
                    "null"
                ],
                "description": "International Tables setting identifier in `n:c` notation.\n\nThe part before the colon is the International Tables space-group number. The part after the colon is the coordinate-system or origin-choice qualifier used to distinguish settings that share the same IT number.\n\n**Requirements/Conventions**:\n\n- Triclinic, hexagonal, and many unique settings use only the IT number, for example `1`.\n- Monoclinic settings use qualifiers such as `b1`, `-b1`, `c2`, or `a3`.\n- Orthorhombic settings use qualifiers such as `abc`, `cab`, `1abc`, or `2bca` when needed.\n- Tetragonal and cubic origin choices use qualifiers such as `1` and `2`; trigonal axis choices use qualifiers such as `h` and `r`.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    "1",
                    "2"
                ]
            },
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
            "hall": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall",
                "title": "Hall Symbol",
                "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
                "x-optimade-type": "string",
                "x-compatibility": [
                    "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hall"
                ],
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "hall",
                    "label": "hall_spacegroups"
                },
                "type": [
                    "string",
                    "null"
                ],
                "description": "The Hall symbol for a crystallographic space-group setting.\n\nHall symbols encode the generators and origin choice of a space-group setting in a form intended to identify the setting unambiguously. In the Anyterial symmetry data, this property is the plain ASCII Hall symbol corresponding to the Hall-keyed record.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    "P 1",
                    "C 2y"
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
            "hm_short": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short",
                "title": "Short Hermann-Mauguin Symbol",
                "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
                "x-optimade-type": "string",
                "x-compatibility": [
                    "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hermann_mauguin"
                ],
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "hm_short",
                    "label": "hm_short_spacegroups"
                },
                "type": [
                    "string",
                    "null"
                ],
                "description": "The setting-specific short Hermann-Mauguin symbol for the space-group setting.\n\nThis field gives the concise Hermann-Mauguin notation used for the concrete Hall setting represented by the containing record. It is compatible with OPTIMADE's `space_group_symbol_hermann_mauguin` when used as the conventional short Hermann-Mauguin symbol.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    "P 1",
                    "C 2"
                ]
            },
            "hm_full": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full",
                "title": "Full Hermann-Mauguin Symbol",
                "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
                "x-optimade-type": "string",
                "x-compatibility": [
                    "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.name_H-M_full.html"
                ],
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "hm_full",
                    "label": "hm_full_spacegroups"
                },
                "type": [
                    "string",
                    "null"
                ],
                "description": "The setting-specific full Hermann-Mauguin symbol for the space-group setting.\n\nThe full symbol expands the short Hermann-Mauguin notation to include the symmetry entries for all relevant crystallographic directions in the setting represented by the containing Hall record.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    "P 1",
                    "C 1 2 1"
                ]
            },
            "hm_extended": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended",
                "title": "Extended Hermann-Mauguin Symbol",
                "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
                "x-optimade-type": "string",
                "x-compatibility": [
                    "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hermann_mauguin_extended"
                ],
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "hm_extended",
                    "label": "hm_extended_spacegroups"
                },
                "type": [
                    "string",
                    "null"
                ],
                "description": "The setting-specific extended Hermann-Mauguin symbol for the space-group setting.\n\nExtended Hermann-Mauguin symbols give additional symmetry-element information compared with the short symbol. Multi-line values preserve line breaks and spacing used to align the extended symbol components.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    "P 1",
                    "C 1 2 1\n  21"
                ]
            },
            "hm_extended_old": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_old",
                "title": "Hermann-Mauguin Extended Old",
                "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                "x-optimade-type": "string",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "hm_extended_old",
                    "label": "hm_extended_old_spacegroups"
                },
                "type": [
                    "string",
                    "null"
                ],
                "description": "The older extended Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    "A b m 2\n c c 21",
                    "C 2 m b\n 21 a a"
                ]
            },
            "hm_short_old": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old",
                "title": "Hermann-Mauguin Short Old",
                "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                "x-optimade-type": "string",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "hm_short_old",
                    "label": "hm_short_old_spacegroups"
                },
                "type": [
                    "string",
                    "null"
                ],
                "description": "The older short Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    "A b m 2",
                    "C 2 m b"
                ]
            },
            "hm_full_old": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_old",
                "title": "Hermann-Mauguin Full Old",
                "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                "x-optimade-type": "string",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "hm_full_old",
                    "label": "hm_full_old_spacegroups"
                },
                "type": [
                    "string",
                    "null"
                ],
                "description": "The older full Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
                "x-optimade-unit": "inapplicable",
                "examples": [
                    "A b m 2",
                    "C 2 m b"
                ]
            }
        }
    },
    "examples": [
        [
            {
                "setting_it_nc": "1",
                "hall": "P 1",
                "it_number": 1,
                "hm_short": "P 1",
                "hm_full": "P 1",
                "hm_extended": "P 1"
            }
        ]
    ]
}
```