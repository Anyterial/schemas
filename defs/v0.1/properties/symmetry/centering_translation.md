# Centering translation (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/centering_translation`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/centering_translation.md)**  
**Definition name:** `centering_translation`

**Property name:** Centering translation  
**Description:** One centering translation of a conventional crystallographic cell.
The translation is represented in fractional coordinates using exact fraction strings.  
**Type:** list  

**Requirements/Conventions**:

- It MUST be a list of three exact fractional-coordinate components.
- The zero translation is included in centering-translation lists and is normally listed first.

**Examples:**

- `["0", "0", "0"]`
- `["1/2", "1/2", "0"]`

**Formats:** [[JSON](centering_translation.json)] [[MD](centering_translation.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/centering_translation",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Centering translation",
    "$comment": "Reusable Anyterial definition for one conventional-cell centering translation.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "centering_translation",
        "label": "centering_translation_symmetry"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "One centering translation of a conventional crystallographic cell.\nThe translation is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- The zero translation is included in centering-translation lists and is normally listed first.",
    "x-optimade-dimensions": {
        "names": [
            "dim_lattice"
        ],
        "sizes": [
            3
        ]
    },
    "items": {
        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
        "title": "fraction",
        "x-optimade-type": "string",
        "x-optimade-definition": {
            "label": "fraction_core",
            "kind": "property",
            "version": "0.1.0",
            "format": "1.3",
            "name": "fraction"
        },
        "type": [
            "string",
            "null"
        ],
        "description": "A fraction represented as a string.",
        "examples": [
            "2/3",
            "5/42",
            "10",
            "0"
        ],
        "x-optimade-unit": "inapplicable"
    },
    "examples": [
        [
            "0",
            "0",
            "0"
        ],
        [
            "1/2",
            "1/2",
            "0"
        ]
    ]
}
```