# Spglib Hall numbers (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers.md)**  
**Definition name:** `spglib_hall_numbers`

**Property name:** Spglib Hall numbers  
**Description:** The spglib Hall numbers corresponding to this Hall setting.  
**Type:** list  

Spglib enumerates 530 settings with Hall numbers 1 to 530.
Distinct spglib Hall numbers can share one Hall symbol, so this is a sorted list of every spglib Hall number whose Hall symbol matches this entry.

**Examples:**

- `[1]`
- `[2]`

**Formats:** [[JSON](spglib_hall_numbers.json)] [[MD](spglib_hall_numbers.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Spglib Hall numbers",
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
    "description": "The spglib Hall numbers corresponding to this Hall setting.\n\nSpglib enumerates 530 settings with Hall numbers 1 to 530.\nDistinct spglib Hall numbers can share one Hall symbol, so this is a sorted list of every spglib Hall number whose Hall symbol matches this entry.",
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