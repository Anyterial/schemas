# To Hall Symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall_symbol`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall_symbol.md)**  
**Definition name:** `to_hall_symbol`

**Property name:** To Hall Symbol  
**Description:** Display Hall symbol corresponding to `to_hall`.  
**Type:** string  



**Examples:**

- `"p 1"`
- `"-p 1"`

**Formats:** [[JSON](to_hall_symbol.json)] [[MD](to_hall_symbol.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall_symbol",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "To Hall Symbol",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "to_hall_symbol",
        "label": "to_hall_symbol_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "Display Hall symbol corresponding to `to_hall`.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "p 1",
        "-p 1"
    ]
}
```