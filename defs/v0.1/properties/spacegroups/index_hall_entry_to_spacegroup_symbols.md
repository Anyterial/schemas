# Index Hall entry to space-group symbols (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroup_symbols`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroup_symbols.md)**  
**Definition name:** `index_hall_entry_to_spacegroup_symbols`

**Property name:** Index Hall entry to space-group symbols  
**Description:** Index from normalized Hall entries to row positions in the top-level `spacegroup_symbols` table.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary whose keys are normalized Hall entries using the same computer notation as the `hall_entry` field, with underscores replacing spaces.
- Values MUST be non-negative integer row indices into `data.spacegroup_symbols`.

**Examples:**

- `{"p_1": 0}`

**Formats:** [[JSON](index_hall_entry_to_spacegroup_symbols.json)] [[MD](index_hall_entry_to_spacegroup_symbols.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroup_symbols",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Index Hall entry to space-group symbols",
    "$comment": "Anyterial top-level index from Hall entries to rows in the space-group symbols table.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "index_hall_entry_to_spacegroup_symbols",
        "label": "index_hall_entry_to_spacegroup_symbols_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Index from normalized Hall entries to row positions in the top-level `spacegroup_symbols` table.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary whose keys are normalized Hall entries using the same computer notation as the `hall_entry` field, with underscores replacing spaces.\n- Values MUST be non-negative integer row indices into `data.spacegroup_symbols`.",
    "properties": {},
    "examples": [
        {
            "p_1": 0
        }
    ]
}
```