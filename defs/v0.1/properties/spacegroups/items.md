# Items (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/items`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/items.md)**  
**Definition name:** `items`

**Property name:** Items  
**Description:** Generic ordered data-list container used by several generated JSON-LD datasets.
The item schema is defined by the containing dataset or parent property.
This property is intentionally generic because `items` is used for symbol rows, transform rows, and normalizer rows in different contexts.  
**Type:** list  



**Examples:**

- `[{"setting_it_nc": "1", "hall": "P 1", "it_number": 1}]`

**Formats:** [[JSON](items.json)] [[MD](items.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/items",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Items",
    "$comment": "Generic Anyterial ordered data-list container used by several generated datasets.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "items",
        "label": "items_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Generic ordered data-list container used by several generated JSON-LD datasets.\nThe item schema is defined by the containing dataset or parent property.\nThis property is intentionally generic because `items` is used for symbol rows, transform rows, and normalizer rows in different contexts.",
    "items": {
        "x-optimade-type": "dictionary",
        "x-optimade-unit": "inapplicable",
        "type": [
            "object",
            "null"
        ],
        "description": "One parent-defined item object.",
        "properties": {}
    },
    "examples": [
        [
            {
                "setting_it_nc": "1",
                "hall": "P 1",
                "it_number": 1
            }
        ]
    ]
}
```