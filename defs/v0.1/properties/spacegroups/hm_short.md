# Short Hermann-Mauguin Symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short.md)**  
**Definition name:** `hm_short`

**Property name:** Short Hermann-Mauguin Symbol  
**Description:** The setting-specific short Hermann-Mauguin symbol for the space-group setting.  
**Type:** string  

This field gives the concise Hermann-Mauguin notation used for the concrete Hall setting represented by the containing record. It is compatible with OPTIMADE's `space_group_symbol_hermann_mauguin` when used as the conventional short Hermann-Mauguin symbol.

**Examples:**

- `"P 1"`
- `"C 2"`

**Formats:** [[JSON](hm_short.json)] [[MD](hm_short.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Short Hermann-Mauguin Symbol",
    "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hermann_mauguin"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hm_short",
        "label": "hm_short_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The setting-specific short Hermann-Mauguin symbol for the space-group setting.\n\nThis field gives the concise Hermann-Mauguin notation used for the concrete Hall setting represented by the containing record. It is compatible with OPTIMADE's `space_group_symbol_hermann_mauguin` when used as the conventional short Hermann-Mauguin symbol.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "P 1",
        "C 2"
    ]
}
```