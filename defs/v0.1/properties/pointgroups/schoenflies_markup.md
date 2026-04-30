# Schoenflies symbol markups (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies_markup`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies_markup.md)**  
**Definition name:** `schoenflies_markup`

**Property name:** Schoenflies symbol markups  
**Description:** Display-oriented renderings of the Schoenflies symbol in `schoenflies`.
The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.  
**Type:** dictionary  



**Examples:**

- `{"html": "<i>P</i> 2<sub>1</sub>/<i>c</i>", "latex": "\\mathit{P}\\,2_{1}/c", "unicode": "P2\u2081/c"}`

**Formats:** [[JSON](schoenflies_markup.json)] [[MD](schoenflies_markup.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies_markup",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Schoenflies symbol markups",
    "$comment": "Anyterial symmetry property definition inheriting the common string markup object.",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "schoenflies_markup",
        "label": "schoenflies_markup_pointgroups"
    },
    "description": "Display-oriented renderings of the Schoenflies symbol in `schoenflies`.\nThe plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.",
    "x-optimade-type": "dictionary",
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "properties": {
        "html": {
            "x-optimade-type": "string",
            "x-optimade-unit": "inapplicable",
            "type": [
                "string",
                "null"
            ],
            "description": "HTML rendering of the sibling string."
        },
        "latex": {
            "x-optimade-type": "string",
            "x-optimade-unit": "inapplicable",
            "type": [
                "string",
                "null"
            ],
            "description": "LaTeX rendering of the sibling string."
        },
        "unicode": {
            "x-optimade-type": "string",
            "x-optimade-unit": "inapplicable",
            "type": [
                "string",
                "null"
            ],
            "description": "Unicode rendering of the sibling string."
        }
    },
    "examples": [
        {
            "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
            "latex": "\\mathit{P}\\,2_{1}/c",
            "unicode": "P2\u2081/c"
        }
    ]
}
```