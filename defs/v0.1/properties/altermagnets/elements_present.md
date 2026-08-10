# Screening elements (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/elements_present`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/elements_present.md)**  
**Definition name:** `elements_present`

**Property name:** Screening elements  
**Description:** The alphabetized chemical element symbols extracted from the formula recorded by the altermagnet screening workflow.  
**Type:** list  
**Implementation requirements:**  
- **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.  

- **Query:** MUST be a queryable property.  
- **Response:**  

This property is a fallback for structureless entries whose standard OPTIMADE `elements` property is null.
A null value means no elements are recorded for this material.

**Examples:**

- `["Cr", "Sb"]`
- `["Mn", "Te"]`

**Formats:** [[JSON](elements_present.json)] [[MD](elements_present.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/elements_present",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Screening elements",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "elements_present",
        "label": "elements_present_altermagnets"
    },
    "x-optimade-unit": "inapplicable",
    "x-optimade-requirements": {
        "support": "may",
        "query-support": "partial",
        "query-support-operators": [
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
        "description": "One chemical element symbol."
    },
    "description": "The alphabetized chemical element symbols extracted from the formula recorded by the altermagnet screening workflow.\n\nThis property is a fallback for structureless entries whose standard OPTIMADE `elements` property is null.\nA null value means no elements are recorded for this material.",
    "examples": [
        [
            "Cr",
            "Sb"
        ],
        [
            "Mn",
            "Te"
        ]
    ]
}
```