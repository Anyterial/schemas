# To Hall (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall.md)**  
**Definition name:** `to_hall`

**Property name:** To Hall  
**Description:** Reference Hall-entry key to which a setting transform maps the current Hall setting.  
**Type:** string  



**Examples:**

- `"p_1"`
- `"-p_1"`

**Formats:** [[JSON](to_hall.json)] [[MD](to_hall.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "To Hall",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "to_hall",
        "label": "to_hall_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "Reference Hall-entry key to which a setting transform maps the current Hall setting.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "p_1",
        "-p_1"
    ]
}
```