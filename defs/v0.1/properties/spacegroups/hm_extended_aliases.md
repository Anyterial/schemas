# Extended Hermann-Mauguin symbol aliases (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases.md)**  
**Definition name:** `hm_extended_aliases`

**Property name:** Extended Hermann-Mauguin symbol aliases  
**Description:** Alternate ASCII forms of `hm_extended` that are accepted for the same generated setting.  
**Type:** list  

The preferred symbol is stored in `hm_extended`.

**Examples:**

- `["A b m 2\n c c 21"]`
- `["B m a 2\n c c 21"]`

**Formats:** [[JSON](hm_extended_aliases.json)] [[MD](hm_extended_aliases.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Extended Hermann-Mauguin symbol aliases",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hm_extended_aliases",
        "label": "hm_extended_aliases_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "Alternate ASCII forms of `hm_extended` that are accepted for the same generated setting.\n\nThe preferred symbol is stored in `hm_extended`.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        [
            "A b m 2\n c c 21"
        ],
        [
            "B m a 2\n c c 21"
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