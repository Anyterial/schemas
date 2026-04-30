# Entries (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/entries`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/entries.md)**  
**Definition name:** `entries`

**Property name:** Entries  
**Description:** Generic top-level keyed data container used by several generated JSON-LD datasets.
The meaning of keys and values is defined by the containing dataset metadata and by sibling fields.
This property is intentionally generic because `entries` is used for compact maps with different value types in different files.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary.
- Keys and values MUST be interpreted according to the containing dataset.

**Examples:**

- `{"1": "p_1"}`

**Formats:** [[JSON](entries.json)] [[MD](entries.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/entries",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Entries",
    "$comment": "Generic Anyterial top-level keyed data container used by several generated datasets.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "entries",
        "label": "entries_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Generic top-level keyed data container used by several generated JSON-LD datasets.\nThe meaning of keys and values is defined by the containing dataset metadata and by sibling fields.\nThis property is intentionally generic because `entries` is used for compact maps with different value types in different files.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary.\n- Keys and values MUST be interpreted according to the containing dataset.",
    "properties": {},
    "examples": [
        {
            "1": "p_1"
        }
    ]
}
```