# Screening source classification (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/classification`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/classification.md)**  
**Definition name:** `classification`

**Property name:** Screening source classification  
**Description:** The source classification assigned to the material by the altermagnet material store from the kinds of its linked symmetry-variant sources.  
**Type:** string  
**Implementation requirements:**  
- **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.  

- **Query:** MUST be queryable using the OPTIMADE filter language equality and inequality operators. Other filter language features do not need to be available.  
- **Response:**  

The value `collinear` means only variants from the collinear source table are linked, `noncollinear-derived` means only variants derived from the noncollinear source table are linked, `mixed` means variants of both kinds are linked, and `unclassified` means no symmetry variants are linked.
A null value means no classification is available or recorded for this material.

**Examples:**

- `"collinear"`
- `"mixed"`

**Formats:** [[JSON](classification.json)] [[MD](classification.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/classification",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Screening source classification",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "classification",
        "label": "classification_altermagnets"
    },
    "x-optimade-unit": "inapplicable",
    "x-optimade-requirements": {
        "support": "may",
        "query-support": "equality only",
        "response-level": "may"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The source classification assigned to the material by the altermagnet material store from the kinds of its linked symmetry-variant sources.\n\nThe value `collinear` means only variants from the collinear source table are linked, `noncollinear-derived` means only variants derived from the noncollinear source table are linked, `mixed` means variants of both kinds are linked, and `unclassified` means no symmetry variants are linked.\nA null value means no classification is available or recorded for this material.",
    "enum": [
        "collinear",
        "noncollinear-derived",
        "mixed",
        "unclassified"
    ],
    "examples": [
        "collinear",
        "mixed"
    ]
}
```