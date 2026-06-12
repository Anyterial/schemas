# Target (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/target`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/target.md)**  
**Definition name:** `target`

**Property name:** Target  
**Description:** Target vector or target value in a generated linear criterion.  
**Type:** list  

In current generated criteria it is usually represented as exact rational components serialized as strings.
The semantic meaning of `target` is parent-specific and should not be reused as a broad standalone concept.

**Examples:**

- `["0", "0", "0"]`
- `["1/2", "0", "0"]`

**Formats:** [[JSON](target.json)] [[MD](target.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/transformations/target",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Target",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "target",
        "label": "target_transformations"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Target vector or target value in a generated linear criterion.\n\nIn current generated criteria it is usually represented as exact rational components serialized as strings.\nThe semantic meaning of `target` is parent-specific and should not be reused as a broad standalone concept.",
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
        "description": "A numerical representation formed as the quotient of two numbers represented as a string.",
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
            "0",
            "0"
        ]
    ]
}
```