# Wyckoff Sets (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets.md)**  
**Definition name:** `wyckoff_sets`

**Property name:** Wyckoff Sets  
**Description:** Sets of Wyckoff letters related by normalizer operations. Each inner list groups Wyckoff positions that can be interchanged by the relevant normalizer action.  
**Type:** list  



**Examples:**

- `[["a"]]`
- `[["i"], ["h"], ["g"]]`

**Formats:** [[JSON](wyckoff_sets.json)] [[MD](wyckoff_sets.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Wyckoff Sets",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "wyckoff_sets",
        "label": "wyckoff_sets_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "Sets of Wyckoff letters related by normalizer operations. Each inner list groups Wyckoff positions that can be interchanged by the relevant normalizer action.",
    "x-optimade-unit": "inapplicable",
    "items": {
        "x-optimade-type": "list",
        "type": [
            "array",
            "null"
        ],
        "description": "One Wyckoff-set combination.",
        "items": {
            "x-optimade-type": "string",
            "type": [
                "string",
                "null"
            ],
            "description": "Wyckoff letter.",
            "x-optimade-unit": "inapplicable"
        },
        "x-optimade-unit": "inapplicable"
    },
    "examples": [
        [
            [
                "a"
            ]
        ],
        [
            [
                "i"
            ],
            [
                "h"
            ],
            [
                "g"
            ]
        ]
    ]
}
```