# Hall-entry to spacegroups index (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroups.md)**  
**Definition name:** `index_hall_entry_to_spacegroups`

**Property name:** Hall-entry to spacegroups index  
**Description:** Index from normalized Hall entries to row positions in the top-level `spacegroups` table.
It allows consumers to look up a space-group setting by Hall entry while keeping `spacegroups` as a compact ordered list.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary whose keys are normalized Hall entries using the same computer notation as the `hall_entry` field, with underscores replacing spaces.
- Each value MUST be a zero-based integer index into the top-level `spacegroups` list.
- For every key-value pair, `spacegroups[value].hall_entry` MUST equal the key.

**Examples:**

- `{"p_1": 0, "-p_1": 1}`

**Formats:** [[JSON](index_hall_entry_to_spacegroups.json)] [[MD](index_hall_entry_to_spacegroups.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroups",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Hall-entry to spacegroups index",
    "$comment": "Anyterial top-level index from Hall entries to rows in the spacegroups table.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "index_hall_entry_to_spacegroups",
        "label": "index_hall_entry_to_spacegroups_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Index from normalized Hall entries to row positions in the top-level `spacegroups` table.\nIt allows consumers to look up a space-group setting by Hall entry while keeping `spacegroups` as a compact ordered list.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary whose keys are normalized Hall entries using the same computer notation as the `hall_entry` field, with underscores replacing spaces.\n- Each value MUST be a zero-based integer index into the top-level `spacegroups` list.\n- For every key-value pair, `spacegroups[value].hall_entry` MUST equal the key.",
    "properties": {},
    "examples": [
        {
            "p_1": 0,
            "-p_1": 1
        }
    ]
}
```