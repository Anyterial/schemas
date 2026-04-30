# Asymmetric unit string (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_str`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_str.md)**  
**Definition name:** `asu_str`

**Property name:** Asymmetric unit string  
**Description:** Plain string rendering of the asymmetric-unit restrictions for the space-group setting.  
**Type:** string  



**Examples:**

- `"x>=0; x<1; y>=0; y<1; z>=0; z<1"`
- `"x>=0 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]; x<=1/2 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]; y>=0; y<1; z>=0; z<1"`

**Formats:** [[JSON](asu_str.json)] [[MD](asu_str.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_str",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Asymmetric unit string",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "asu_str",
        "label": "asu_str_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "Plain string rendering of the asymmetric-unit restrictions for the space-group setting.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "x>=0; x<1; y>=0; y<1; z>=0; z<1",
        "x>=0 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]; x<=1/2 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]; y>=0; y<1; z>=0; z<1"
    ]
}
```