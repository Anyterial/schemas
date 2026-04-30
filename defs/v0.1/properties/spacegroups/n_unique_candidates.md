# N Unique Candidates (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_unique_candidates`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_unique_candidates.md)**  
**Definition name:** `n_unique_candidates`

**Property name:** N Unique Candidates  
**Description:** Number of candidate affine operations remaining after exact duplicate removal.  
**Type:** integer  



**Examples:**

- `48`
- `16`

**Formats:** [[JSON](n_unique_candidates.json)] [[MD](n_unique_candidates.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_unique_candidates",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "N Unique Candidates",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_unique_candidates",
        "label": "n_unique_candidates_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of candidate affine operations remaining after exact duplicate removal.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        48,
        16
    ]
}
```