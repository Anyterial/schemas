# Hermann-Mauguin Short Old (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old.md)**  
**Definition name:** `hm_short_old`

**Property name:** Hermann-Mauguin Short Old  
**Description:** The older short Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.  
**Type:** string  

Hermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.

**Requirements/Conventions**:

- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.
- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.
- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.

**Examples:**

- `"A b m 2"`
- `"C 2 m b"`

**Formats:** [[JSON](hm_short_old.json)] [[MD](hm_short_old.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Hermann-Mauguin Short Old",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hm_short_old",
        "label": "hm_short_old_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "The older short Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "A b m 2",
        "C 2 m b"
    ]
}
```