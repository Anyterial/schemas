# Symops Generators Xyz (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators_xyz.md)**  
**Definition name:** `symops_generators_xyz`

**Property name:** Symops Generators Xyz  
**Description:** Minimal generator subset of the full symmetry-operation group in fractional `x,y,z` notation, ordered consistently with `symops_generators`.  
**Type:** list  



**Examples:**

- `["-x,-y,-z"]`
- `["-x,y,-z"]`

**Formats:** [[JSON](symops_generators_xyz.json)] [[MD](symops_generators_xyz.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators_xyz",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Symops Generators Xyz",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "symops_generators_xyz",
        "label": "symops_generators_xyz_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "Minimal generator subset of the full symmetry-operation group in fractional `x,y,z` notation, ordered consistently with `symops_generators`.",
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
            "-x,-y,-z"
        ],
        [
            "-x,y,-z"
        ]
    ]
}
```