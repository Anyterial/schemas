# Hermann-Mauguin Short Aliases (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases.md)**  
**Definition name:** `hm_short_aliases`

**Property name:** Hermann-Mauguin Short Aliases  
**Description:** Alternate ASCII forms of `hm_short` that are accepted for the same generated setting. The preferred symbol is stored in `hm_short`.  
**Type:** list  



**Examples:**

- `["C c c a", "C c c b"]`
- `["A b a a", "A c a a"]`

**Formats:** [[JSON](hm_short_aliases.json)] [[MD](hm_short_aliases.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Hermann-Mauguin Short Aliases",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hm_short_aliases",
        "label": "hm_short_aliases_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "Alternate ASCII forms of `hm_short` that are accepted for the same generated setting. The preferred symbol is stored in `hm_short`.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        [
            "C c c a",
            "C c c b"
        ],
        [
            "A b a a",
            "A c a a"
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