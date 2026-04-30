# Symmetry operations in x,y,z notation (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_xyz.md)**  
**Definition name:** `symops_xyz`

**Property name:** Symmetry operations in x,y,z notation  
**Description:** Full list of symmetry operations for the space-group setting written in fractional `x,y,z` coordinate notation. Each expression acts on fractional coordinates in the setting represented by the containing Hall entry.  
**Type:** list  



**Examples:**

- `["x,y,z"]`
- `["-x,-y,-z", "x,y,z"]`

**Formats:** [[JSON](symops_xyz.json)] [[MD](symops_xyz.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_xyz",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Symmetry operations in x,y,z notation",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "symops_xyz",
        "label": "symops_xyz_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "Full list of symmetry operations for the space-group setting written in fractional `x,y,z` coordinate notation. Each expression acts on fractional coordinates in the setting represented by the containing Hall entry.",
    "x-optimade-unit": "inapplicable",
    "items": {
        "x-optimade-type": "string",
        "x-optimade-unit": "inapplicable",
        "type": [
            "string"
        ],
        "description": "One symmetry operation in x,y,z notation."
    },
    "examples": [
        [
            "x,y,z"
        ],
        [
            "-x,-y,-z",
            "x,y,z"
        ]
    ],
    "x-compatibility": [
        "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symmetry_operations_xyz"
    ]
}
```