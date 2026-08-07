# Electronic type (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/electronic_type`](https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/electronic_type.md)**  
**Definition name:** `electronic_type`

**Property name:** Electronic type  
**Description:** A qualitative classification of the electronic structure of the material.  
**Type:** string  

The value is derived from the Kohn-Sham band gap: `metallic` when the band gap is zero, `semiconducting` when it is positive, and `unknown` when the band gap is not available.
A null value means the classification is not available for this material.

**Examples:**

- `"metallic"`
- `"semiconducting"`

**Formats:** [[JSON](electronic_type.json)] [[MD](electronic_type.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/altermagnets/electronic_type",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Electronic type",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "electronic_type",
        "label": "electronic_type_altermagnets"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "string",
        "null"
    ],
    "description": "A qualitative classification of the electronic structure of the material.\n\nThe value is derived from the Kohn-Sham band gap: `metallic` when the band gap is zero, `semiconducting` when it is positive, and `unknown` when the band gap is not available.\nA null value means the classification is not available for this material.",
    "enum": [
        "metallic",
        "semiconducting",
        "unknown"
    ],
    "examples": [
        "metallic",
        "semiconducting"
    ]
}
```