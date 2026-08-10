# Magnetic phases (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/magnetic_phases`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/magnetic_phases.md)**  
**Definition name:** `magnetic_phases`

**Property name:** Magnetic phases  
**Description:** The full ordered, deduplicated magnetic-phase list collected from the material's linked symmetry variants.  
**Type:** list  
**Implementation requirements:**  
- **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.  

- **Query:** MUST be a queryable property.  
- **Response:**  

The values are the short phase labels used by the symmetry source tables, currently `AM` for an altermagnetic phase and `FiM` for a fully compensated ferrimagnetic phase; the scalar `magnetic_phase` property serves the long form of the first entry.
A null value means no magnetic phases are recorded for this material.

**Examples:**

- `["AM"]`
- `["AM", "FiM"]`

**Formats:** [[JSON](magnetic_phases.json)] [[MD](magnetic_phases.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/magnetic_phases",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Magnetic phases",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "magnetic_phases",
        "label": "magnetic_phases_altermagnets"
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
        "description": "One short magnetic-phase label."
    },
    "description": "The full ordered, deduplicated magnetic-phase list collected from the material's linked symmetry variants.\n\nThe values are the short phase labels used by the symmetry source tables, currently `AM` for an altermagnetic phase and `FiM` for a fully compensated ferrimagnetic phase; the scalar `magnetic_phase` property serves the long form of the first entry.\nA null value means no magnetic phases are recorded for this material.",
    "examples": [
        [
            "AM"
        ],
        [
            "AM",
            "FiM"
        ]
    ]
}
```