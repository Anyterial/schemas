# Number of pointgroup symops (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_pointgroup_symops`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_pointgroup_symops.md)**  
**Definition name:** `n_pointgroup_symops`

**Property name:** Number of pointgroup symops  
**Description:** Number of point-group symmetry operations.  
**Type:** integer  

For a space-group entry this is the number of operations of the point group of the space group, and it MUST equal the length of the `symops_representative` list when present.

**Examples:**

- `1`
- `2`

**Formats:** [[JSON](n_pointgroup_symops.json)] [[MD](n_pointgroup_symops.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_pointgroup_symops",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Number of pointgroup symops",
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
    "description": "Number of point-group symmetry operations.\n\nFor a space-group entry this is the number of operations of the point group of the space group, and it MUST equal the length of the `symops_representative` list when present.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        1,
        2
    ]
}
```