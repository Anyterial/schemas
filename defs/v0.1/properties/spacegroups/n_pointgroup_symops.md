# N Pointgroup Symops (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_pointgroup_symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_pointgroup_symops.md)**  
**Definition name:** `n_pointgroup_symops`

**Property name:** N Pointgroup Symops  
**Description:** Number of point-group symmetry operations represented by the space group, excluding centering translations.  
**Type:** integer  



**Examples:**

- `1`
- `2`

**Formats:** [[JSON](n_pointgroup_symops.json)] [[MD](n_pointgroup_symops.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_pointgroup_symops",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "N Pointgroup Symops",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "n_pointgroup_symops",
        "label": "n_pointgroup_symops_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Number of point-group symmetry operations represented by the space group, excluding centering translations.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        1,
        2
    ]
}
```