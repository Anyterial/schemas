# Structure Seminvariants (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/structure_seminvariants`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/structure_seminvariants.md)**  
**Definition name:** `structure_seminvariants`

**Property name:** Structure Seminvariants  
**Description:** Structure seminvariant vectors and moduli for the space-group setting. These characterize phase restrictions and FFT grid constraints associated with the symmetry.  
**Type:** list  



**Examples:**

- `[{"vector": [1, 0], "modulus": 0}, {"vector": [0, 1], "modulus": 0}, {"vector": [0, 0], "modulus": 0}]`
- `[{"vector": [1, 0], "modulus": 2}, {"vector": [0, 1], "modulus": 2}, {"vector": [0, 0], "modulus": 2}]`

**Formats:** [[JSON](structure_seminvariants.json)] [[MD](structure_seminvariants.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/structure_seminvariants",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Structure Seminvariants",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "structure_seminvariants",
        "label": "structure_seminvariants_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "Structure seminvariant vectors and moduli for the space-group setting. These characterize phase restrictions and FFT grid constraints associated with the symmetry.",
    "x-optimade-unit": "inapplicable",
    "items": {
        "x-optimade-type": "dictionary",
        "type": [
            "object",
            "null"
        ],
        "description": "One structure-seminvariant condition vector.",
        "properties": {
            "vector": {
                "x-optimade-type": "list",
                "type": [
                    "array",
                    "null"
                ],
                "description": "Integer vector defining the seminvariant congruence.",
                "items": {
                    "x-optimade-type": "integer",
                    "type": [
                        "integer",
                        "null"
                    ],
                    "description": "One vector component.",
                    "x-optimade-unit": "inapplicable"
                },
                "x-optimade-unit": "inapplicable"
            },
            "modulus": {
                "x-optimade-type": "integer",
                "type": [
                    "integer",
                    "null"
                ],
                "description": "Modulus for the seminvariant congruence.",
                "x-optimade-unit": "inapplicable"
            }
        },
        "x-optimade-unit": "inapplicable"
    },
    "examples": [
        [
            {
                "vector": [
                    1,
                    0
                ],
                "modulus": 0
            },
            {
                "vector": [
                    0,
                    1
                ],
                "modulus": 0
            },
            {
                "vector": [
                    0,
                    0
                ],
                "modulus": 0
            }
        ],
        [
            {
                "vector": [
                    1,
                    0
                ],
                "modulus": 2
            },
            {
                "vector": [
                    0,
                    1
                ],
                "modulus": 2
            },
            {
                "vector": [
                    0,
                    0
                ],
                "modulus": 2
            }
        ]
    ]
}
```