# Criterion target (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/target`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/target.md)**  
**Definition name:** `target`

**Property name:** Criterion target  
**Description:** Exact target vector or scalar of a generated linear criterion.  
**Type:** list  

This field appears in `criteria` items of basis-transform records, for example in backward-lift criteria, where it gives the value that the linear form evaluated on the constrained coordinates must equal.
The components are exact rational values serialized as fraction strings.

**Examples:**

- `["0", "0", "0"]`
- `["1/2", "0", "0"]`

**Formats:** [[JSON](target.json)] [[MD](target.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/transformations/target",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Criterion target",
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
    "description": "Exact target vector or scalar of a generated linear criterion.\n\nThis field appears in `criteria` items of basis-transform records, for example in backward-lift criteria, where it gives the value that the linear form evaluated on the constrained coordinates must equal.\nThe components are exact rational values serialized as fraction strings.",
    "items": {
        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
        "title": "Fraction",
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