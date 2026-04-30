# Extended Hermann-Mauguin Symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended.md)**  
**Definition name:** `hm_extended`

**Property name:** Extended Hermann-Mauguin Symbol  
**Description:** The setting-specific extended Hermann-Mauguin symbol for the space-group setting.  
**Type:** string  

Extended Hermann-Mauguin symbols give additional symmetry-element information compared with the short symbol. Multi-line values preserve line breaks and spacing used to align the extended symbol components.

**Examples:**

- `"P 1"`
- `"C 1 2 1\n  21"`

**Formats:** [[JSON](hm_extended.json)] [[MD](hm_extended.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Extended Hermann-Mauguin Symbol",
    "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hermann_mauguin_extended"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hm_extended",
        "label": "hm_extended_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The setting-specific extended Hermann-Mauguin symbol for the space-group setting.\n\nExtended Hermann-Mauguin symbols give additional symmetry-element information compared with the short symbol. Multi-line values preserve line breaks and spacing used to align the extended symbol components.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "P 1",
        "C 1 2 1\n  21"
    ]
}
```