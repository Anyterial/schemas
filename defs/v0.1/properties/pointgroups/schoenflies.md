# Schoenflies symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies.md)**  
**Definition name:** `schoenflies`

**Property name:** Schoenflies symbol  
**Description:** The Schoenflies symbol for the crystallographic point group.  
**Type:** string  

The value is one of the 32 crystallographic point-group symbols in Schoenflies notation, written in ASCII without subscript formatting.
The symbol `S6` is used for the point group also known as `C3i`.

**Examples:**

- `"C1"`
- `"C2v"`
- `"Oh"`

**Formats:** [[JSON](schoenflies.json)] [[MD](schoenflies.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Schoenflies symbol",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "schoenflies",
        "label": "schoenflies_pointgroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The Schoenflies symbol for the crystallographic point group.\n\nThe value is one of the 32 crystallographic point-group symbols in Schoenflies notation, written in ASCII without subscript formatting.\nThe symbol `S6` is used for the point group also known as `C3i`.",
    "x-optimade-unit": "inapplicable",
    "enum": [
        "C1",
        "Ci",
        "C2",
        "Cs",
        "C2h",
        "D2",
        "C2v",
        "D2h",
        "C4",
        "S4",
        "C4h",
        "D4",
        "C4v",
        "D2d",
        "D4h",
        "C3",
        "S6",
        "D3",
        "C3v",
        "D3d",
        "C6",
        "C3h",
        "C6h",
        "D6",
        "C6v",
        "D3h",
        "D6h",
        "T",
        "Th",
        "O",
        "Td",
        "Oh"
    ],
    "examples": [
        "C1",
        "C2v",
        "Oh"
    ]
}
```