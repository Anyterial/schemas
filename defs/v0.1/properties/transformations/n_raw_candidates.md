# Number of raw candidates (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_raw_candidates`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_raw_candidates.md)**  
**Definition name:** `n_raw_candidates`

**Property name:** Number of raw candidates  
**Description:** Number of candidate affine operations considered before filtering and deduplication.  
**Type:** integer  

The counted candidate set itself is not stored; this value documents the size of the bounded search.

**Examples:**

- `48`
- `6960`

**Formats:** [[JSON](n_raw_candidates.json)] [[MD](n_raw_candidates.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_raw_candidates",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Number of raw candidates",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_raw_candidates",
        "label": "n_raw_candidates_transformations"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of candidate affine operations considered before filtering and deduplication.\n\nThe counted candidate set itself is not stored; this value documents the size of the bounded search.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        48,
        6960
    ]
}
```