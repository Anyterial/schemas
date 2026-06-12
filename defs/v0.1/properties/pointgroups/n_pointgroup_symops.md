# number of pointgroup symops (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_pointgroup_symops`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_pointgroup_symops.md)**  
**Definition name:** `n_pointgroup_symops`

**Property name:** number of pointgroup symops  
**Description:** Number of point-group symmetry operations.  
**Type:** integer  



**Examples:**

- `1`
- `2`

**Formats:** [[JSON](n_pointgroup_symops.json)] [[MD](n_pointgroup_symops.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_pointgroup_symops",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "number of pointgroup symops",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_pointgroup_symops",
        "label": "n_pointgroup_symops_pointgroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of point-group symmetry operations.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        1,
        2
    ]
}
```