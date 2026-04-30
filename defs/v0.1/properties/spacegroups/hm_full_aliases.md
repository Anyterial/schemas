# Hermann-Mauguin Full Aliases (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases.md)**  
**Definition name:** `hm_full_aliases`

**Property name:** Hermann-Mauguin Full Aliases  
**Description:** Alternate ASCII forms of `hm_full` that are accepted for the same generated setting. The preferred symbol is stored in `hm_full`.  
**Type:** list  



**Examples:**

- `["F 23"]`
- `["I 23"]`

**Formats:** [[JSON](hm_full_aliases.json)] [[MD](hm_full_aliases.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Hermann-Mauguin Full Aliases",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hm_full_aliases",
        "label": "hm_full_aliases_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "Alternate ASCII forms of `hm_full` that are accepted for the same generated setting. The preferred symbol is stored in `hm_full`.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        [
            "F 23"
        ],
        [
            "I 23"
        ]
    ],
    "items": {
        "x-optimade-type": "string",
        "type": [
            "string",
            "null"
        ],
        "description": "One alternate symbol string.",
        "x-optimade-unit": "inapplicable"
    }
}
```