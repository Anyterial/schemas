# Normalized search text (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/search_text`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/search_text.md)**  
**Definition name:** `search_text`

**Property name:** Normalized search text  
**Description:** The normalized lowercase free-text aggregate maintained by the altermagnet material store, concatenating the formula, MAGNDATA identifiers, space groups, elements, magnetic phases, wave classes, and the source classification.  
**Type:** string  
**Implementation requirements:**  
- **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.  

- **Query:** MUST be a queryable property.  
- **Response:**  

It is served verbatim so a client can reproduce the legacy free-text search with `CONTAINS`.
A null value means no search text is recorded for this material.

**Examples:**

- `"crsb 0.528 p6_3/mmc cr sb pnma (62) am d collinear"`

**Formats:** [[JSON](search_text.json)] [[MD](search_text.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/search_text",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Normalized search text",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "search_text",
        "label": "search_text_altermagnets"
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
    "description": "The normalized lowercase free-text aggregate maintained by the altermagnet material store, concatenating the formula, MAGNDATA identifiers, space groups, elements, magnetic phases, wave classes, and the source classification.\n\nIt is served verbatim so a client can reproduce the legacy free-text search with `CONTAINS`.\nA null value means no search text is recorded for this material.",
    "examples": [
        "crsb 0.528 p6_3/mmc cr sb pnma (62) am d collinear"
    ]
}
```