# Point-group Hermann-Mauguin symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group.md)**  
**Definition name:** `point_group`

**Property name:** Point-group Hermann-Mauguin symbol  
**Description:** The Hermann-Mauguin point-group symbol for the crystallographic point group of the space group.  
**Type:** string  

This field identifies the crystallographic point group obtained from the space group by removing translational components.
The value uses the same Hermann-Mauguin symbol vocabulary as the `hm_symbol` key of the pointgroups entries, defined by `/defs/v0.1/properties/pointgroups/hm_symbol`, and can be used to look up the corresponding pointgroups entry.

**Examples:**

- `"1"`
- `"2/m"`
- `"m-3m"`

**Formats:** [[JSON](point_group.json)] [[MD](point_group.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Point-group Hermann-Mauguin symbol",
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
    "description": "The Hermann-Mauguin point-group symbol for the crystallographic point group of the space group.\n\nThis field identifies the crystallographic point group obtained from the space group by removing translational components.\nThe value uses the same Hermann-Mauguin symbol vocabulary as the `hm_symbol` key of the pointgroups entries, defined by `/defs/v0.1/properties/pointgroups/hm_symbol`, and can be used to look up the corresponding pointgroups entry.",
    "x-optimade-unit": "inapplicable",
    "enum": [
        "1",
        "-1",
        "2",
        "m",
        "2/m",
        "222",
        "mm2",
        "mmm",
        "4",
        "-4",
        "4/m",
        "422",
        "4mm",
        "-42m",
        "4/mmm",
        "3",
        "-3",
        "32",
        "3m",
        "-3m",
        "6",
        "-6",
        "6/m",
        "622",
        "6mm",
        "-62m",
        "6/mmm",
        "23",
        "m-3",
        "432",
        "-43m",
        "m-3m"
    ],
    "examples": [
        "1",
        "2/m",
        "m-3m"
    ]
}
```