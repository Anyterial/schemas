# Crystal system (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system.md)**  
**Definition name:** `crystal_system`

**Property name:** Crystal system  
**Description:** The crystal system of the space group or point group.  
**Type:** string  

Values use the conventional crystallographic system names.

**Examples:**

- `"triclinic"`
- `"monoclinic"`

**Formats:** [[JSON](crystal_system.json)] [[MD](crystal_system.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Crystal system",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.crystal_system.html"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "crystal_system",
        "label": "crystal_system_pointgroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The crystal system of the space group or point group.\n\nValues use the conventional crystallographic system names.",
    "x-optimade-unit": "inapplicable",
    "enum": [
        "triclinic",
        "monoclinic",
        "orthorhombic",
        "tetragonal",
        "trigonal",
        "hexagonal",
        "cubic"
    ],
    "examples": [
        "triclinic",
        "monoclinic"
    ]
}
```