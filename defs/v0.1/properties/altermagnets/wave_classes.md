# Wave classes (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/wave_classes`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/wave_classes.md)**  
**Definition name:** `wave_classes`

**Property name:** Wave classes  
**Description:** The full ordered, deduplicated spin-momentum wave-class list collected from the material's linked symmetry variants.  
**Type:** list  
**Implementation requirements:**  
- **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.  

- **Query:** MUST be a queryable property.  
- **Response:**  

The values use the same vocabulary as the scalar `wave_class` property, which serves the first entry of this list.
A null value means no wave classes are recorded for this material.

**Examples:**

- `["d"]`
- `["d", "g"]`

**Formats:** [[JSON](wave_classes.json)] [[MD](wave_classes.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/wave_classes",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Wave classes",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "wave_classes",
        "label": "wave_classes_altermagnets"
    },
    "x-optimade-unit": "inapplicable",
    "x-optimade-requirements": {
        "support": "may",
        "query-support": "partial",
        "query-support-operators": [
            "HAS",
            "HAS ANY",
            "HAS ALL"
        ],
        "response-level": "may"
    },
    "type": [
        "array",
        "null"
    ],
    "items": {
        "x-optimade-type": "string",
        "x-optimade-unit": "inapplicable",
        "type": [
            "string"
        ],
        "description": "One spin-momentum wave-class label."
    },
    "description": "The full ordered, deduplicated spin-momentum wave-class list collected from the material's linked symmetry variants.\n\nThe values use the same vocabulary as the scalar `wave_class` property, which serves the first entry of this list.\nA null value means no wave classes are recorded for this material.",
    "examples": [
        [
            "d"
        ],
        [
            "d",
            "g"
        ]
    ]
}
```