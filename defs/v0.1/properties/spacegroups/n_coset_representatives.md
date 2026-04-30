# N Coset Representatives (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_coset_representatives`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_coset_representatives.md)**  
**Definition name:** `n_coset_representatives`

**Property name:** N Coset Representatives  
**Description:** Number of nontrivial coset representatives retained after deduplication modulo the space group.  
**Type:** integer  



**Examples:**

- `47`
- `23`

**Formats:** [[JSON](n_coset_representatives.json)] [[MD](n_coset_representatives.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_coset_representatives",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "N Coset Representatives",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_coset_representatives",
        "label": "n_coset_representatives_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of nontrivial coset representatives retained after deduplication modulo the space group.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        47,
        23
    ]
}
```