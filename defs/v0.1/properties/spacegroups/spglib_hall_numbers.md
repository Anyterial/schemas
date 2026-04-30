# Spglib Hall Numbers (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers.md)**  
**Definition name:** `spglib_hall_numbers`

**Property name:** Spglib Hall Numbers  
**Description:** spglib Hall numbers corresponding to the generated setting.  
**Type:** list  



**Examples:**

- `[1]`
- `[2]`

**Formats:** [[JSON](spglib_hall_numbers.json)] [[MD](spglib_hall_numbers.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Spglib Hall Numbers",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "spglib_hall_numbers",
        "label": "spglib_hall_numbers_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "spglib Hall numbers corresponding to the generated setting.",
    "x-optimade-unit": "inapplicable",
    "items": {
        "x-optimade-type": "integer",
        "x-optimade-unit": "inapplicable",
        "type": [
            "integer"
        ]
    },
    "examples": [
        [
            1
        ],
        [
            2
        ]
    ]
}
```