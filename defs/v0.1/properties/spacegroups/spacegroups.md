# Space groups (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroups.md)**  
**Definition name:** `spacegroups`

**Property name:** Space groups  
**Description:** Ordered table of crystallographic space-group setting records.
Each item describes one concrete Hall/International Tables setting of a space group, including symbols, classifications, symmetry operations, asymmetric-unit information, Wyckoff positions, and related auxiliary data.
The companion `index_hall_entry_to_spacegroups` property maps normalized Hall entries to indices in this list.  
**Type:** list  

**Requirements/Conventions**:

- Items MUST be ordered in the same setting order as `symbols.json.gz`, with additional cctbx-only Hall settings kept in their IT-number block.
- A single IT number can occur in several items.
- The `setting_it_nc` property gives the corresponding International Tables `n:c` setting code when applicable.

**Examples:**

- `[{"setting_it_nc": "5:b1", "it_number": 5, "hall_entry": "c_2y"}]`

**Formats:** [[JSON](spacegroups.json)] [[MD](spacegroups.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroups",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Space groups",
    "$comment": "Anyterial top-level ordered space-group setting table.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "spacegroups",
        "label": "spacegroups_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Ordered table of crystallographic space-group setting records.\nEach item describes one concrete Hall/International Tables setting of a space group, including symbols, classifications, symmetry operations, asymmetric-unit information, Wyckoff positions, and related auxiliary data.\nThe companion `index_hall_entry_to_spacegroups` property maps normalized Hall entries to indices in this list.\n\n**Requirements/Conventions**:\n\n- Items MUST be ordered in the same setting order as `symbols.json.gz`, with additional cctbx-only Hall settings kept in their IT-number block.\n- A single IT number can occur in several items.\n- The `setting_it_nc` property gives the corresponding International Tables `n:c` setting code when applicable.",
    "items": {
        "x-optimade-type": "dictionary",
        "x-optimade-unit": "inapplicable",
        "type": [
            "object",
            "null"
        ],
        "description": "One space-group setting record.",
        "properties": {}
    },
    "examples": [
        [
            {
                "setting_it_nc": "5:b1",
                "it_number": 5,
                "hall_entry": "c_2y"
            }
        ]
    ]
}
```