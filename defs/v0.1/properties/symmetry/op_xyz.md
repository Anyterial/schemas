# Operation xyz (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op_xyz.md)**  
**Definition name:** `op_xyz`

**Property name:** Operation xyz  
**Description:** Coordinate operation expressed in the algebraic xyz form, also known as Jones' faithful representation (Bradley & Cracknell, 1972: pp. 35-37; adapted for computer strings).  
**Type:** string  

The following definition is adapted from (and meant to be compatible with) the IUCr symCIF version 1.0.1 dictionary definition of `_space_group_symop.operation_xyz` referenced to: International Tables for Crystallography (2002). Volume A, Space-group symmetry, edited by Th. Hahn, 5th. ed. (Kluwer Academic Publishers).
It is available at: https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group_symop.operation_xyz.html

If W is a matrix representation of the rotational part of the symmetry operation defined by the positions and signs of x, y and z, and w is a column of translations defined by the fractions, an equivalent position X' is generated from a given position X by the equation: X' = WX + w.

**Examples:**

- `"-x,-y,z"`
- `"x,1/2-y,1/2+z"`

**Formats:** [[JSON](op_xyz.json)] [[MD](op_xyz.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op_xyz",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Operation xyz",
    "x-optimade-type": "string",
    "x-compatibility": [
        "https://schemas.optimade.org/defs/v1.2/properties/optimade/common/symmetry_operation_xyz",
        "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group_symop.operation_xyz.html"
    ],
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "op_xyz",
        "label": "op_xyz_symmetry"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "string",
        "null"
    ],
    "description": "Coordinate operation expressed in the algebraic xyz form, also known as Jones' faithful representation (Bradley & Cracknell, 1972: pp. 35-37; adapted for computer strings).\n\nThe following definition is adapted from (and meant to be compatible with) the IUCr symCIF version 1.0.1 dictionary definition of `_space_group_symop.operation_xyz` referenced to: International Tables for Crystallography (2002). Volume A, Space-group symmetry, edited by Th. Hahn, 5th. ed. (Kluwer Academic Publishers).\nIt is available at: https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group_symop.operation_xyz.html\n\nIf W is a matrix representation of the rotational part of the symmetry operation defined by the positions and signs of x, y and z, and w is a column of translations defined by the fractions, an equivalent position X' is generated from a given position X by the equation: X' = WX + w.",
    "x-undef-pattern": "^([-+]?[xyz]([-+][xyz])?([-+](1/2|[12]/3|[1-3]/4|[1-5]/6))?|[-+]?(1/2|[12]/3|[1-3]/4|[1-5]/6)([-+][xyz]([-+][xyz])?)?),([-+]?[xyz]([-+][xyz])?([-+](1/2|[12]/3|[1-3]/4|[1-5]/6))?|[-+]?(1/2|[12]/3|[1-3]/4|[1-5]/6)([-+][xyz]([-+][xyz])?)?),([-+]?[xyz]([-+][xyz])?([-+](1/2|[12]/3|[1-3]/4|[1-5]/6))?|[-+]?(1/2|[12]/3|[1-3]/4|[1-5]/6)([-+][xyz]([-+][xyz])?)?)$",
    "examples": [
        "-x,-y,z",
        "x,1/2-y,1/2+z"
    ]
}
```