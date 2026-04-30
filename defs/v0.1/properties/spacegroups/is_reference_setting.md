# Is Reference Setting (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_reference_setting`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_reference_setting.md)**  
**Definition name:** `is_reference_setting`

**Property name:** Is Reference Setting  
**Description:** Boolean flag indicating whether this Hall setting is the selected reference setting for its International Tables space-group number.  
**Type:** boolean  



**Examples:**

- `true`
- `false`

**Formats:** [[JSON](is_reference_setting.json)] [[MD](is_reference_setting.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_reference_setting",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Is Reference Setting",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "boolean",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "is_reference_setting",
        "label": "is_reference_setting_spacegroups"
    },
    "type": [
        "boolean",
        "null"
    ],
    "description": "Boolean flag indicating whether this Hall setting is the selected reference setting for its International Tables space-group number.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        true,
        false
    ]
}
```