# Hall Symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall.md)**  
**Definition name:** `hall`

**Property name:** Hall Symbol  
**Description:** The Hall symbol for a crystallographic space-group setting.  
**Type:** string  

Hall symbols encode the generators and origin choice of a space-group setting in a form intended to identify the setting unambiguously. In the Anyterial symmetry data, this property is the plain ASCII Hall symbol corresponding to the Hall-keyed record.

**Examples:**

- `"P 1"`
- `"C 2y"`

**Formats:** [[JSON](hall.json)] [[MD](hall.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Hall Symbol",
    "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hall"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hall",
        "label": "hall_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The Hall symbol for a crystallographic space-group setting.\n\nHall symbols encode the generators and origin choice of a space-group setting in a form intended to identify the setting unambiguously. In the Anyterial symmetry data, this property is the plain ASCII Hall symbol corresponding to the Hall-keyed record.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "P 1",
        "C 2y"
    ]
}
```