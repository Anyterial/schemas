# Laue Class (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class.md)**  
**Definition name:** `laue_class`

**Property name:** Laue Class  
**Description:** The Laue class associated with the space group or point group.  
**Type:** string  

The Laue class groups point groups that become equivalent when inversion symmetry is included.

**Examples:**

- `"-1"`
- `"2/m"`

**Formats:** [[JSON](laue_class.json)] [[MD](laue_class.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Laue Class",
    "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.Laue_class.html"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "laue_class",
        "label": "laue_class_pointgroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The Laue class associated with the space group or point group.\n\nThe Laue class groups point groups that become equivalent when inversion symmetry is included.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "-1",
        "2/m"
    ]
}
```