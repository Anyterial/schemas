# International Tables Coordinate-System Code (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_coordinate_system_code`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_coordinate_system_code.md)**  
**Definition name:** `it_coordinate_system_code`

**Property name:** International Tables Coordinate-System Code  
**Description:** The International Tables coordinate-system code for the setting.  
**Type:** string  

The code distinguishes setting choices such as monoclinic unique-axis and cell choices, orthorhombic axis settings, tetragonal/cubic origin choices, and trigonal hexagonal or rhombohedral axes.

**Examples:**

- `"b1"`
- `"2"`

**Formats:** [[JSON](it_coordinate_system_code.json)] [[MD](it_coordinate_system_code.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_coordinate_system_code",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "International Tables Coordinate-System Code",
    "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.IT_coordinate_system_code.html"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "it_coordinate_system_code",
        "label": "it_coordinate_system_code_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The International Tables coordinate-system code for the setting.\n\nThe code distinguishes setting choices such as monoclinic unique-axis and cell choices, orthorhombic axis settings, tetragonal/cubic origin choices, and trigonal hexagonal or rhombohedral axes.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "b1",
        "2"
    ]
}
```