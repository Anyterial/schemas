# Hall entry (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry.md)**  
**Definition name:** `hall_entry`

**Property name:** Hall entry  
**Description:** Normalized Hall-table entry key used internally by the generated datasets.  
**Type:** string  

The value is derived from the Hall symbol by using lowercase letters and underscores in place of spaces. It is stable for lookup within these data files, while the display Hall symbol is provided separately by `hall` and its formatted variants.

**Requirements/Conventions**:

- This field identifies a concrete Hall setting, not only an IT space-group type.
- The same value is normally used as the key of the containing `spacegroups` map.

**Examples:**

- `"p_1"`
- `"-p_1"`

**Formats:** [[JSON](hall_entry.json)] [[MD](hall_entry.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
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
}
```