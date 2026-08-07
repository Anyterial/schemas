# Magnetic phase (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/magnetic_phase`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/magnetic_phase.md)**  
**Definition name:** `magnetic_phase`

**Property name:** Magnetic phase  
**Description:** The magnetic phase assigned to the material by collinear/noncollinear symmetry analysis.  
**Type:** string  

The vocabulary distinguishes `altermagnet`, denoting an altermagnetic phase, and `compensated ferrimagnet`, denoting a fully compensated ferrimagnetic phase.
A null value means no magnetic phase is available or recorded for this material.

**Examples:**

- `"altermagnet"`
- `"compensated ferrimagnet"`

**Formats:** [[JSON](magnetic_phase.json)] [[MD](magnetic_phase.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/magnetic_phase",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Magnetic phase",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "magnetic_phase",
        "label": "magnetic_phase_altermagnets"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "string",
        "null"
    ],
    "description": "The magnetic phase assigned to the material by collinear/noncollinear symmetry analysis.\n\nThe vocabulary distinguishes `altermagnet`, denoting an altermagnetic phase, and `compensated ferrimagnet`, denoting a fully compensated ferrimagnetic phase.\nA null value means no magnetic phase is available or recorded for this material.",
    "enum": [
        "altermagnet",
        "compensated ferrimagnet"
    ],
    "examples": [
        "altermagnet",
        "compensated ferrimagnet"
    ]
}
```