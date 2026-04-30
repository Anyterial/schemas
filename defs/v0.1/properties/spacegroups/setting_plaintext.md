# Setting Plaintext (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_plaintext`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_plaintext.md)**  
**Definition name:** `setting_plaintext`

**Property name:** Setting Plaintext  
**Description:** Human-readable description of the International Tables coordinate-system setting.  
**Type:** string  

This field expands `setting_it_nc` into a short phrase such as a monoclinic unique-axis and cell-choice description, an orthorhombic axis permutation, or an origin-choice description.

**Examples:**

- `"unique axis b"`
- `"unique axis c"`

**Formats:** [[JSON](setting_plaintext.json)] [[MD](setting_plaintext.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_plaintext",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Setting Plaintext",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "setting_plaintext",
        "label": "setting_plaintext_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "Human-readable description of the International Tables coordinate-system setting.\n\nThis field expands `setting_it_nc` into a short phrase such as a monoclinic unique-axis and cell-choice description, an orthorhombic axis permutation, or an origin-choice description.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "unique axis b",
        "unique axis c"
    ]
}
```