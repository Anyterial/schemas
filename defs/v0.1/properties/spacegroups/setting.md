# Setting (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting.md)**  
**Definition name:** `setting`

**Property name:** Setting  
**Description:** Setting suffix or setting annotation extracted from the cctbx universal Hermann-Mauguin symbol.  
**Type:** string  

This value is a compact textual description of the coordinate setting portion of the cctbx symbol, for example an origin choice or axis-setting annotation. It is primarily an auxiliary generator field and SHOULD NOT be used as a substitute for the International Tables `setting_it_nc` identifier.

**Examples:**

- `"(c,a,b)"`
- `"(b,c,a)"`

**Formats:** [[JSON](setting.json)] [[MD](setting.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Setting",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "setting",
        "label": "setting_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "Setting suffix or setting annotation extracted from the cctbx universal Hermann-Mauguin symbol.\n\nThis value is a compact textual description of the coordinate setting portion of the cctbx symbol, for example an origin choice or axis-setting annotation. It is primarily an auxiliary generator field and SHOULD NOT be used as a substitute for the International Tables `setting_it_nc` identifier.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "(c,a,b)",
        "(b,c,a)"
    ]
}
```