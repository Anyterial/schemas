# Index (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index.md)**  
**Definition name:** `index`

**Property name:** Index  
**Description:** Subgroup or transform index. For subgroup transforms it is the crystallographic subgroup index `[G:H]`, equal to the determinant factor of the basis transformation when applicable.  
**Type:** integer  



**Examples:**

- `2`
- `4`

**Formats:** [[JSON](index.json)] [[MD](index.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Index",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "index",
        "label": "index_spacegroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Subgroup or transform index. For subgroup transforms it is the crystallographic subgroup index `[G:H]`, equal to the determinant factor of the basis transformation when applicable.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        2,
        4
    ]
}
```