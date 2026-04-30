# Maximal subgroup type (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/subgroup_type`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/subgroup_type.md)**  
**Definition name:** `subgroup_type`

**Property name:** Maximal subgroup type  
**Description:** International Tables maximal subgroup class: `t` for translationengleiche or `k` for klassengleiche.  
**Type:** string  



**Examples:**

- `"k"`
- `"t"`

**Formats:** [[JSON](subgroup_type.json)] [[MD](subgroup_type.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/subgroup_type",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Maximal subgroup type",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "subgroup_type",
        "label": "subgroup_type_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "International Tables maximal subgroup class: `t` for translationengleiche or `k` for klassengleiche.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "k",
        "t"
    ]
}
```