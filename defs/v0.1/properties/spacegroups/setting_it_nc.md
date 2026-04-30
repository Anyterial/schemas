# International Tables setting code n:c (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc.md)**  
**Definition name:** `setting_it_nc`

**Property name:** International Tables setting code n:c  
**Description:** International Tables setting identifier in `n:c` notation.  
**Type:** string  

The part before the colon is the International Tables space-group number. The part after the colon is the coordinate-system or origin-choice qualifier used to distinguish settings that share the same IT number.

**Requirements/Conventions**:

- Triclinic, hexagonal, and many unique settings use only the IT number, for example `1`.
- Monoclinic settings use qualifiers such as `b1`, `-b1`, `c2`, or `a3`.
- Orthorhombic settings use qualifiers such as `abc`, `cab`, `1abc`, or `2bca` when needed.
- Tetragonal and cubic origin choices use qualifiers such as `1` and `2`; trigonal axis choices use qualifiers such as `h` and `r`.

**Examples:**

- `"1"`
- `"2"`

**Formats:** [[JSON](setting_it_nc.json)] [[MD](setting_it_nc.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "International Tables setting code n:c",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "setting_it_nc",
        "label": "setting_it_nc_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "International Tables setting identifier in `n:c` notation.\n\nThe part before the colon is the International Tables space-group number. The part after the colon is the coordinate-system or origin-choice qualifier used to distinguish settings that share the same IT number.\n\n**Requirements/Conventions**:\n\n- Triclinic, hexagonal, and many unique settings use only the IT number, for example `1`.\n- Monoclinic settings use qualifiers such as `b1`, `-b1`, `c2`, or `a3`.\n- Orthorhombic settings use qualifiers such as `abc`, `cab`, `1abc`, or `2bca` when needed.\n- Tetragonal and cubic origin choices use qualifiers such as `1` and `2`; trigonal axis choices use qualifiers such as `h` and `r`.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "1",
        "2"
    ]
}
```