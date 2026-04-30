# Wyckoff splitting (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_splitting`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_splitting.md)**  
**Definition name:** `wyckoff_splitting`

**Property name:** Wyckoff splitting  
**Description:** Wyckoff-position splitting data associated with a subgroup or same-space-group transform.
The map is keyed by parent Wyckoff letter.
Each value is an ordered list of subgroup Wyckoff-position assignments or coordinate expressions as emitted by the generator.  
**Type:** dictionary  

**Requirements/Conventions**:

- Dynamic keys MUST be parent Wyckoff letters.
- Values MUST be lists.
- Each listed item is currently a compact generator record whose exact shape is defined by the parent transform table.

**Examples:**

- `{"c": [["e", "x", "y", "z"], ["e", "-x", "y", "-z"]]}`

**Formats:** [[JSON](wyckoff_splitting.json)] [[MD](wyckoff_splitting.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_splitting",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Wyckoff splitting",
    "$comment": "Anyterial property definition for Wyckoff-position splitting data attached to subgroup transforms.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "wyckoff_splitting",
        "label": "wyckoff_splitting_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Wyckoff-position splitting data associated with a subgroup or same-space-group transform.\nThe map is keyed by parent Wyckoff letter.\nEach value is an ordered list of subgroup Wyckoff-position assignments or coordinate expressions as emitted by the generator.\n\n**Requirements/Conventions**:\n\n- Dynamic keys MUST be parent Wyckoff letters.\n- Values MUST be lists.\n- Each listed item is currently a compact generator record whose exact shape is defined by the parent transform table.",
    "properties": {},
    "examples": [
        {
            "c": [
                [
                    "e",
                    "x",
                    "y",
                    "z"
                ],
                [
                    "e",
                    "-x",
                    "y",
                    "-z"
                ]
            ]
        }
    ]
}
```