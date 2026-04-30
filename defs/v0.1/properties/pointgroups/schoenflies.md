# Schoenflies Symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies.md)**  
**Definition name:** `schoenflies`

**Property name:** Schoenflies Symbol  
**Description:** The Schoenflies symbol for the space-group type.  
**Type:** string  

The ASCII form follows the CIF convention for `_space_group.name_Schoenflies`, using a period to separate the Schoenflies point-group symbol from the superscript index.

**Examples:**

- `"C1.1"`
- `"C2.3"`

**Formats:** [[JSON](schoenflies.json)] [[MD](schoenflies.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Schoenflies Symbol",
    "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.name_Schoenflies.html"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "schoenflies",
        "label": "schoenflies_pointgroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The Schoenflies symbol for the space-group type.\n\nThe ASCII form follows the CIF convention for `_space_group.name_Schoenflies`, using a period to separate the Schoenflies point-group symbol from the superscript index.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "C1.1",
        "C2.3"
    ]
}
```