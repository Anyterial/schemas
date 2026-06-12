# Hermann-Mauguin entry aliases (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry_aliases.md)**  
**Definition name:** `hm_entry_aliases`

**Property name:** Hermann-Mauguin entry aliases  
**Description:** Alternative Hermann-Mauguin entry labels from International Tables for Crystallography Volume B table A1.4.2.7 that identify the same generated Hall-symbol row as `hm_entry`.  
**Type:** list  

This field is used when table A1.4.2.7 distinguishes conventional settings by H-M entry label even though the generated static space-group row is shared.
The primary label is stored in `hm_entry`; this list stores the remaining labels that should resolve to the same row in H-M-entry lookup indices.

**Requirements/Conventions**:

- Each item MUST follow the same formatting conventions as `hm_entry`.
- The list MUST NOT repeat the value stored in `hm_entry`.
- If there are no alternate H-M entry labels for the row, this field SHOULD be omitted rather than stored as an empty list.

**Examples:**

- `["C c c b:1"]`
- `["A c a a:1"]`

**Formats:** [[JSON](hm_entry_aliases.json)] [[MD](hm_entry_aliases.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry_aliases",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Hermann-Mauguin entry aliases",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hm_entry_aliases",
        "label": "hm_entry_aliases_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "Alternative Hermann-Mauguin entry labels from International Tables for Crystallography Volume B table A1.4.2.7 that identify the same generated Hall-symbol row as `hm_entry`.\n\nThis field is used when table A1.4.2.7 distinguishes conventional settings by H-M entry label even though the generated static space-group row is shared.\nThe primary label is stored in `hm_entry`; this list stores the remaining labels that should resolve to the same row in H-M-entry lookup indices.\n\n**Requirements/Conventions**:\n\n- Each item MUST follow the same formatting conventions as `hm_entry`.\n- The list MUST NOT repeat the value stored in `hm_entry`.\n- If there are no alternate H-M entry labels for the row, this field SHOULD be omitted rather than stored as an empty list.",
    "x-optimade-unit": "inapplicable",
    "items": {
        "x-optimade-type": "string",
        "x-optimade-unit": "inapplicable",
        "type": [
            "string"
        ],
        "description": "One alternate Hermann-Mauguin entry label."
    },
    "examples": [
        [
            "C c c b:1"
        ],
        [
            "A c a a:1"
        ]
    ]
}
```