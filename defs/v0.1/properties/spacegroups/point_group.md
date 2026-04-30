# Point-Group Hermann-Mauguin Symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group.md)**  
**Definition name:** `point_group`

**Property name:** Point-Group Hermann-Mauguin Symbol  
**Description:** The Hermann-Mauguin point-group symbol associated with the space group.  
**Type:** string  

This field identifies the crystallographic point group obtained from the space group by removing translational components.

**Examples:**

- `"1"`
- `"2"`

**Formats:** [[JSON](point_group.json)] [[MD](point_group.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Point-Group Hermann-Mauguin Symbol",
    "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.point_group_H-M.html"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "point_group",
        "label": "point_group_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The Hermann-Mauguin point-group symbol associated with the space group.\n\nThis field identifies the crystallographic point group obtained from the space group by removing translational components.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "1",
        "2"
    ]
}
```