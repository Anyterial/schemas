# Maximal subgroup type (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/subgroup_type`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/subgroup_type.md)**  
**Definition name:** `subgroup_type`

**Property name:** Maximal subgroup type  
**Description:** International Tables maximal subgroup class.  
**Type:** string  

The value is `t` for a translationengleiche subgroup and `k` for a klassengleiche subgroup.
The field is omitted when the enclosing record is not a maximal subgroup relation.

**Examples:**

- `"k"`
- `"t"`

**Formats:** [[JSON](subgroup_type.json)] [[MD](subgroup_type.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/transformations/subgroup_type",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Maximal subgroup type",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "subgroup_type",
        "label": "subgroup_type_transformations"
    },
    "type": [
        "string"
    ],
    "description": "International Tables maximal subgroup class.\n\nThe value is `t` for a translationengleiche subgroup and `k` for a klassengleiche subgroup.\nThe field is omitted when the enclosing record is not a maximal subgroup relation.",
    "enum": [
        "t",
        "k"
    ],
    "x-optimade-unit": "inapplicable",
    "examples": [
        "k",
        "t"
    ]
}
```