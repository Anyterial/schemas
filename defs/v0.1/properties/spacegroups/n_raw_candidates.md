# N Raw Candidates (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_raw_candidates`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_raw_candidates.md)**  
**Definition name:** `n_raw_candidates`

**Property name:** N Raw Candidates  
**Description:** Number of candidate affine operations considered before filtering and deduplication.  
**Type:** integer  



**Examples:**

- `48`
- `6960`

**Formats:** [[JSON](n_raw_candidates.json)] [[MD](n_raw_candidates.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_raw_candidates",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "N Raw Candidates",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_raw_candidates",
        "label": "n_raw_candidates_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of candidate affine operations considered before filtering and deduplication.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        48,
        6960
    ]
}
```