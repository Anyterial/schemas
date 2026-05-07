# Symmetry operations modulo centering in x,y,z notation (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_mod_centering_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_mod_centering_xyz.md)**  
**Definition name:** `symops_mod_centering_xyz`

**Property name:** Symmetry operations modulo centering in x,y,z notation  
**Description:** Symmetry operations modulo centering translations in fractional `x,y,z` notation, ordered consistently with `symops_mod_centering`.  
**Type:** list  



**Examples:**

- `["x,y,z"]`
- `["-x,y,-z", "x,y,z"]`

**Formats:** [[JSON](symops_mod_centering_xyz.json)] [[MD](symops_mod_centering_xyz.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_mod_centering_xyz",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Symmetry operations modulo centering in x,y,z notation",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "symops_mod_centering_xyz",
        "label": "symops_mod_centering_xyz_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "Symmetry operations modulo centering translations in fractional `x,y,z` notation, ordered consistently with `symops_mod_centering`.",
    "x-optimade-unit": "inapplicable",
    "items": {
        "x-optimade-type": "string",
        "x-optimade-unit": "inapplicable",
        "type": [
            "string"
        ]
    },
    "examples": [
        [
            "x,y,z"
        ],
        [
            "-x,y,-z",
            "x,y,z"
        ]
    ]
}
```