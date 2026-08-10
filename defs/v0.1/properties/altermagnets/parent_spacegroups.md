# Parent space groups (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/parent_spacegroups`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/parent_spacegroups.md)**  
**Definition name:** `parent_spacegroups`

**Property name:** Parent space groups  
**Description:** The full ordered, deduplicated parent-space-group list collected from the material's linked symmetry variants.  
**Type:** list  
**Implementation requirements:**  
- **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.  

- **Query:** MUST be a queryable property.  
- **Response:**  

The values are plain-text display strings combining the Hermann-Mauguin symbol and the space-group number, e.g. `Pnma (62)`.
A null value means no parent space groups are recorded for this material.

**Examples:**

- `["Pnma (62)"]`
- `["R-3c (167)", "R3c (161)"]`

**Formats:** [[JSON](parent_spacegroups.json)] [[MD](parent_spacegroups.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/parent_spacegroups",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Parent space groups",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "parent_spacegroups",
        "label": "parent_spacegroups_altermagnets"
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
        "description": "One parent-space-group display string."
    },
    "description": "The full ordered, deduplicated parent-space-group list collected from the material's linked symmetry variants.\n\nThe values are plain-text display strings combining the Hermann-Mauguin symbol and the space-group number, e.g. `Pnma (62)`.\nA null value means no parent space groups are recorded for this material.",
    "examples": [
        [
            "Pnma (62)"
        ],
        [
            "R-3c (167)",
            "R3c (161)"
        ]
    ]
}
```