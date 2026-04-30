# Hermann-Mauguin Symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol.md)**  
**Definition name:** `hm_symbol`

**Property name:** Hermann-Mauguin Symbol  
**Description:** Hermann-Mauguin point-group symbol used as the key and display symbol for a point-group record.  
**Type:** string  



**Examples:**

- `"1"`
- `"-1"`

**Formats:** [[JSON](hm_symbol.json)] [[MD](hm_symbol.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Hermann-Mauguin Symbol",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hm_symbol",
        "label": "hm_symbol_pointgroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "Hermann-Mauguin point-group symbol used as the key and display symbol for a point-group record.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "1",
        "-1"
    ]
}
```