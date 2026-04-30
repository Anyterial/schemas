# N Symops (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops.md)**  
**Definition name:** `n_symops`

**Property name:** N Symops  
**Description:** Number of symmetry operations in the finite operation list of the generated entry.  
**Type:** integer  



**Examples:**

- `1`
- `2`

**Formats:** [[JSON](n_symops.json)] [[MD](n_symops.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "N Symops",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_symops",
        "label": "n_symops_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of symmetry operations in the finite operation list of the generated entry.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        1,
        2
    ]
}
```