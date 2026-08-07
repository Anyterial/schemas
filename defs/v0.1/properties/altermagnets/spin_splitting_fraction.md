# Spin splitting fraction (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/spin_splitting_fraction`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/spin_splitting_fraction.md)**  
**Definition name:** `spin_splitting_fraction`

**Property name:** Spin splitting fraction  
**Description:** A dimensionless relative spin-splitting measure in the range 0 to 1.  
**Type:** float  

A null value means the quantity is not available for this material.

**Examples:**



**Formats:** [[JSON](spin_splitting_fraction.json)] [[MD](spin_splitting_fraction.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/spin_splitting_fraction",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Spin splitting fraction",
    "x-optimade-type": "float",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "spin_splitting_fraction",
        "label": "spin_splitting_fraction_altermagnets"
    },
    "x-optimade-unit": "dimensionless",
    "type": [
        "number",
        "null"
    ],
    "description": "A dimensionless relative spin-splitting measure in the range 0 to 1.\n\nA null value means the quantity is not available for this material."
}
```