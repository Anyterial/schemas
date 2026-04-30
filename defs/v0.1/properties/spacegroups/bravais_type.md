# Bravais Type (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/bravais_type`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/bravais_type.md)**  
**Definition name:** `bravais_type`

**Property name:** Bravais Type  
**Description:** The Bravais type of the translational lattice.  
**Type:** string  

The symbol consists of a lower-case crystal-system letter followed by an upper-case centring symbol, using setting-independent `mS` and `oS` for monoclinic and orthorhombic side-centred lattices.

**Examples:**

- `"aP"`
- `"mS"`

**Formats:** [[JSON](bravais_type.json)] [[MD](bravais_type.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/bravais_type",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Bravais Type",
    "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.Bravais_type.html"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "bravais_type",
        "label": "bravais_type_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The Bravais type of the translational lattice.\n\nThe symbol consists of a lower-case crystal-system letter followed by an upper-case centring symbol, using setting-independent `mS` and `oS` for monoclinic and orthorhombic side-centred lattices.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "aP",
        "mS"
    ]
}
```