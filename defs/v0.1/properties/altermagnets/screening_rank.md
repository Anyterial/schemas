# Screening rank (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/screening_rank`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/screening_rank.md)**  
**Definition name:** `screening_rank`

**Property name:** Screening rank  
**Description:** The material's ordinal position in the published high-throughput screening table, starting at 1.  
**Type:** integer  

The rank reflects the curated ordering of the source dataset.
A null value means the material has no recorded screening position.

**Examples:**



**Formats:** [[JSON](screening_rank.json)] [[MD](screening_rank.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/screening_rank",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Screening rank",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "screening_rank",
        "label": "screening_rank_altermagnets"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "integer",
        "null"
    ],
    "description": "The material's ordinal position in the published high-throughput screening table, starting at 1.\n\nThe rank reflects the curated ordering of the source dataset.\nA null value means the material has no recorded screening position."
}
```