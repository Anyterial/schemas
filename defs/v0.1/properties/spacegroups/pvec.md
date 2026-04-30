# Basis transformation origin shift (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pvec`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pvec.md)**  
**Definition name:** `pvec`

**Property name:** Basis transformation origin shift  
**Description:** Translation or origin-shift vector of a crystallographic basis or setting transformation.
This emitted space-group property uses the common `/properties/symmetry/pvec` definition for its nested value shape and dimensional metadata.  
**Type:** list  



**Examples:**

- `["0", "0", "0"]`
- `["1/4", "1/4", "0"]`

**Formats:** [[JSON](pvec.json)] [[MD](pvec.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pvec",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Basis transformation origin shift",
    "$comment": "Anyterial space-group property definition inheriting the common semantic `pvec` definition.",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "pvec",
        "label": "pvec_spacegroups"
    },
    "description": "Translation or origin-shift vector of a crystallographic basis or setting transformation.\nThis emitted space-group property uses the common `/properties/symmetry/pvec` definition for its nested value shape and dimensional metadata.",
    "x-optimade-type": "list",
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "x-optimade-dimensions": {
        "names": [
            "dim_lattice"
        ],
        "sizes": [
            3
        ]
    },
    "items": {
        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
        "title": "fraction",
        "x-optimade-type": "string",
        "x-optimade-definition": {
            "label": "fraction_core",
            "kind": "property",
            "version": "0.1.0",
            "format": "1.3",
            "name": "fraction"
        },
        "type": [
            "string",
            "null"
        ],
        "description": "A fraction represented as a string.",
        "examples": [
            "2/3",
            "5/42",
            "10",
            "0"
        ],
        "x-optimade-unit": "inapplicable"
    },
    "examples": [
        [
            "0",
            "0",
            "0"
        ],
        [
            "1/4",
            "1/4",
            "0"
        ]
    ]
}
```