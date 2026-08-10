# Screening formula (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/formula`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/formula.md)**  
**Definition name:** `formula`

**Property name:** Screening formula  
**Description:** The chemical formula recorded by the altermagnet screening workflow, served verbatim as a display string.  
**Type:** string  
**Implementation requirements:**  
- **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.  

- **Query:** MUST be queryable using the OPTIMADE filter language equality and inequality operators. Other filter language features do not need to be available.  
- **Response:**  

This property is a fallback for structureless entries whose standard OPTIMADE chemical formula properties are null.
A null value means no formula is recorded for this material.

**Examples:**

- `"CrSb"`
- `"RuO2"`

**Formats:** [[JSON](formula.json)] [[MD](formula.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/formula",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Screening formula",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "formula",
        "label": "formula_altermagnets"
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
    "description": "The chemical formula recorded by the altermagnet screening workflow, served verbatim as a display string.\n\nThis property is a fallback for structureless entries whose standard OPTIMADE chemical formula properties are null.\nA null value means no formula is recorded for this material.",
    "examples": [
        "CrSb",
        "RuO2"
    ]
}
```