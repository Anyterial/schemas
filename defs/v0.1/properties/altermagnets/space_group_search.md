# Normalized screening space group (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/space_group_search`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/space_group_search.md)**  
**Definition name:** `space_group_search`

**Property name:** Normalized screening space group  
**Description:** The screening space-group display string normalized by stripping surrounding whitespace and lowercasing.  
**Type:** string  
**Implementation requirements:**  
- **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.  

- **Query:** MUST be a queryable property.  
- **Response:**  

It is intended for case-insensitive `CONTAINS` matching with the same normalization used by the legacy search path; the display form is served by the `space_group` property.
A null value means no space group is recorded for this material.

**Examples:**

- `"p6_3/mmc"`
- `"p4_2/mnm"`

**Formats:** [[JSON](space_group_search.json)] [[MD](space_group_search.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/space_group_search",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Normalized screening space group",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "space_group_search",
        "label": "space_group_search_altermagnets"
    },
    "x-optimade-unit": "inapplicable",
    "x-optimade-requirements": {
        "support": "may",
        "query-support": "partial",
        "query-support-operators": [
            "CONTAINS"
        ],
        "response-level": "should not"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The screening space-group display string normalized by stripping surrounding whitespace and lowercasing.\n\nIt is intended for case-insensitive `CONTAINS` matching with the same normalization used by the legacy search path; the display form is served by the `space_group` property.\nA null value means no space group is recorded for this material.",
    "examples": [
        "p6_3/mmc",
        "p4_2/mnm"
    ]
}
```