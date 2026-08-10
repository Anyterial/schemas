# ICSD identifiers (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/icsd_ids`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/icsd_ids.md)**  
**Definition name:** `icsd_ids`

**Property name:** ICSD identifiers  
**Description:** The ordered, deduplicated Inorganic Crystal Structure Database identifiers collected from the material's linked symmetry variants.  
**Type:** list  
**Implementation requirements:**  
- **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.  

- **Query:** MUST be a queryable property.  
- **Response:**  

The identifiers are served as strings exactly as recorded in the symmetry source tables.
A null value means no ICSD identifiers are recorded for this material.

**Examples:**

- `["93775"]`
- `["109371", "609865"]`

**Formats:** [[JSON](icsd_ids.json)] [[MD](icsd_ids.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/icsd_ids",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "ICSD identifiers",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "icsd_ids",
        "label": "icsd_ids_altermagnets"
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
        "description": "One Inorganic Crystal Structure Database identifier."
    },
    "description": "The ordered, deduplicated Inorganic Crystal Structure Database identifiers collected from the material's linked symmetry variants.\n\nThe identifiers are served as strings exactly as recorded in the symmetry source tables.\nA null value means no ICSD identifiers are recorded for this material.",
    "examples": [
        [
            "93775"
        ],
        [
            "109371",
            "609865"
        ]
    ]
}
```