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
        "properties": {}
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