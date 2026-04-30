# Full Hermann-Mauguin Symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full.md)**  
**Definition name:** `hm_full`

**Property name:** Full Hermann-Mauguin Symbol  
**Description:** The setting-specific full Hermann-Mauguin symbol for the space-group setting.  
**Type:** string  

The full symbol expands the short Hermann-Mauguin notation to include the symmetry entries for all relevant crystallographic directions in the setting represented by the containing Hall record.

**Examples:**

- `"P 1"`
- `"C 1 2 1"`

**Formats:** [[JSON](hm_full.json)] [[MD](hm_full.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Full Hermann-Mauguin Symbol",
    "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.name_H-M_full.html"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hm_full",
        "label": "hm_full_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The setting-specific full Hermann-Mauguin symbol for the space-group setting.\n\nThe full symbol expands the short Hermann-Mauguin notation to include the symmetry entries for all relevant crystallographic directions in the setting represented by the containing Hall record.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "P 1",
        "C 1 2 1"
    ]
}
```