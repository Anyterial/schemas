# fraction (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/core/fraction`](https://schemas.anyterial.se/defs/v0.1/properties/core/fraction.md)**  
**Definition name:** `fraction`

**Property name:** fraction  
**Description:** A fraction represented as a string.  
**Type:** string  



**Examples:**

- `"2/3"`
- `"5/42"`
- `"10"`
- `"0"`

**Formats:** [[JSON](fraction.json)] [[MD](fraction.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
    "$schema": "https://schemas.optimade.org/meta/v1.2/optimade/property_definition.json",
    "title": "fraction",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "label": "fraction_core",
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "fraction"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "A fraction represented as a string.",
    "examples": [
        "2/3",
        "5/42",
        "10",
        "0"
    ],
    "x-optimade-unit": "inapplicable"
}
```