# Number of symops (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops.md)**  
**Definition name:** `n_symops`

**Property name:** Number of symops  
**Description:** Number of symmetry operations in the finite operation list of the generated entry.  
**Type:** integer  

When the entry contains a `symops` list, this value MUST equal its length.

**Examples:**

- `1`
- `2`

**Formats:** [[JSON](n_symops.json)] [[MD](n_symops.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Number of symops",
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
    "description": "Number of symmetry operations in the finite operation list of the generated entry.\n\nWhen the entry contains a `symops` list, this value MUST equal its length.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        1,
        2
    ]
}
```