# Basis transformation origin shift (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec.md)**  
**Definition name:** `pvec`

**Property name:** Basis transformation origin shift  
**Description:** Translation or origin-shift part of a crystallographic basis or setting transformation.
The vector is represented in fractional coordinates using exact fraction strings.  
**Type:** list  

**Requirements/Conventions**:

- It MUST be a list of three exact fractional-coordinate components.
- Each component MUST be represented as a fraction string.
- The parent transform definition specifies the source and target setting convention for the transformation.

**Examples:**

- `["0", "0", "0"]`
- `["1/4", "1/4", "0"]`

**Formats:** [[JSON](pvec.json)] [[MD](pvec.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Basis transformation origin shift",
    "$comment": "Reusable Anyterial definition for the translation/origin-shift part of a crystallographic basis or setting transformation.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "pvec",
        "label": "pvec_symmetry"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Translation or origin-shift part of a crystallographic basis or setting transformation.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- The parent transform definition specifies the source and target setting convention for the transformation.",
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
            "1/4",
            "1/4",
            "0"
        ]
    ]
}
```