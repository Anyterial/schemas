# Centring Type (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centring_type`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centring_type.md)**  
**Definition name:** `centring_type`

**Property name:** Centring Type  
**Description:** The lattice centring symbol for the crystallographic setting.  
**Type:** string  

This setting-dependent symbol identifies primitive, face-centred, body-centred, rhombohedral, or hexagonal centring as represented in the setting record.

**Examples:**

- `"P"`
- `"C"`

**Formats:** [[JSON](centring_type.json)] [[MD](centring_type.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centring_type",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Centring Type",
    "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.centring_type.html"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "centring_type",
        "label": "centring_type_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The lattice centring symbol for the crystallographic setting.\n\nThis setting-dependent symbol identifies primitive, face-centred, body-centred, rhombohedral, or hexagonal centring as represented in the setting record.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "P",
        "C"
    ]
}
```