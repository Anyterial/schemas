# Target (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/target`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/target.md)**  
**Definition name:** `target`

**Property name:** Target  
**Description:** Target vector or target value in a generated linear criterion.
In current generated criteria it is usually represented as exact rational components serialized as strings.
The semantic meaning of `target` is parent-specific and should not be reused as a broad standalone concept.  
**Type:** list  



**Examples:**

- `["0", "0", "0"]`
- `["1/2", "0", "0"]`

**Formats:** [[JSON](target.json)] [[MD](target.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/target",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Target",
    "$comment": "Anyterial local target vector property used in generated linear criteria.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "target",
        "label": "target_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Target vector or target value in a generated linear criterion.\nIn current generated criteria it is usually represented as exact rational components serialized as strings.\nThe semantic meaning of `target` is parent-specific and should not be reused as a broad standalone concept.",
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
            "0",
            "0"
        ]
    ]
}
```