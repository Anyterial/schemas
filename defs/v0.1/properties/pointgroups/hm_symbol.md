# Hermann-Mauguin symbol (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol.md)**  
**Definition name:** `hm_symbol`

**Property name:** Hermann-Mauguin symbol  
**Description:** Hermann-Mauguin point-group symbol used as the key and display symbol for a point-group record.  
**Type:** string  

The value is one of the 32 crystallographic point-group symbols in Hermann-Mauguin notation, written in ASCII with `-` denoting rotoinversion.

**Examples:**

- `"1"`
- `"-1"`
- `"m-3m"`

**Formats:** [[JSON](hm_symbol.json)] [[MD](hm_symbol.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Hermann-Mauguin symbol",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "hm_symbol",
        "label": "hm_symbol_pointgroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "Hermann-Mauguin point-group symbol used as the key and display symbol for a point-group record.\n\nThe value is one of the 32 crystallographic point-group symbols in Hermann-Mauguin notation, written in ASCII with `-` denoting rotoinversion.",
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
        "-1",
        "m-3m"
    ]
}
```